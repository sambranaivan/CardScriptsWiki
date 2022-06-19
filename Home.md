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

## Functions

Return type | Function |Description
-- | -- | --
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


Return type | Function |Description
-- | -- | --
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


Return type | Function |Description
-- | -- | --
Group | Duel.GetFusionMaterial(int player) | Returns a group of cards that are usable as fusion materials by the players, those cards consist of cards in the player's monster zone and also in the player's hand, GY and spell/trap zone that are affected by an EFFECT_EXTRA_FUSION_MATERIAL effect.
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

## 
Return type | Function |Description
-- | -- | --
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
