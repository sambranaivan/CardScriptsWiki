Welcome to the Project Ignis card scripts wiki! Hopefully one day there will be detailed documentation here.

# Scripting Library
- TODO

## Parameter naming convention
The functions passed to Effect.SetCondition, Effect.SetCost, Effect.SetTarget and Effect.SetOperation usually receive the following paramaters:
- `e`: effect
- `tp`: triggering player
- `eg`: event group
- `ep`: event player
- `ev`: event value
- `re`: reason effect
- `r`: reason
- `rp`: reason player
Additionally, costs (passed via Effect.SetCost) receive `chk` and targets (via Effect.SetTarget) receive `chk` and `chkc`:
- chk: check (as in, "activation check"). The core runs the function with chk being 0 when it performs the activation check and with chk being 1 when the effect is activated.
- chkc: needed in effects that target for effects that can redirect the targeting to another card (e.g. `Cairngorgon, Antiluminescent Knight`).

<html>
<body>
<!--StartFragment--><google-sheets-html-origin><style type="text/css"><!--td {border: 1px solid #ccc;}br {mso-data-placement:same-cell;}--></style>

sig | name | desc
-- | -- | --
void | initial_effect(Card c) | The function that will be called for each card's initialization.
int | bit.band(int a, int b) | Does a bitwise AND operation between 2 integers. (Deprecated, advised to use (int a)&(int b) instead.)
int | bit.lshift(int a, int b) | Shifts all bits of an integer to the left by an amount (Deprecated, advised to use (int a)<<(int b) instead.)
int | bit.bor(int a, int b) | Does a bitwise OR operation between 2 integers. (Deprecated, advised to use (int a)\|(int b) instead.)
int | bit.rshift(int a, int b) | Shift all bits of an integer to the right by an amount (Deprecated, advised to use (int a)>>(int b) instead.)
int | bit.bxor(int a, int b) | Does a bitwise XOR operation between 2 integers. (Deprecated, advised to use (int a)~(int b) instead.)
int | bit.bnot(int a) | Swaps the bits of an integer, 0 to 1 and 1 to 0. (Deprecated, advised to use ~(int a) instead.)
int | bit.replace(int a, int b, int c[, int width=1]) | Returns a copy of (int a) with the field with a width changed to value (int b)
int | bit.extract(int a, int b[, int width=1]) | Returns the field of (int a) with a width
int | Card.GetLuaRef(Card c) | Returns an integer representing the internal value used by lua to access the Card c.
Card | Card.FromLuaRef(int ref) | Returns a Card object from a given lua reference. The function errors out if the reference is invalid or does not refer to a Card object.
bool | Card.IsDeleted(Card c) | Returns if the Card object got internally deleted and remained as dangling reference inside the lua state.
int | Group.GetLuaRef(Group g) | Returns an integer representing the internal value used by lua to access the Group g.
Group | Group.FromLuaRef(int ref) | Returns a Group object from a given lua reference. The function errors out if the reference is invalid or does not refer to a Group object.
bool | Group.IsDeleted(Group g) | Returns if the Group object got internally deleted and remained as dangling reference inside the lua state.
int | Effect.GetLuaRef(Effect e) | Returns an integer representing the internal value used by lua to access the Effect e.
Effect | Effect.FromLuaRef(int ref) | Returns a Effect object from a given lua reference. The function errors out if the reference is invalid or does not refer to a Effect object.
bool | Effect.IsDeleted(Effect e) | Returns if the Effect object got internally deleted and remained as dangling reference inside the lua state.
table, int | GetID() | Returns two values, a card object and its ID, used before the initial effect.
int[,int] | Card.GetCode(Card c) | Returns the current code (ID/name) of the card "c".
int | Card.GetOriginalCode(Card c) | Returns the original printed code (ID/name) of the card "c".
int, int | Card.GetOriginalCodeRule(Card c) | Returns the original code (ID/name) of the card "c" while taking into account name clauses/alias (used for the "original name" wording).
int, int ... | Card.GetFusionCode(Card c) | Returns the code/ID that "c" has as a Fusion Material (see "Fusion Tag").
int, int ... | Card.GetLinkCode(Card c) | Returns the code/ID that "c" has as a Link Material (see "Formud Skipper").
bool | Card.IsSummonCode(Card c, Card sc\|nil, int sumtype, int playerid, int ...) | Checks if "c" has a specific code from the "..." list if it is to be used as material for the Summon type "sumtype" of "sc" performed by the player "playerid".
bool | Card.IsFusionCode(Card c, int ...) | Checks if "c" has a specific code from the "..." list as a Fusion Material.
bool | Card.IsLinkCode(Card c, int ...) | Checks if "c" has a specific code from the "..." list as a Link Material.
bool | Card.IsSetCard(Card c, int setname[, Card scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Checks if "c" is part of the archetype "setname" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
bool | Card.IsOriginalSetCard(Card c, int setname) | Checks if "c" is originally part of the archetype "setname".
bool | Card.IsPreviousSetCard(Card c, int setname) | Checks if "c" was previously part of the archetype "setname".
bool | Card.IsFusionSetCard(Card c, int setname) | Checks if "c" is part of the archetype "setname" if it is to be used as a Fusion Material.
int ... | Card.GetSetCard(Card c[, Card\|nil scard, int sumtype=0, int playerid=PLAYER_NONE]) | Returns the archetype(s) that "c" has (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
int ... | Card.GetOriginalSetCard(Card c) | Returns the original archetype(s) that "c" is a part of.
int ... | Card.GetPreviousSetCard(Card c) | Returns the archetype(s) that "c" was part of previously.
int ... | Card.GetFusionSetCard(Card c) | Returns the archetype(s) that "c" is a part of if it is to be used as a Fusion Material.
bool | Card.IsLinkSummonable(Card c[, Group\|Card\|nil must_use, Group\|Card\|nil  mg, int min=0, int max=0]) | Checks if "c" can be Link Summoned using "must_use" as part of its materials, choosing among "mg", with "min" and "max" materials to be used for the Link Summon.
bool | Card.IsLinkSetCard(Card c, int setname) | Checks if "c" is part of the archetype "setname" as a Link Material.
int | Card.GetType(Card c[, Card\|nil scard, int sumtype = 0, int playerid = PLAYER_NONE]) | Gets the current type of a Card (Card c) where (Card scard) if provided checks the monster that (Card c) would be used as material, (int sumtype) is for checking the summon type and (int playerid) is the player checking the type.
int | Card.GetOriginalType(Card c) | Returns the original card type (Monster/Spell/Trap) of "c".
int | Card.GetLevel(Card c) | Returns the current Level of "c". (Returns 0 if it has no Level, e.g. Xyz/Link.)
int | Card.GetRank(Card c) | Returns the current Rank of "c". (Returns 0 if it has no Rank.)
int | Card.GetLink(Card c) | Returns the current Link Rating of "c". (Returns 0 if it has no Link Rating.)
int | Card.GetSynchroLevel(Card c, Card sc) | Returns the Level of "c" if it would be used as a Synchro Material for "sc".
int | Card.GetRitualLevel(Card c, Card rc) | Returns the Level of "c" if it would be Tributed for the Ritual Summon of "rc".
int | Card.GetOriginalLevel(Card c) | Returns the original Level of "c". (Returns 0 if it has no Level, e.g. Xyz/Link.)
int | Card.GetOriginalRank(Card c) | Returns the original Rank of "c". (Returns 0 if it has no Rank.)
bool | Card.IsXyzLevel(Card c, Card xyzc, int lv) | Checks if "c" would be Level "lv" if it was to be used as Xyz Material for "xyzc".
int | Card.GetLeftScale(Card c) | Returns the current left Pendulum Scale of "c". (Returns 0 if it has no Pendulum Scale.)
int | Card.GetOriginalLeftScale(Card c) | Returns the original left Pendulum Scale of "c". (Returns 0 if it has no Pendulum Scale.)
int | Card.GetRightScale(Card c) | Returns the current right Pendulum Scale of "c". (Returns 0 if it has no Pendulum Scale.)
int | Card.GetOriginalRightScale(Card c) | Returns the original right Pendulum Scale of "c". (Returns 0 if it has no Pendulum Scale.)
bool | Card.IsLinkMarker(Card c, int markers) | Checks if (Card c) has the Link markers represented by (int markers)
Group | Card.GetLinkedGroup(Card c) | Returns a group with all the cards that "c" points to. (Returns an empty group if it does not point to any cards.)
int | Card.GetLinkedGroupCount(Card c) | Returns the number of cards that "c" points to.
int | Card.GetLinkedZone(Card c[, int cp = c:GetControler()]) | Returns all the zones that "c" points to (on the field of player "cp").
int | Card.GetFreeLinkedZone(Card c) | Returns all the zones that "c" points to that are not occupied by a card.
Group | Card.GetMutualLinkedGroup(Card c) | Returns a group with all the cards that are co-linked with "c". (Returns an empty group if there are none.)
int | Card.GetMutualLinkedGroupCount(Card c) | Returns the number of cards that are co-linked with "c".
int | Card.GetMutualLinkedZone(Card c, int cp = c:GetControler()) | Gets all zones that (Card c) points to as part of a co-Link, that belong to player (int cp)
bool | Card.IsLinked(Card c) | Checks if "c" is linked. (A card is linked if it is pointing to another card, or if another card is pointing to it.)
Group | Duel.GetFusionMaterial(int player) | Returns a group of cards that are usable as fusion materials by the players, those cards consist of cards in the player's monster zone and also in the player's hand, GY and spell/trap zone that are affected by an EFFECT_EXTRA_FUSION_MATERIAL effect.
-- | -- | --
Group | Card.GetColumnGroup(Card c[, int left\|nil, int right\|nil]) | Returns a group with all the cards that are in the same column as "c". If "left" or "right" are provided, the returned group will also include the cards from the N columns on the left or right of "c" respectively, where N is the number passed for the "left" or "right" parameter.
int | Card.GetColumnGroupCount(Card c[, int left\|nil, int right\|nil]) | Returns the number of cards that are in the same column as "c". If "left" or "right" are provided, the returned number will also include the cards from the N columns on the left or right of "c" respectively, where N is the number passed for the "left" or "right" parameter.
int | Card.GetColumnZone(Card c, int loc[, int left\|nil, int right\|nil, int cp = c:GetControler()\|nil]) | Returns all the zones in the same column as "c" that are part of the location "loc". If "cp" is provided, the returned zones will only include the ones that belong to player "cp". If "left" or "right" are provided, the returned zones will also include the ones from the N columns on the left or right of "c" respectively, where N is the number passed for the "left" or "right" parameter.
bool | Card.IsAllColumn(Card c) | Checks if all the zones of the column that "c" is on are occupied.
int | Card.GetAttribute(Card c[, Card  scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Returns the current Attribute of "c" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
int | Card.GetOriginalAttribute(Card c) | Returns the original Attribute of "c".
int | Card.GetRace(Card c[, Card scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Returns the current Monster Type of "c" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
int | Card.GetOriginalRace(Card c) | Returns the original Monster Type of "c".
int | Card.GetAttack(Card c) | Returns the current ATK of "c".
int | Card.GetBaseAttack(Card c) | Returns the original ATK of "c".
int | Card.GetTextAttack(Card c) | Returns the original printed ATK of "c".
int | Card.GetDefense(Card c) | Returns the current DEF of "c".
int | Card.GetBaseDefense(Card c) | Returns the original DEF of "c".
int | Card.GetTextDefense(Card c) | Returns the original printed DEF of "c".
int, int | Card.GetPreviousCodeOnField(Card c) | Returns the code/ID that "c" had when it was on the field.
int | Card.GetPreviousTypeOnField(Card c) | Returns the card type that "c" had when it was on the field.
int | Card.GetPreviousLevelOnField(Card c) | Returns the Level that "c" had when it was on the field.
int | Card.GetPreviousRankOnField(Card c) | Returns the Rank that "c" had when it was on the field.
int | Card.GetPreviousAttributeOnField(Card c) | Returns the Attribute that "c" had when it was on the field.
int | Card.GetPreviousRaceOnField(Card c) | Returns the Monster Type that "c" had when it was on the field.
int | Card.GetPreviousAttackOnField(Card c) | Returns the ATK that "c" had when it was on the field.
int | Card.GetPreviousDefenseOnField(Card c) | Returns the DEF that "c" had when it was on the field.
int | Card.GetOwner(Card c) | Returns the owner of "c".
int | Card.GetControler(Card c) | Returns the controller of "c".
int | Card.GetPreviousControler(Card c) | Returns the previous controller of "c".
int | Card.GetReason(Card c) | Returns the reason for an event that happened to "c" (e.g. cost, effect).
Card | Card.GetReasonCard(Card c) | Returns the card which is the reason that an event happened to "c".
int | Duel.GetZoneWithLinkedCount(int count, int tp) | Returns a zone flag including the tp's zones that are pointed by at least "count" Link Monsters.
void | Duel.GoatConfirm(int tp, int loc) | Used for goat versions of cards, handle the "fail to find" scenario. It confirms tp's LOCATION_DECK or LOCATION_HAND (passed in loc), the hand is revealed to the opposing player, the deck is revealed to tp.
void | aux.EnableNeosReturn(Card c[, int extracat, function extrainfo, function extraop]) | Adds the effect to shuffle the card into the Extra Deck at the End Phase (most commonly used by "Neos" Fusion Monsters). If provided, "extracat", "extrainfo" and "extraop" will add additional effect categories, operation info and operations respectively to the effect. The Condition, Target and Operation functions of this effect, named NeosReturnCondition1/2, NeosReturnTarget and NeosReturnOperation, are detailed in cards_specific_functions.lua.
bool | Auxiliary.NeosReturnCondition1(e,tp,eg,ep,ev,re,r,rp) | See cards_specific_functions.lua.
bool | Auxiliary.NeosReturnCondition2(e,tp,eg,ep,ev,re,r,rp) | See cards_specific_functions.lua.
void | Auxiliary.NeosReturnTarget(c,extrainfo) | See cards_specific_functions.lua.
void | Auxiliary.NeosReturnOperation(c,extraop) | See cards_specific_functions.lua.
bool | aux.NeosReturnSubstituteFilter(Card c) | Auxiliary filter used by NeosReturnOperation. Returns if Card c can be removed as cost and is Neos Fusion
function | aux.seqmovcon(e,tp,eg,ep,ev,re,r,rp) | Condition for effects that make the monster change its current sequence/column.
function | aux.seqmovop(e,tp,eg,ep,ev,re,r,rp) | Operation for effects that make the monster change its current sequence/column.
function | aux.FilterFaceupFunction(function f, ...) | Filter to check face-up cards that match (function f) where (...) are extra parameters to f. Can be used as the function paramater in SelectMatchingCard/Target and IsExistingMatchingCard/Target.
int | Group.GetToBeLinkedZone(card tc, card c, int tp[, bool clink = false, bool emz = false]) | Returns the zone(s) of a player "tp" such that "c" would point to "tc" if "tc" would be summoned. If "clink" is set to true it will only return the zone(s) so that "c" and "tc" would be co-linked. Set "emz" to true if the summoned monster could be placed in the Extra Monster Zone so that the possibility of Extra Linking is accounted for (see "G Golem Crystal Heart" for an example use).
int | Card.GetToBeLinkedZone(group g, card c, int tp[, bool clink = false, bool emz = false]) | Iterates group g with "Card.GetToBeLinkedZone" operations.
int | Card.GetReasonPlayer(Card c) | Returns the player that is the reason for an event that happened to "c".
Effect | Card.GetReasonEffect(Card c) | Returns the effect which is the reason for an event that happened to "c".
void | Card.SetReason(Card c, int reason[, bool keep=false]) | Sets the reason of "c" as "reason". If "keep" is set to true "c" will maintain the previous reason that it had.
void | Card.SetReasonCard(Card c, Card rc) | Sets "rc" as the card that was the reason of an event that happened to "c".
void | Card.SetReasonPlayer(Card c, int rp) | Sets "rp" as the player that was the reason of an event that happened to "c".
void | Card.SetReasonEffect(Card c, Effect re) | Sets "re" as the effect that was the reason of an event that happened to "c".
int | Card.GetPosition(Card c) | Returns the current position of "c".
int | Card.GetPreviousPosition(Card c) | Returns the previous position of "c".
int | Card.GetBattlePosition(Card c) | Returns the position of "c" at the start of the Damage Step (see "Marshmallon").
int | Card.GetLocation(Card c) | Returns the location of "c".
int | Card.GetPreviousLocation(Card c) | Returns the previous location of "c".
int | Card.GetSequence(Card c) | Gets the sequence/order of the location of (Card c)
int | Card.GetPreviousSequence(Card c) | Gets the sequence/order of the location of (Card c)
int | Card.GetSummonType(Card c) | Gets the type in which (Card c) was Summoned
int | Card.GetSummonLocation(Card c) | Returns the location that "c" was summoned from.
int | Card.GetSummonPlayer(Card c) | Returns the player that summoned "c".
int | Card.GetDestination(Card c) | Returns the location that "c" would be sent to (e.g. when it would be destroyed).
int | Card.GetLeaveFieldDest(Card c) | Returns the location that "c" would be sent to when it leaves the field, while taking into account effects that redirect that location (e.g. "but banish it if it leaves the field").
int | Card.GetTurnID(Card c) | Returns the turn that "c" was sent/placed to its current location.
int | Card.GetFieldID(Card c) | Returns the field ID of "c" when it was placed on the field.
int | Card.GetRealFieldID(Card c) | Returns the unique field ID that "c" has.
int | Card.GetCardID(Card c) | Returns the internal card ID that "c" has. This will be unique per card and won't change during the course of the duel.
bool | Card.IsCode(Card c, int ...) | Checks if "c" has at least 1 code/ID among the "..." list.
bool | Card.IsType(Card c, int type[, Card scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Checks if the card type of "c" is "type" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
bool | Card.IsLevel(Card c, int lv) | Checks if "c" has a Level equal to "lv".
bool | Card.IsRank(Card c, int rk) | Checks if "c" has a Rank equal to "rk".
bool | Card.IsLink(Card c, int lk) | Checks if "c" has a Link Rating equal to "lk".
bool | Card.IsRace(Card c, int race[, Card scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Checks if the Monster Type of "c" is "race" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
bool | Card.IsAttribute(Card c, int attribute[, Card scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Checks if the Attribute of "c" is "attribute" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
bool | Card.IsReason(Card c, int reason) | Checks if the reason for an event that happened to "c" is "reason" (REASON_x).
bool | Card.IsSummonType(Card c, int ...) | Checks if "c" is Summoned by one of the summon types in the "..." list.
bool | Card.IsStatus(Card c, int status) | Checks if "c" has the given status (STATUS_x)
bool | Card.IsNotTuner(Card c) | Checks if "c" is a non-Tuner monster.
void | Card.SetStatus(Card c, int status, bool enable) | Sets the status (STATUS_x) of a Card (Card c) and possibly enables it
bool | Card.IsGeminiState(Card c) | Checks if a Card (Card c) is a Gemini monster with its effect enabled.
void | Card.EnableGeminiState(Card c) | Enables the Gemini effect of a card (Card c).
void | Card.SetTurnCounter(Card c, int counter) | Sets the turn counter of a Card (Card c) to a value (int count)
int | Card.GetTurnCounter(Card c) | Gets the turn counter of a Card (Card c)
void | Card.SetMaterial(Card c, Card\|Group\|nil materials) | Sets the Material of a Card (Card c) to the passed ones. If nil is passed, the material group of the card is cleared.
Group | Card.GetMaterial(Card c) | Gets the material which was used as cost for a Card (Card c)
int | Card.GetMaterialCount(Card c) | Gets the number of materials used as cost for a Card (Card c)
Group | Card.GetEquipGroup(Card c) | Gets a Group of Cards equipped to a Card (Card c)
int | Card.GetEquipCount(Card c) | Gets the number of cards equipped to a Card (Card c)
Card | Card.GetEquipTarget(Card c) | Gets the Card that a Card (Card c) is equipped to
Card | Card.GetPreviousEquipTarget(Card c) | Gets the Card that a Card (Card c) was equipped to
bool | Card.CheckEquipTarget(Card c1, Card c2) | Checks if a Card (Card c1) has another Card (Card c2) as equip target
int | Card.GetUnionCount(Card c) | Gets Amount of Union monsters equipped to a Card (Card c)
Group | Card.GetOverlayGroup(Card c) | Gets the cards overlayed to a Card (Card c)
int | Card.GetOverlayCount(Card c) | Gets the number of cards overlayed to a Card (Card c)
Card | Card.GetOverlayTarget(Card c) | Gets the card that (Card c) is an overlay of
bool | Card.CheckRemoveOverlayCard(Card c, int player, int count, int reason) | Checks if the player (int player) can remove a number (int count) of Xyz materials from a Card c for a specific reason (int reason)
bool | Card.RemoveOverlayCard(Card c, int player, int min, int max, int reason) | Makes player (int Player) remove overlay cards from a Card (Card c), with minimum of (int min) and maximum of (int max) with (int reason) as reason
Group | Card.GetAttackedGroup(Card c) | Gets a group of cards attacked by Card c, cleared before drawing and when starting second Battle Phase
int | Card.GetAttackedGroupCount(Card c) | Gets the number of cards attacked by Card c, set to 0 before drawing and when starting second Battle Phase
int | Card.GetAttackedCount(Card c) | Gets the number of successful(not negated) attacks done by Card c, set to 0 before drawing and when starting second Battle Phase
Group | Card.GetBattledGroup(Card c) | Gets a Group of cards that are battled (all the attacking and the attacked cards), cleared at predraw and when starting second Battle Phase
int | Card.GetBattledGroupCount(Card c) | Gets the count of cards that has battled (all the attacking and the attacked cards)
int | Card.GetAttackAnnouncedCount(Card c) | Gets the number of attacks declared by Card c, set to 0 before drawing and when starting second Battle Phase
bool | Card.IsDirectAttacked(Card c) | Checks if a Card (Card c) has successfully attacked directly
void | Card.SetCardTarget(Card c1, Card c2) | Sets the second card (Card c2) as a target of the first card (Card c1)
Group | Card.GetCardTarget(Card c) | Gets the group of cards that a card (Card c) is assigned targets to
Card | Card.GetFirstCardTarget(Card c) | Get the first of a card (Card c)'s target cards. A bit faster than Card.GetCardTarget(Card c):GetFirst()
int | Card.GetCardTargetCount(Card c) | Gets the number of targets that a card (Card c) is assigned to
bool | Card.IsHasCardTarget(Card c1, Card c2) | Checks whether the second card (Card c2) is a target of the first card (Card c1)
void | Card.CancelCardTarget(Card c1, Card c2) | Removes the second card (Card c2) from the list of the first card (Card c1)'s target
Group | Card.GetOwnerTarget(Card c) | Gets a group of cards (including equips) that a card (Card c) is a target of
int | Card.GetOwnerTargetCount(Card c) | Gets the number of cards (including equips) that a card (Card c) is a target of
Effect | Card.GetActivateEffect(Card c) | Gets a card (Card c)'s EFFECT_TYPE_ACTIVATE effect
Effect[,Group,int,int,Effect,int,int] | Card.CheckActivateEffect(Card c, bool neglect_con, bool neglect_cost, bool copy_info) | Checks a card (Card c)'s EFFECT_TYPE_ACTIVATE effect while checking for whether it can be activated. Returns _nil_ if effect condition is not met. Set _neglect_con_ to _true_ to ignore condition checking. Set _neglect_cost_ to _true_ to ignore cost payable checking. Set _copy_info_ to true to return the activate effect's supposed info, for other than EVENT_FREE_CHAIN usually (eg,ep,ev,r,re,rp)
int | Card.RegisterEffect(Card c, Effect e[, bool forced=false, ...]) | Registers an Effect (Effect e) (usually an Effect created with Effect.CreateEffect()) to a Card (Card c), ... is a list of integers which Registers further effects in the utility.
Effect\|nil | Card.IsHasEffect(Card c, int code) | Checks if a Card (Card c) has an Effect (EFFECT_x)
Effect, ... | Card.GetCardEffect(Card c, [, int effect_code]) | Returns all the effects with that code (int effect_code) registered to card (Card c). With no effect_code (type or effect_code=0) it will return all the effects registered. [effect_code refers to "EFFECT_" constants, eg: EFFECT_NECRO_VALLEY]
void | Card.ResetEffect(Card c, int reset_code, int reset_type) | Resets all effects of a Card (Card c) (e.g. "c:ResetEffect(RESET_DISABLE,RESET_EVENT)")
int | Card.GetEffectCount(Card c, int code) | Gets the amount of an Effect (EFFECT_x) registered to a Card (Card c)
Effect | Card.RegisterFlagEffect(Card c, int code, int reset_flag, int property, int reset_count[, int label, int desc]) | Registers a flag effect to a card (Card c) with (int code) that resets with (int reset_flag), as the effect code. (int reset_flag).
int | Card.GetFlagEffect(Card c, int code) | Returns the amount of flag effects with (int code) as the effect code that are registered to a card (Card c)
void | Card.ResetFlagEffect(Card c, int code) | Resets a flag with (int code) as the effect code from a card (Card c)
bool | Card.SetFlagEffectLabel(Card c, int code, int label) | Assigns an integer (int label) number to the flag effect attached to a card (Card c) with (int code) as the effect code. Returns true if a flag effect with such code existed and the label was set.
int,... | Card.GetFlagEffectLabel(Card c, int code) | Gets the integer labels to the flag effect attached to a card (Card c) with (int code) as the effect code, returns nil if there is no integer label.
void | Card.CreateRelation(Card c1, Card c2, int reset_flag) | Creates a relation between the first card (Card c1) and the second card (Card c2), which will be reset when the first card hits the reset flag
void | Card.ReleaseRelation(Card c1, Card c2) | Releases the relation between the first card (Card c1) and the second card (Card c2). Does not release relation from the second card that is resulting from _c2:CreateRelation(c1)_
void | Card.CreateEffectRelation(Card c, Effect e) | Creates a relation between a card (Card c) and an effect (Effect e)
void | Card.ReleaseEffectRelation(Card c,Effect e) | Releases any relation between a card (Card c) and an effect (Effect e)
void | Card.ClearEffectRelation(Card c) | Clears any relation between a card (Card c) and all effects and chains
bool | Card.IsRelateToEffect(Card c, Effect e) | Checks whether a card (Card c) is related to an effect (Effect e)
bool | Card.IsRelateToChain(Card c, int chainc) | Checks whether a card (Card c) is related to the chain numbered (int chainc)
bool | Card.IsRelateToCard(Card c1, Card c2) | Checks whether a card (Card c1) is related to another card (Card c2) (That results from _c1:CreateRelation(c2)_)
bool | Card.IsRelateToBattle(Card c) | Checks whether a card (Card c) is related to battle (either as attacker or as an attack target)
int | Card.CopyEffect(Card c, int code, int reset_flag[, int reset_count]) | Temporarily adds to a card (Card c) the effect of card with the specified card code (int code) that resets according to the ascribed reset flag (int reset_flag)
int | Card.ReplaceEffect(Card c, int code, int reset_flag[, int reset_count]) | Temporarily replace all effects of a card (Card c) with the effect of card with the specified card code (int code) that resets according to the ascribed reset flag (int reset_flag)
void | Card.EnableUnsummonable(Card c) | Makes a card (Card c) unsummonable except with its own procedure
void | Card.EnableReviveLimit(Card c) | Makes a card (Card c) unsummonable except with its own procedure, or after it's Summon procedure is complete
void | Card.CompleteProcedure(Card c) | Makes a card (Card c) be considered that it's Summon procedure is complete
bool | Card.IsDisabled(Card c) | Checks whether a card (Card c) is disabled, equivalent with c:IsStatus(STATUS_DISABLED)
bool | Card.IsDestructable(Card c[, Effect e]) | Checks whether a card (Card c) can be destroyed; if an effect (effect e) is given, checks whether the card can be destroyed by that effect
bool | Card.IsSummonableCard(Card c) | Checks if a card (Card c) is normally summonable, returns false when the card is subject of Card.EnableUnsummonable or Card.EnableReviveLimit
bool | Card.IsSpecialSummonable(Card c) | Checks if a card (Card c) is summonable by it's summon procedure
bool | Card.IsSynchroSummonable(Card c[, Group\|Card\|nil must_use, Group\|Card\|nil  mg, int min=0, int max=0]) | Checks if "c" can be Synchro Summoned using "must_use" as part of its materials, choosing among "mg", with "min" and "max" materials to be used for the Synchro Summon. How this works is that the script would check for all EFFECT_SPSUMMON_PROC that has SUMMON_TYPE_SYNCHRO as it's Value, then checks the effects' Condition with the provided arguments. Check out "aux.SynCondition" in "proc_synchro.lua" for how this is handled.

<!--EndFragment-->
</body>
</html>
