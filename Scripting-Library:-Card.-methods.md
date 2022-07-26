return type | function name | description
-- | -- | --
bool | Card.AddCounter(Card c, int countertype, int count[, int singly=false]) | Adds a number (int count) of the specified counter (int countertype) to a card (Card c). If singly is set to a number, then it will be added by that number each time. When the number of added counter would exceed the limit for that card, it is not added.
void | Card.AddMonsterAttribute(Card c, int extra_type, [int attribute, int race, int level, int atk, int def]) | Transforms a card (Card c) to a monster. The card type will become TYPE_MONSTER + extra_type. Uses the values if provided, otherwise uses the card's own values in Database. Be aware that the values added using this (except for Card type) will be reset when the card is flipped face-down.
void | Card.AddMonsterAttributeComplete(Card c) | Used in conjunction with Card.AddMonsterAttribute, completes a card's (Card c) transformation to a monster. It is best to call this after the card has arrived in Monster Zone (i.e. after Duel.SpecialSummonStep). Does nothing with cards without EFFECT_PRE_MONSTER (added automatically by Card.AddMonsterAttribute).
table | Card.AddSetCodeRules(card c, ...) |  
void\|int | Card.Alias(Card c[, int code]) | Changes (Card c)'s alias if (int code) is inputted, else returns the current card's alias.
int | Card.AnnounceAnotherAttribute(Card c, int player) | Makes (int player) announce an attribute different from the one(s) (Card c) currently has
int | Card.AnnounceAnotherRace(Card c, int player) | Makes (int player) announce a monster type (Race) different from the one(s) (Card c) currently has
void | Card.AssumeProperty(Card c,int assume_type, int assume_value) | Assume a property for a card (Card c), the card will be considered as having an assumed specific property (int assume_type) as the inputted value (int assume_value) (only as long as the function is still processing)
void\|int | Card.Attack(Card c[, int val]) | Changes (Card c)'s original ATK if (int val) is inputted, else returns the current card's original ATK.
void\|int | Card.Attribute(Card c[, int att]) | Changes (Card c)'s original attribute(s) if (int att) is inputed, else returns the current card's original attribute(s).
void | Card.CancelCardTarget(Card c1, Card c2) | Removes the second card (Card c2) from the list of the first card (Card c1)'s target
void | Card.CancelToGrave(Card c[, bool cancel=true]) | if cancel is true, cancels the to-grave rule and movement of a card (Card c). If false, enforce the rule that it must go from the field to Graveyard instead.
bool | Card.CanChainAttack(Card c[, int ac = 2, bool monsteronly = false]) | Checks if a card (Card c) can make a follow-up attack. Specifying the integer ac checks whether it can attack that number of times. Setting monsteronly to true checks only the possibility of follow-up attack to monster
bool | Card.CanSummonOrSet(...) | Returns if the card passed can be normal summoned or normal set.
Effect[,Group,int,int,Effect,int,int] | Card.CheckActivateEffect(Card c, bool neglect_con, bool neglect_cost, bool copy_info) | Checks a card (Card c)'s EFFECT_TYPE_ACTIVATE effect while checking for whether it can be activated. Returns _nil_ if effect condition is not met. Set _neglect_con_ to _true_ to ignore condition checking. Set _neglect_cost_ to _true_ to ignore cost payable checking. Set _copy_info_ to true to return the activate effect's supposed info, for other than EVENT_FREE_CHAIN usually (eg,ep,ev,r,re,rp)
bool | Card.CheckAdjacent(card c) | Returns if either of the sequences next to the card c's sequence is available. Already handles the Extra monster zone (sequence > 4). Limited to Monster Zones.
bool | Card.CheckEquipTarget(Card c1, Card c2) | Checks if a Card (Card c1) has another Card (Card c2) as equip target
bool | Card.CheckFusionMaterial(Card c[, Group g, Card gc\|nil, int chkf=PLAYER_NONE]) | Check if g contains a set of fusion material that c needs [must contain gc]## Check the Condition function for the effect of EFFECT_FUSION_MATERIAL according to the type of c
bool | Card.CheckFusionSubstitute(Card c, Card fc) | Checks if a card (Card c) can be treated as a substitute for one of a Fusion Monster's (Card fc) Fusion Material.
bool | Card.CheckRemoveOverlayCard(Card c, int player, int count, int reason) | Checks if the player (int player) can remove a number (int count) of Xyz materials from a Card c for a specific reason (int reason)
bool | Card.CheckUniqueOnField(Card c,int check_player) | Checks if a card's (Card c) going to a player's (int player) field would violate the "Can only control 1" clause
void | Card.ClearEffectRelation(Card c) | Clears any relation between a card (Card c) and all effects and chains
void\|int | Card.Code(Card c[, int code]) | Changes (Card c)'s original card name if (int code) is inputted, else returns the current original card name.
void | Card.CompleteProcedure(Card c) | Makes a card (Card c) be considered that it's Summon procedure is complete
int | Card.CopyEffect(Card c, int code, int reset_flag[, int reset_count]) | Temporarily adds to a card (Card c) the effect of card with the specified card code (int code) that resets according to the ascribed reset flag (int reset_flag)
void | Card.CreateEffectRelation(Card c, Effect e) | Creates a relation between a card (Card c) and an effect (Effect e)
void | Card.CreateRelation(Card c1, Card c2, int reset_flag) | Creates a relation between the first card (Card c1) and the second card (Card c2), which will be reset when the first card hits the reset flag
void\|int | Card.Defense(Card c[, int val]) | Changes (Card c)'s original DEF if (int val) is inputted, else returns the current card's original DEF.
void | Card.EnableCounterPermit(Card c, int countertype[, int location]) | Makes the card (Card c) able to hold a type of counter (int countertype). If a location is provided (int location), the card will be able to hold counter only when in the specified location.
void | Card.EnableGeminiState(Card c) | Enables the Gemini effect of a card (Card c).
void | Card.EnableReviveLimit(Card c) | Makes a card (Card c) unsummonable except with its own procedure, or after it's Summon procedure is complete
void | Card.EnableUnsummonable(Card c) | Makes a card (Card c) unsummonable except with its own procedure
Card | Card.FromLuaRef(int ref) | Returns a Card object from a given lua reference. The function errors out if the reference is invalid or does not refer to a Card object.
Effect | Card.GetActivateEffect(Card c) | Gets a card (Card c)'s EFFECT_TYPE_ACTIVATE effect
int | Card.GetAttack(Card c) | Returns the current ATK of "c".
Group,bool | Card.GetAttackableTarget(Card c) | Gets a card's (Card c) valid attack targets
int | Card.GetAttackAnnouncedCount(Card c) | Gets the number of attacks declared by Card c, set to 0 before drawing and when starting second Battle Phase
int | Card.GetAttackedCount(Card c) | Gets the number of successful(not negated) attacks done by Card c, set to 0 before drawing and when starting second Battle Phase
Group | Card.GetAttackedGroup(Card c) | Gets a group of cards attacked by Card c, cleared before drawing and when starting second Battle Phase
int | Card.GetAttackedGroupCount(Card c) | Gets the number of cards attacked by Card c, set to 0 before drawing and when starting second Battle Phase
int | Card.GetAttribute(Card c[, Card  scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Returns the current Attribute of "c" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
int | Card.GetBaseAttack(Card c) | Returns the original ATK of "c".
int | Card.GetBaseDefense(Card c) | Returns the original DEF of "c".
Group | Card.GetBattledGroup(Card c) | Gets a Group of cards that are battled (all the attacking and the attacked cards), cleared at predraw and when starting second Battle Phase
int | Card.GetBattledGroupCount(Card c) | Gets the count of cards that has battled (all the attacking and the attacked cards)
int | Card.GetBattlePosition(Card c) | Returns the position of "c" at the start of the Damage Step (see "Marshmallon").
Card | Card.GetBattleTarget(Card c) | Gets a card's (Card c) current battle target
Effect, ... | Card.GetCardEffect(Card c, [, int effect_code]) | Returns all the effects with that code (int effect_code) registered to card (Card c). With no effect_code (type or effect_code=0) it will return all the effects registered. [effect_code refers to "EFFECT_" constants, eg: EFFECT_NECRO_VALLEY]
int | Card.GetCardID(Card c) | Returns the internal card ID that "c" has. This will be unique per card and won't change during the course of the duel.
Group | Card.GetCardTarget(Card c) | Gets the group of cards that a card (Card c) is assigned targets to
int | Card.GetCardTargetCount(Card c) | Gets the number of targets that a card (Card c) is assigned to
int[,int] | Card.GetCode(Card c) | Returns the current code (ID/name) of the card "c".
Group | Card.GetColumnGroup(Card c[, int left\|nil, int right\|nil]) | Returns a group with all the cards that are in the same column as "c". If "left" or "right" are provided, the returned group will also include the cards from the N columns on the left or right of "c" respectively, where N is the number passed for the "left" or "right" parameter.
int | Card.GetColumnGroupCount(Card c[, int left\|nil, int right\|nil]) | Returns the number of cards that are in the same column as "c". If "left" or "right" are provided, the returned number will also include the cards from the N columns on the left or right of "c" respectively, where N is the number passed for the "left" or "right" parameter.
int | Card.GetColumnZone(Card c, int loc[, int left\|nil, int right\|nil, int cp = c:GetControler()\|nil]) | Returns all the zones in the same column as "c" that are part of the location "loc". If "cp" is provided, the returned zones will only include the ones that belong to player "cp". If "left" or "right" are provided, the returned zones will also include the ones from the N columns on the left or right of "c" respectively, where N is the number passed for the "left" or "right" parameter.
int | Card.GetControler(Card c) | Returns the controller of "c".
int | Card.GetCounter(Card c, int countertype) | Returns the number of counters of a specific type (int countertype) on a card (Card c).
int | Card.GetDefense(Card c) | Returns the current DEF of "c".
int | Card.GetDestination(Card c) | Returns the location that "c" would be sent to (e.g. when it would be destroyed).
int | Card.GetEffectCount(Card c, int code) | Gets the amount of an Effect (EFFECT_x) registered to a Card (Card c)
int | Card.GetEquipCount(Card c) | Gets the number of cards equipped to a Card (Card c)
Group | Card.GetEquipGroup(Card c) | Gets a Group of Cards equipped to a Card (Card c)
Card | Card.GetEquipTarget(Card c) | Gets the Card that a Card (Card c) is equipped to
int | Card.GetFieldID(Card c) | Returns the field ID of "c" when it was placed on the field.
Card | Card.GetFirstCardTarget(Card c) | Get the first of a card (Card c)'s target cards. A bit faster than Card.GetCardTarget(Card c):GetFirst()
int | Card.GetFlagEffect(Card c, int code) | Returns the amount of flag effects with (int code) as the effect code that are registered to a card (Card c)
int,... | Card.GetFlagEffectLabel(Card c, int code) | Gets the integer labels to the flag effect attached to a card (Card c) with (int code) as the effect code, returns nil if there is no integer label.
int | Card.GetFreeLinkedZone(Card c) | Returns all the zones that "c" points to that are not occupied by a card.
int, int ... | Card.GetFusionCode(Card c) | Returns the code/ID that "c" has as a Fusion Material (see "Fusion Tag").
int ... | Card.GetFusionSetCard(Card c) | Returns the archetype(s) that "c" is a part of if it is to be used as a Fusion Material.
int | Card.GetLeaveFieldDest(Card c) | Returns the location that "c" would be sent to when it leaves the field, while taking into account effects that redirect that location (e.g. "but banish it if it leaves the field").
int | Card.GetLeftScale(Card c) | Returns the current left Pendulum Scale of "c". (Returns 0 if it has no Pendulum Scale.)
int | Card.GetLevel(Card c) | Returns the current Level of "c". (Returns 0 if it has no Level, e.g. Xyz/Link.)
int | Card.GetLink(Card c) | Returns the current Link Rating of "c". (Returns 0 if it has no Link Rating.)
int, int ... | Card.GetLinkCode(Card c) | Returns the code/ID that "c" has as a Link Material (see "Formud Skipper").
Group | Card.GetLinkedGroup(Card c) | Returns a group with all the cards that "c" points to. (Returns an empty group if it does not point to any cards.)
int | Card.GetLinkedGroupCount(Card c) | Returns the number of cards that "c" points to.
int | Card.GetLinkedZone(Card c[, int cp = c:GetControler()]) | Returns all the zones that "c" points to (on the field of player "cp").
int | Card.GetLocation(Card c) | Returns the location of "c".
int | Card.GetLuaRef(Card c) | Returns an integer representing the internal value used by lua to access the Card c.
Group | Card.GetMaterial(Card c) | Gets the material which was used as cost for a Card (Card c)
int | Card.GetMaterialCount(Card c) | Gets the number of materials used as cost for a Card (Card c)
table | Card.GetMetatable(card c, code current_code) | Similar to Duel.GetMetatable, but if current_code is true it behaves as if it were Duel.GetMetatable(c:GetCode()), otherwise it returns the __index field of the card's object (this difference only matters when a card's id is not its original one, like when copying names via effect or having an alias)
Group | Card.GetMutualLinkedGroup(Card c) | Returns a group with all the cards that are co-linked with "c". (Returns an empty group if there are none.)
int | Card.GetMutualLinkedGroupCount(Card c) | Returns the number of cards that are co-linked with "c".
int | Card.GetMutualLinkedZone(Card c, int cp = c:GetControler()) | Gets all zones that (Card c) points to as part of a co-Link, that belong to player (int cp)
int | Card.GetOriginalAttribute(Card c) | Returns the original Attribute of "c".
int | Card.GetOriginalCode(Card c) | Returns the original printed code (ID/name) of the card "c".
int, int | Card.GetOriginalCodeRule(Card c) | Returns the original code (ID/name) of the card "c" while taking into account name clauses/alias (used for the "original name" wording).
int | Card.GetOriginalLeftScale(Card c) | Returns the original left Pendulum Scale of "c". (Returns 0 if it has no Pendulum Scale.)
int | Card.GetOriginalLevel(Card c) | Returns the original Level of "c". (Returns 0 if it has no Level, e.g. Xyz/Link.)
int | Card.GetOriginalRace(Card c) | Returns the original Monster Type of "c".
int | Card.GetOriginalRank(Card c) | Returns the original Rank of "c". (Returns 0 if it has no Rank.)
int | Card.GetOriginalRightScale(Card c) | Returns the original right Pendulum Scale of "c". (Returns 0 if it has no Pendulum Scale.)
int ... | Card.GetOriginalSetCard(Card c) | Returns the original archetype(s) that "c" is a part of.
int | Card.GetOriginalType(Card c) | Returns the original card type (Monster/Spell/Trap) of "c".
int | Card.GetOverlayCount(Card c) | Gets the number of cards overlayed to a Card (Card c)
Group | Card.GetOverlayGroup(Card c) | Gets the cards overlayed to a Card (Card c)
Card | Card.GetOverlayTarget(Card c) | Gets the card that (Card c) is an overlay of
int | Card.GetOwner(Card c) | Returns the owner of "c".
Group | Card.GetOwnerTarget(Card c) | Gets a group of cards (including equips) that a card (Card c) is a target of
int | Card.GetOwnerTargetCount(Card c) | Gets the number of cards (including equips) that a card (Card c) is a target of
int | Card.GetPosition(Card c) | Returns the current position of "c".
int | Card.GetPreviousAttackOnField(Card c) | Returns the ATK that "c" had when it was on the field.
int | Card.GetPreviousAttributeOnField(Card c) | Returns the Attribute that "c" had when it was on the field.
int, int | Card.GetPreviousCodeOnField(Card c) | Returns the code/ID that "c" had when it was on the field.
int | Card.GetPreviousControler(Card c) | Returns the previous controller of "c".
int | Card.GetPreviousDefenseOnField(Card c) | Returns the DEF that "c" had when it was on the field.
Card | Card.GetPreviousEquipTarget(Card c) | Gets the Card that a Card (Card c) was equipped to
int | Card.GetPreviousLevelOnField(Card c) | Returns the Level that "c" had when it was on the field.
int | Card.GetPreviousLocation(Card c) | Returns the previous location of "c".
int | Card.GetPreviousPosition(Card c) | Returns the previous position of "c".
int | Card.GetPreviousRaceOnField(Card c) | Returns the Monster Type that "c" had when it was on the field.
int | Card.GetPreviousRankOnField(Card c) | Returns the Rank that "c" had when it was on the field.
int | Card.GetPreviousSequence(Card c) | Gets the sequence/order of the location of (Card c)
int ... | Card.GetPreviousSetCard(Card c) | Returns the archetype(s) that "c" was part of previously.
int | Card.GetPreviousTypeOnField(Card c) | Returns the card type that "c" had when it was on the field.
int | Card.GetRace(Card c[, Card scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Returns the current Monster Type of "c" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
int | Card.GetRank(Card c) | Returns the current Rank of "c". (Returns 0 if it has no Rank.)
int | Card.GetRealFieldID(Card c) | Returns the unique field ID that "c" has.
int | Card.GetReason(Card c) | Returns the reason for an event that happened to "c" (e.g. cost, effect).
Card | Card.GetReasonCard(Card c) | Returns the card which is the reason that an event happened to "c".
Effect | Card.GetReasonEffect(Card c) | Returns the effect which is the reason for an event that happened to "c".
int | Card.GetReasonPlayer(Card c) | Returns the player that is the reason for an event that happened to "c".
int | Card.GetRightScale(Card c) | Returns the current right Pendulum Scale of "c". (Returns 0 if it has no Pendulum Scale.)
int | Card.GetRitualLevel(Card c, Card rc) | Returns the Level of "c" if it would be Tributed for the Ritual Summon of "rc".
int | Card.GetScale(Card c) | Returns the scale value that (Card c) has. If c is not TYPE_PENDULUM, returns 0. Runs on the assumption that both scales have the same value, returning the value for the left scale if the card is not on the Pendulum Zone. For cards with different values for the scales (no official card at the moment), returns the left scale if the card is in the left Pendulum Zone or the right scale, if it is in the right Pendulum Zone.
int | Card.GetSequence(Card c) | Gets the sequence/order of the location of (Card c)
int ... | Card.GetSetCard(Card c[, Card\|nil scard, int sumtype=0, int playerid=PLAYER_NONE]) | Returns the archetype(s) that "c" has (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
int | Card.GetSummonLocation(Card c) | Returns the location that "c" was summoned from.
int | Card.GetSummonPlayer(Card c) | Returns the player that summoned "c".
int | Card.GetSummonType(Card c) | Gets the type in which (Card c) was Summoned
int | Card.GetSynchroLevel(Card c, Card sc) | Returns the Level of "c" if it would be used as a Synchro Material for "sc".
int | Card.GetTextAttack(Card c) | Returns the original printed ATK of "c".
int | Card.GetTextDefense(Card c) | Returns the original printed DEF of "c".
int | Card.GetToBeLinkedZone(group g, card c, int tp[, bool clink = false, bool emz = false]) | Iterates group g with "Card.GetToBeLinkedZone" operations.
int,int | Card.GetTributeRequirement(Card c) | Give a min and a max tribute requirement of a card
int | Card.GetTurnCounter(Card c) | Gets the turn counter of a Card (Card c)
int | Card.GetTurnID(Card c) | Returns the turn that "c" was sent/placed to its current location.
int | Card.GetType(Card c[, Card\|nil scard, int sumtype = 0, int playerid = PLAYER_NONE]) | Gets the current type of a Card (Card c) where (Card scard) if provided checks the monster that (Card c) would be used as material, (int sumtype) is for checking the summon type and (int playerid) is the player checking the type.
int | Card.GetUnionCount(Card c) | Gets Amount of Union monsters equipped to a Card (Card c)
bool | Card.HasLevel(Card c) | Returns if a Card (Card c) has a level. for Links: false; for Xyzs: false, except if affected by  "EFFECT_RANK_LEVEL..." or similar effects; for Dark Synchros: true, because they have a negative level; for level 0 monsters: true, because 0 is a value.
bool | Card.IsAbleToChangeControler(Card c) | Checks if a card (Card c) is capable of having it's control changed. Checks only whether the card is affected by EFFECT_CANNOT_CHANGE_CONTROL.
bool | Card.IsAbleToDeck(Card c) | Return if the card c can be returned to the Deck (return true or false)
bool | Card.IsAbleToDeckAsCost(Card c) | Checks if a card (Card c) is able to go to the Deck as a cost
bool | Card.IsAbleToDeckOrExtraAsCost(Card c) | Checks if a card (Card c) is able to go to either the Deck or the Extra Deck as a cost
bool | Card.IsAbleToExtra(Card c) | Return if the card c can be returned to the Extra Deck (return true or false)
bool | Card.IsAbleToExtraAsCost(Card c) | Checks if a card (Card c) is able to go to the Extra Deck as a cost
bool | Card.IsAbleToGrave(Card c) | Checks if a card (Card c) is able to go to the Graveyard
bool | Card.IsAbleToGraveAsCost(Card c) | Checks if a card (Card c) is able to go to the Graveyard as a cost
bool | Card.IsAbleToHand(Card c) | Return if the card c can be returned to the hand (return true or false)
bool | Card.IsAbleToHandAsCost(Card c) | Checks if a card (Card c) is able to go to the Hand as a cost
bool | Card.IsAbleToRemove(Card c[, int player]) | Checks if a card (Card c) is able to be banished
bool | Card.IsAbleToRemoveAsCost(Card c) | Checks if a card (Card c) is able to be banished as a cost
bool | Card.IsAllColumn(Card c) | Checks if all the zones of the column that "c" is on are occupied.
bool | Card.IsAttack(Card c, int value) | Returns if a card (Card c) has an ATK equal to int value
bool | Card.IsAttackAbove(Card c, int atk) | Checks if a card (Card c) has ATK equal or above the specified number (int attack), will return false if the card has ? ATK and is not face-up on the field.
bool | Card.IsAttackBelow(Card c, int atk) | Checks if a card (Card c) has ATK equal or below the specified number (int attack), will return false if the card has ? ATK and is not face-up on the field.
bool | Card.IsAttackPos(Card c) | Checks if a card (Card c) is in Attack position
bool | Card.IsAttribute(Card c, int attribute[, Card scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Checks if the Attribute of "c" is "attribute" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
bool | Card.IsBattleDestroyed(Card c) | Returns if (Card c) has been confirmed to be destroyed by battle
bool | Card.IsCanAddCounter(Card c, int countertype, int count[, bool least_one=false, int loc = 0]) | Checks if a number (int count) of the specified counter (int countertype) can be added to a card (Card c). When the number of added counter would exceed the limit for that card, if "least_one" is set to true, then it will return true if at least one more counter can be added otherwise it will return false. If location is specified, it return if it could receive counter when placed on that location.
bool | Card.IsCanAttack(Card c) | Checks if a card (Card c) can attack
bool | Card.IsCanBeBattleTarget(Card c1, Card c2) | Checks if a card (Card c1) is a valid battle target for another card (Card c2)
bool | Card.IsCanBeEffectTarget(Card c, Effect e) | Checks if a card (Card c) is targetable by an effect (Effect e)
bool | Card.IsCanBeFusionMaterial(Card c[, Card fc, bool ignore_mon=false]) | Checks if a card (Card c) can be a Fusion material. If (Card fc) is provided, checks if it can be a Fusion Material for that card. If ignore_mon is true, it does not check whether the card is a monster.
bool | Card.IsCanBeLinkMaterial(Card c, [Card linkc, int player]) | Checks if (Card c) can be used as material for a (Card linkc). "player" is only an additional parameter, is used to send it to the functions as an additional parameter, such as target (function in SetTarget) or operation (function in SetOperation).
bool | Card.IsCanBeMaterial(Card c, int summontype) | Checks if a effect_spsummon_condition is beign applied and is false. It is the generic IscanbeXmaterial
bool | Card.IsCanBeRitualMaterial(Card c[, Card sc]) | Checks if a card (Card c) can be used as Tribute for Ritual Summon. If (Card sc) is provided, checks if it can be used as Tribute for that card's Ritual Summon.
bool | Card.IsCanBeSpecialSummoned(Card c, Effect e, int sumtype, int sumplayer, bool nocheck, bool nolimit[, int sumpos=POS_FACEUP, int target_player=sumplayer]) | Checks whether a card (Card c) can be Special Summoned by (Effect e), by a summon of type (int sumtype), by player (int sumplayer), in position (int sumpos), to (int target_player)'s side of the field. If (bool nocheck) is true, it will check for a summon ignoring conditions. If (bool nolimit) is true, it will check for a summon ignoring the revive limit.
bool | Card.IsCanBeSynchroMaterial(Card c[, Card sc, Card tuner]) | Checks if a card (Card c) can be used as a Synchro Material. If (Card sc) is provided, checks if it can be a Synchro Material for that card. If (Card tuner) is also provided, also checks if it can be a Synchro Material if the tuner if that card.
bool | Card.IsCanBeXyzMaterial(Card c, Card sc\|nil) | Checks if a card (Card c) can be used as an Xyz Material. If (Card sc) is provided, checks if it can be used for that card's Xyz Summon.
bool | Card.IsCanChangePosition(Card c) | Checks if the given (Card c) can change its battle position
bool | Card.IsCanRemoveCounter(Card c, int player, int countertype, int count, int reason) | Checks if a number (int count) of the specified counter (int countertype) can be removed from a card (Card c), with reason described by (int reason)
bool | Card.IsCanTurnSet(Card c) | Checks if a card (Card c) can be made to face-down position (Set)
bool | Card.IsCode(Card c, int ...) | Checks if "c" has at least 1 code/ID among the "..." list.
bool | Card.IsColumn(Card c, int seq, int tp, int loc) | Checks (Card c) its column using the data of another card which allows checking even if the other card has already left the field using its Sequence (int seq), controller (int tp) and location (int loc)
bool | Card.IsControler(Card c, int controler) | Checks if a card (Card c) has player (int p) as it's controller
bool | Card.IsControlerCanBeChanged(Card c[, bool ign = false, int zone = 0xff]) | Checks if a card (Card c) can change control. Checks whether the card is in Monster Zone and whether the opposing player has enough space, in addition of checking for EFFECT_CANNOT_CHANGE_CONTROL. if a zone is provided, it uses only these zones as references. (also ign is supposed to be ignore monster zone checking)
bool | Card.IsDefense(Card c, int value) | Returns if a card (Card c) has an DEF equal to int value
bool | Card.IsDefenseAbove(Card c, int def) | Checks if a card (Card c) has DEF equal or above the specified number (int defense), will return false if the card has ? DEF and is not face-up on the field.
bool | Card.IsDefenseBelow(Card c, int def) | Checks if a card (Card c) has DEF equal or below the specified number (int defense), will return false if the card has ? DEF and is not face-up on the field.
bool | Card.IsDefensePos(Card c) | Checks if a card (Card c) is in Defense position
bool | Card.IsDeleted(Card c) | Returns if the Card object got internally deleted and remained as dangling reference inside the lua state.
bool | Card.IsDestructable(Card c[, Effect e]) | Checks whether a card (Card c) can be destroyed; if an effect (effect e) is given, checks whether the card can be destroyed by that effect
bool | Card.IsDifferentAttribute(Card c, int att) | Returns if (Card c) does not have attribute (int att)
bool | Card.IsDifferentAttribute(Card c, int race) | Returns if (Card c) does not have Race (int race)
bool | Card.IsDirectAttacked(Card c) | Checks if a Card (Card c) has successfully attacked directly
bool | Card.IsDisabled(Card c) | Checks whether a card (Card c) is disabled, equivalent with c:IsStatus(STATUS_DISABLED)
bool | Card.IsDiscardable(Card[, int reason=REASON_COST]) | Checks if a card (Card c) can be discarded for (int reason).
bool | Card.IsEvenScale(Card c) | Returns if a pendulum card (Card c) is a card with an even value for the scale, using Card.GetScale to get the value.
bool | Card.IsExtraLinked(Card c) | Checks if a card is Extra Linked, uses aux.ExtraLinked which obtains 2 Extra Monster Zone monsters of each player and checks if (Card c) is included in the chain of co-linked cards.
bool | Card.IsFacedown(Card c) | Checks if a card (Card c) is face-down
bool | Card.IsFaceup(Card c) | Checks if a card (Card c) is face-up
bool | Card.IsForbidden(Card c) | Checks if a card (Card c) is forbidden to be used (equal to calling c:IsStatus(STATUS_FORBIDDEN))
bool | Card.IsFusionCode(Card c, int ...) | Checks if "c" has a specific code from the "..." list as a Fusion Material.
bool | Card.IsFusionSetCard(Card c, int setname) | Checks if "c" is part of the archetype "setname" if it is to be used as a Fusion Material.
bool | Card.IsFusionSummonableCard |  
bool | Card.IsGeminiState(Card c) | Checks if a Card (Card c) is a Gemini monster with its effect enabled.
bool | Card.IsHasCardTarget(Card c1, Card c2) | Checks whether the second card (Card c2) is a target of the first card (Card c1)
Effect\|nil | Card.IsHasEffect(Card c, int code) | Checks if a Card (Card c) has an Effect (EFFECT_x)
bool | Card.IsImmuneToEffect(Card c, Effect e) | Checks if a card (Card c) is not affected by an effect (Effect e)
bool | Card.IsInExtraMZone(Card c, int tp) | Return if (Card c) is in an Extra Monster Zone. If (int tp) is provided, also returns if (Card c) is of that controller.
bool | Card.IsInMainMZone(Card c, int tp) | Return if (Card c) is in a Main Monster Zone. If (int tp) is provided, also returns if (Card c) is of that controller.
bool | Card.IsLevel(Card c, int lv) | Checks if "c" has a Level equal to "lv".
bool | Card.IsLevelAbove(Card c, int level) | Checks if a card (Card c) has level equal or above the specified number (int level), will return false if the card has no level.
bool | Card.IsLevelBelow(Card c, int level) | Checks if a card (Card c) has level equal or below the specified number (int level), will return false if the card has no level.
bool | Card.IsLink(Card c, int lk) | Checks if "c" has a Link Rating equal to "lk".
bool | Card.IsLinkAbove (Card c, int link_rating) | Checks if (Card c) has a Link Rating (link_rating) equal or greater than the given number
bool | Card.IsLinkBelow (Card c, int link_rating) | Checks if (Card c) has a Link Rating (link_rating) equal or lower than the given number
bool | Card.IsLinkCode(Card c, int ...) | Checks if "c" has a specific code from the "..." list as a Link Material.
bool | Card.IsLinked(Card c) | Checks if "c" is linked. (A card is linked if it is pointing to another card, or if another card is pointing to it.)
bool | Card.IsLinkMarker(Card c, int markers) | Checks if (Card c) has the Link markers represented by (int markers)
bool | Card.IsLinkMonster(card c) | Returns if Card C is a Link Monster. This function was added due to the introduction of Link Spells that makes checking only for IsType==TYPE_LINK not accurate depending on the effect used.
bool | Card.IsLinkSetCard(Card c, int setname) | Checks if "c" is part of the archetype "setname" as a Link Material.
bool | Card.IsLinkSpell(card c) | Returns if Card C is a Link Spell.
bool | Card.IsLinkSummonable(Card c[, Group\|Card\|nil must_use, Group\|Card\|nil  mg, int min=0, int max=0]) | Checks if "c" can be Link Summoned using "must_use" as part of its materials, choosing among "mg", with "min" and "max" materials to be used for the Link Summon.
bool | Card.IsLocation(Card c, int location) | Checks if a card (Card c) is located on the specified location (int location)
bool | Card.IsMonster(Card c) | Returns if (Card c) is a monster type card
bool | Card.IsMSetable(Card, bool ignore_count, Effect e\|nil[, int min=0]) | Checks whether a card (Card c) can be Normal Set as a monster. Setting ignore_count to true makes it ignore the standard once per turn summon limit. If an effect (Effect e) is given, checks whether it can be Normal Summoned by that effect. The last value denotes the minimum tribute amount.
bool | Card.IsNonEffectMonster(Card c) | Returns if (Card c) is a Monster and does not have TYPE_EFFECT
bool | Card.IsNotTuner(Card c) | Checks if "c" is a non-Tuner monster.
bool | Card.IsOddScale(Card c) | Returns if a pendulum card (Card c) is a card with an odd value for the scale, using Card.GetScale to get the value.
bool | Card.IsOnField(Card c) | Checks if a card (Card c) is located on the field
bool | Card.IsOriginalAttribute(Card c, int val) | Checks if (Card c) is of original attribute (int val)
bool | Card.IsOriginalCode(Card c, int cd) | Checks if (Card c) has original card name of (int cd)
bool | Card.IsOriginalCodeRule(Card c, int cd) | Checks if (Card c) has original code rule of (int cd)
bool | Card.IsOriginalRace(Card c, int val) | Checks if (Card c) is of original monster type (int val)
bool | Card.IsOriginalSetCard(Card c, int setname) | Checks if "c" is originally part of the archetype "setname".
bool | Card.IsOriginalType(Card c, int val) | Checks if (Card c) is of original card type (int val)
bool | Card.IsPosition(Card c, int pos) | Checks if a card (Card c) is in the specified position (int pos)
bool | Card.IsPreviousControler(Card c, int tp) | Checks if (Card c) is previous controlled by player (int tp)
bool | Card.IsPreviousLocation(Card c, int location) | Checks if a card (Card c) is previously located on the specified location (int location)
bool | Card.IsPreviousPosition(Card c, int pos) | Checks if a card (Card c) is previously in the specified position (int pos)
bool | Card.IsPreviousSetCard(Card c, int setname) | Checks if "c" was previously part of the archetype "setname".
bool | Card.IsProcedureSummonable(Card c, int cardtype, int sumtype[, Group\|Card\|nil must_use, Group\|Card\|nil  mg, int min=0, int max=0]) | Checks if "c" or type "cardtype" can be Summoned according to the "sumtype" procedure using "must_use" as part of its materials, choosing among "mg", with "min" and "max" materials to be used for the Xyz Summon
bool | Card.IsPublic(Card c) | Checks if a card's (Card c) information is known to both players. In practice, about the same as c:IsPosition(POS_FACEUP)
bool | Card.IsRace(Card c, int race[, Card scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Checks if the Monster Type of "c" is "race" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
bool | Card.IsRank(Card c, int rk) | Checks if "c" has a Rank equal to "rk".
bool | Card.IsRankAbove(Card c, int rank) | Checks if a card (Card c) has rank equal or above the specified number (int rank), will return false if the card has no rank
bool | Card.IsRankBelow(Card c, int rank) | Checks if a card (Card c) has rank equal or below the specified number (int rank), will return false if the card has no rank
bool | Card.IsReason(Card c, int reason) | Checks if the reason for an event that happened to "c" is "reason" (REASON_x).
bool | Card.IsReincarnationSummoned(Card c) | Interacts with the functions for "Salamangreat" Reincarnation procedure. Returns if card c has CARD_SALAMANGREAT_SANCTUARY as FlagEffect
bool | Card.IsRelateToBattle(Card c) | Checks whether a card (Card c) is related to battle (either as attacker or as an attack target)
bool | Card.IsRelateToCard(Card c1, Card c2) | Checks whether a card (Card c1) is related to another card (Card c2) (That results from _c1:CreateRelation(c2)_)
bool | Card.IsRelateToChain(Card c, int chainc) | Checks whether a card (Card c) is related to the chain numbered (int chainc)
bool | Card.IsRelateToEffect(Card c, Effect e) | Checks whether a card (Card c) is related to an effect (Effect e)
bool | Card.IsReleasable(Card c) | Checks if a card (Card c) is able to be Tributed
bool | Card.IsReleasableByEffect(Card c) | Checks if a card (Card c) is able to be Tributed by a card effect
bool | Card.IsRitualMonster(Card c) | Returns if (Card c) is a Ritual Monster.
bool | Card.IsRitualSpell(Card c) | Returns if (Card c) is a Ritual Spell.
bool | Card.IsSequence(c, ...) | Returns if a Card (Card c) is located at any of the sequences passed as arguments
bool | Card.IsSetCard(Card c, int setname[, Card scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Checks if "c" is part of the archetype "setname" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
bool | Card.IsSpecialSummonable(Card c) | Checks if a card (Card c) is summonable by it's summon procedure
bool | Card.IsSSetable(Card c[, bool ignore_field=false]) | Checks whether a card (Card c) can be Set in S/T zone. Setting ignore_field to true makes it not check for free space in the S/T Zone.
bool | Card.IsStatus(Card c, int status) | Checks if "c" has the given status (STATUS_x)
bool | Card.IsSummonable(Card c, bool ignore_count, Effect e\|nil[, int min=0]) | Checks whether a card (Card c) can be Normal Summoned. Setting ignore_count to true makes it ignore the standard once per turn summon limit. If an effect (Effect e) is given, checks whether it can be Normal Summoned by that effect. The last value denotes the minimum tribute amount.
bool | Card.IsSummonableCard(Card c) | Checks if a card (Card c) is normally summonable, returns false when the card is subject of Card.EnableUnsummonable or Card.EnableReviveLimit
bool | Card.IsSummonCode(Card c, Card sc\|nil, int sumtype, int playerid, int ...) | Checks if "c" has a specific code from the "..." list if it is to be used as material for the Summon type "sumtype" of "sc" performed by the player "playerid".
bool | Card.IsSummonLocation(Card c, int loc) | Checks if (Card c) is summoned from location (int loc)
bool | Card.IsSummonPlayer(Card c, int tp) | Checks if (Card c) is summoned by player (int tp)
bool | Card.IsSummonType(Card c, int ...) | Checks if "c" is Summoned by one of the summon types in the "..." list.
bool | Card.IsSynchroSummonable(Card c[, Group\|Card\|nil must_use, Group\|Card\|nil  mg, int min=0, int max=0]) | Checks if "c" can be Synchro Summoned using "must_use" as part of its materials, choosing among "mg", with "min" and "max" materials to be used for the Synchro Summon. How this works is that the script would check for all EFFECT_SPSUMMON_PROC that has SUMMON_TYPE_SYNCHRO as it's Value, then checks the effects' Condition with the provided arguments. Check out "aux.SynCondition" in "proc_synchro.lua" for how this is handled.
bool | Card.IsType(Card c, int type[, Card scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Checks if the card type of "c" is "type" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
bool | Card.IsXyzLevel(Card c, Card xyzc, int lv) | Checks if "c" would be Level "lv" if it was to be used as Xyz Material for "xyzc".
bool | Card.IsXyzSummonable(Card c[, Group\|Card\|nil must_use, Group\|Card\|nil  mg, int min=0, int max=0]) | Checks if "c" can be Xyz Summoned using "must_use" as part of its materials, choosing among "mg", with "min" and "max" materials to be used for the Xyz Summon
void\|int | Card.Level(Card c[, int level]) | Changes (Card c)'s original level if (int level) is inputted, else returns the current card's original level
void\|int | Card.LinkMarker(Card c[, int linkmarker]) | Changes (Card c)'s original Link Markers if (int linkmarker) is inputted, else returns the current card's original Link Markers.
void\|int | Card.Lscale(Card c[, int scale]) | Changes (Card c)'s original right scale if (int scale) is inputted, else returns the current card's original right scale.
bool | Card.MoveAdjacent(card c) | Executes a move operation for card c, to one of its available adjacent sequences (int the Monster Zone)
void\|int | Card.Race(Card c[, int race]) | Changes (Card c)'s original monster type(s)/race(s) if (int race) is inputed, else returns the current card's original monster type(s)/race(s).
void | Card.Recreate(Card c, int code[, int\|nil alias, int\|nil setcode, int\|nil type, int\|nil level, int\|nil attribute, int\|nil race, int\|nil atk, int\|nil def, int\|nil lscale, int\|nil rscale, bool\|nil replace_effect=false]) | Changes (Card c) into a card with (int code) as its original card number from the database. If any of the parameters are included, that stat is also changed. If (bool replace_effect) is set to true, its effect also changes to the effects of (int code).
int | Card.RegisterEffect(Card c, Effect e[, bool forced=false, ...]) | Registers an Effect (Effect e) (usually an Effect created with Effect.CreateEffect()) to a Card (Card c), ... is a list of integers which Registers further effects in the utility.
Effect | Card.RegisterFlagEffect(Card c, int code, int reset_flag, int property, int reset_count[, int label, int desc]) | Registers a flag effect to a card (Card c) with (int code) that resets with (int reset_flag), as the effect code. (int reset_flag).
void | Card.ReleaseEffectRelation(Card c,Effect e) | Releases any relation between a card (Card c) and an effect (Effect e)
void | Card.ReleaseRelation(Card c1, Card c2) | Releases the relation between the first card (Card c1) and the second card (Card c2). Does not release relation from the second card that is resulting from _c2:CreateRelation(c1)_
void | Card.RemoveCounter(Card c, int player, int countertype, int count, int reason) | Remove a number (int count) of the specified counter (int countertype) from a card (Card c), with reason described by (int reason)
bool | Card.RemoveOverlayCard(Card c, int player, int min, int max, int reason) | Makes player (int Player) remove overlay cards from a Card (Card c), with minimum of (int min) and maximum of (int max) with (int reason) as reason
int | Card.ReplaceEffect(Card c, int code, int reset_flag[, int reset_count]) | Temporarily replace all effects of a card (Card c) with the effect of card with the specified card code (int code) that resets according to the ascribed reset flag (int reset_flag)
void | Card.ResetEffect(Card c, int reset_code, int reset_type) | Resets all effects of a Card (Card c) (e.g. "c:ResetEffect(RESET_DISABLE,RESET_EVENT)")
void | Card.ResetFlagEffect(Card c, int code) | Resets a flag with (int code) as the effect code from a card (Card c)
void | Card.ResetNegateEffect(Card c[, int code1,...]) | Reset a card c affected by the effect of cards whose card number is code1, code2 ...
void | Card.ReverseInDeck(Card c) | Reverse a card (Card c) in Deck (make it face-up)
void\|int | Card.Rscale(Card c[, int scale]) | Changes (Card c)'s original left scale if (int scale) is inputted, else returns the current card's original left scale.
void | Card.SetCardTarget(Card c1, Card c2) | Sets the second card (Card c2) as a target of the first card (Card c1)
void\|int | Card.Setcode(Card c[, int setcode]) | Changes (Card c)'s original archetype(s)/setcode(s) if (int setcode) is inputted, else returns the current card's original archetype(s)/setcode(s).
void | Card.SetCounterLimit(Card c, int countertype, int count) | Sets the limit (int count) of how many counter of a type (int countertype) can be held by a card (Card c)
bool | Card.SetFlagEffectLabel(Card c, int code, int label) | Assigns an integer (int label) number to the flag effect attached to a card (Card c) with (int code) as the effect code. Returns true if a flag effect with such code existed and the label was set.
void | Card.SetHint(Card c, int type, int value) | Sets a card (Card c) hint displaying, type is CHINT_* and value is the appropriate value depending on the type
void | Card.SetMaterial(Card c, Card\|Group\|nil materials) | Sets the Material of a Card (Card c) to the passed ones. If nil is passed, the material group of the card is cleared.
void | Card.SetReason(Card c, int reason[, bool keep=false]) | Sets the reason of "c" as "reason". If "keep" is set to true "c" will maintain the previous reason that it had.
void | Card.SetReasonCard(Card c, Card rc) | Sets "rc" as the card that was the reason of an event that happened to "c".
void | Card.SetReasonEffect(Card c, Effect re) | Sets "re" as the effect that was the reason of an event that happened to "c".
void | Card.SetReasonPlayer(Card c, int rp) | Sets "rp" as the player that was the reason of an event that happened to "c".
void | Card.SetSPSummonOnce(Card c, int spsummon_code) | Make a card (Card c) can only be Special Summoned when the turn has not Special Summoned another card with the same code (int code) as its Card.SetSpecialSummonOnce. Basically, makes the "You can only Special Summon "Some Monster" once per turn" condition
void | Card.SetStatus(Card c, int status, bool enable) | Sets the status (STATUS_x) of a Card (Card c) and possibly enables it
void | Card.SetTurnCounter(Card c, int counter) | Sets the turn counter of a Card (Card c) to a value (int count)
void | Card.SetUniqueOnField(Card c, int s, int o, int unique_code[, int unique_location=LOCATION_ONFIELD]) | Sets a card's (Card c) "Can only control 1" clause, int s denotes checking of the would-be owner's field, int o denotes checking the opposing field. unique_location denotes the location the card is unique (setting location outside the field has no meaning)
void\|int | Card.Type(Card c[, int type]) | Changes (Card c)'s original type(s) if (int type) is inputted, else returns the current card's original type(s).
int | Card.UpdateAttack(card c, int amount, int reset, [card rc]) | Applies an ATK change to card c, equal to int amt, with resets defined in int reset. If the reason card rc is not provided, uses as default card c. Returns the ammount of ATK sucessfully changed.
int | Card.UpdateDefense(card c, int amount, int reset, [card rc]) | Applies a DEF change to card c, equal to int amt, with resets defined in int reset. If the reason card rc is not provided, uses as default card c. Returns the ammount of DEF sucessfully changed.
int | Card.UpdateLevel(card c, int amount, int reset, [card rc]) | Applies a level change to card c, equal to int amt, with resets defined in int reset. If the reason card rc is not provided, uses as default card c. Returns the ammount of levels sucessfully changed.
int | Card.UpdateLink(card c, int amount, int reset, [card rc]) | Applies a link change to card c, equal to int amt, with resets defined in int reset. If the reason card rc is not provided, uses as default card c. Returns the ammount of links sucessfully changed.
int | Card.UpdateRank(card c, int amount, int reset, [card rc]) | Applies a rank change to card c, equal to int amt, with resets defined in int reset. If the reason card rc is not provided, uses as default card c. Returns the ammount of ranks sucessfully changed.
int | Card.UpdateScale(card c, int amount, int reset, [card rc]) | Applies a scale change to card c, equal to int amt, with resets defined in int reset. If the reason card rc is not provided, uses as default card c. Returns the ammount of scales sucessfully changed.
