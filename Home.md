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

### Auxiliary Functions
Return type | Function |Description
-- | -- | --
effect | aux.AddContinuousSkillProcedure(c,coverNum, drawless,flip) | Procedure for continuous Spell/Trap Skill-- c: the card (card)-- coverNum: the Number of the cover (int)-- drawless: if the player draw 1 less card at the start of the duel (bool)-- flip: if the continuous card get flipped at the start of the duel (bool)
void | aux.AddEquipProcedure(Card c, int|nil p, function|nil f, function|nil eqlimit, function|nil cost, function|nil tg, function|nil op, function|nil con) | Adds the Equip Card Activation where (int p) is the player, setting 0 will limit to monsters you control, setting to 1 will be your opponent and PLAYER_ALL/nil will be for either player. (function f) is the filters on which monsters you can equip it to. (function eqlimit) if provided will that limitation on which monsters you can only equip it (e.g. Those that can only be equipped by this activation, e.g. Train Connection). (function cost) would be the cost to activate it. (function tg) are effects that applied to it after targeting the monster to equip, and also checking requirements. (function op) is any operation that is applied after the Equip Proc equips. (function con) returns a bool which are conditions that need to be fulfilled for the Equip Card to be activated.
void | aux.AddEREquipLimit(Card c, function|nil con, function|nil equipval, function equipop, Effect linkedeff, int|nil prop, int|nil resetflag, int|nil resetcount) | Registers effects that need to be checked for the effect of "Millennium-Eyes Illusionist". (function con) is any conditions that need to be fulfilled in order to apply its "equipping" effect. (function equipval) is the filter of valid monsters you can equip to it. (function equipop) is the equipping by its effect. (Effect linkedeff) is the effect that equips. (int prop) is the list of additional properties for SetProperty to register effects. (int resetflag) and (int resetcount) is used if the effect would reset such as, until only the End Phase.
effect | aux.AddFieldSkillProcedure(card c, coverNum, drawless) | Procedure for Field skills--c: the skill (card)--coverNum: the cover corresponding to the back (int)--drawless: if the skill make you draw 1 less card at the start of the duel (bool)
effect, effect | aux.AddKaijuProcedure(card c) | Adds Kaiju's stardand procedure to the monster (which also includes the uniqueness on field condition). Calls the following auxilary function: KaijuCondition
effect | aux.AddLavaProcedure(card c, int required, int position, funtion filter, int value, int description) | Adds Lava Golem-like procedure (monster that tribute to Special Summon on opponent's field), int required is the amount of monster to tribute, position is which position is it summoned and filter specify the monster it must tribute, value sets the type of Special summon and description adds a description for it. Calls the following auxiliary functions: LavaCondition, LavaCheck, LavaTarget and LavOperation, defined in cards_specific_functions.lua.
function | aux.AddMaleficSummonProcedure(c,code,loc,excond) | Procedure for "Malefic" monsters' Special Summon (also includes handling of "Malefic Paradox Gear"'s effect)
effect | aux.AddNormalSetProcedure(card c, bool ns, bool opt, int min, int max, int sum_type_val, string desc, function f, function sumop) |  
effect | aux.AddNormalSummonProcedure(card c, bool ns, bool opt, int min, int max, int sum_type_val, string desc, function f, function sumop) |
void | aux.AddPersistentProcedure(Card c, int|nil p, function|nil f, int|nil category, int|nil property, int|nil hint1, int|nil hint2, function|nil con, function|nil cost, function|nil tg, function|nil op, bool|nil anypos) | Adds the Persistent Trap Procedure where is the player, setting 0 will limit to monsters you control, setting to 1 will be your opponent and PLAYER_ALL/nil will be for either player. (function f) is the filters on which monsters you can target. (bool anypos) is a check if the target needs to be face-up. Setting this to true will allow it to be targeted even if it isn't face-up.
effect | aux.AddPreDrawSkillProcedure(c, coverNum, drawless, skillcon, skillop, countlimit) | Function for the skills that "trigger" at the start of the turn/Before the Draw-- c: the card (card)-- coverNum: the Number of the cover (int)-- drawless: if the player draw 1 less card at the start of the duel (bool)-- flip con: condition to activate the skill (function)-- flipOp: operation related to the skill activation (function)
effect | aux.AddSkillProcedure(c, coverNum, drawless, skillcon, skillop, countlimit) | Procedure for basic skill-- c: the card (card)-- coverNum: the Number of the cover (int)-- drawless: if the player draw 1 less card at the start of the duel (bool)-- flip con: condition to activate the skill (function)-- flipOp: operation related to the skill activation (function)
void | aux.AddUnionProcedure(Card c, function f, bool oldrule, bool oldprotect) | Adds the Union Procedure to (Card c) where (function f) is the cards you can equip the Union monster to, and (bool oldrule) is a check to apply old rulings of the Union monster. if oldprotect is not nil, uses old rules for destroy replacement (If the equipped monster would be destroyed, destroy this card instead.)
void | aux.AddValuesReset(resetfunc) |  
effect | aux.AddVrainsSkillProcedure(c, skillcon, skillop, efftype) | Procedure for Vrains Skills--flip con: condition to activate the skill (function)--flipOp: operation related to the skill activation (function)--efftype: Event to trigger the Skill, default to EVENT_FREE_CHAIN. Additionally accept EFFECT_NEGATE_SKILL for Anti Skill (int)
bool | aux.AND(...)(...) | First (...) is a list of functions which will be used to check the parameters in the second set of (...), separated with "and". The second set of (...) is applied automatically when used as a filter.
int | aux.AnnounceAnotherAttribute(group g, int player) | Makes (int player) announce an attribute different from the one(s) already among the members of (group g)
int | aux.AnnounceAnotherRace(group g, int player) | Makes (int player) announce a monster type (Race) different from the one(s) already among the members of (group g)
int | aux.AskAny(stringid) |  
int | aux.AskEveryone(stringid) |  
bool | aux.bdcon(Effect e, int tp, Group eg|nil, int ep, int ev, Effect re, int r, int rp) | Default condition of EVENT_BATTLE_DESTROYING. "When this card destroys a monster by battle" and checks if itself is still the same state after battle.
bool | aux.bdgcon(Effect e, int tp, Group eg|nil, int ep, int ev, Effect re, int r, int rp) | Condition of EVENT_BATTLE_DESTROYING. "When this card destroys a monster by battle and sends it to the Graveyard" and checks if itself is still the same state after battle.
bool | aux.bdocon(Effect e, int tp, Group eg|nil, int ep, int ev, Effect re, int r, int rp) | Condition of EVENT_BATTLE_DESTROYING. "When this card destroys an opponent's monster by battle" and checks if itself is still the same state after battle.
bool | aux.bdogcon(Effect e, int tp, Group eg\|nil, int ep, int ev, Effect re, int r, int rp) | Condition of EVENT_BATTLE_DESTROYING. "When this card destroys an opponent's monster by battle and sends it to the Graveyard" and checks if itself is still the same state after battle.
void | aux.BeginPuzzle() | Sets up the beginning of a puzzle, causing the player to lose during the End Phase
bool | aux.bfgcost(Effect e, int tp, Group|nil eg, int ep, int ev, Effect re, int r, int rp, int chk) | Default SetCost for "You can banish this card from your Graveyard"
table | aux.BitSplit(int number) | Auxiliary function to help printing hints for attribute-related cards such as Cynet Codec
void | aux.CallToken(int code) | Function is used mostly for Anime Cards calling 419/420 to enable more functions. Also used in Anime Numbers with alias to prevent errors made by alias.
bool | aux.CanActivateSkill(int player) |  

Return type | Function |Description
-- | -- | --
int | aux.cannotmatfilter(int val1, [int ...]) | Return the value(s) passed formated to be used for EFFECT_CANNOT_BE_MATERIAL.
bool | aux.CanPlaceCounter(card c,int counter_type) | Checks whether card c has an effect that places int counter_type counters (on itself or others). Corresponding table: "s.counter_place_list".
void | aux.chainreg(Effect e, int tp, Group eg|nil, int ep, int ev, Effect re, int r, int rp) | Flag effect used for Spell Counter (that are put when the Spell card resolves)
int | aux.ChangeBattleDamage(int player, int value) | Changes the battle damage that (int player) would have taken to (int value)
bool | aux.CheckPendulumZones(int player) | Returns if (int player) has at least one Pendulum zone free, using Duel.CheckLocation.
bool | aux.CheckUnionEquip(Card uc, Card tc) | A check if you can equip a Union monster (Card uc) to (Card tc).
bool | aux.CheckUnionEquip(uc,tc) | See proc_union.lua.
bool | aux.CheckValidExtra(card c, int player, group sg, group mg, lc, group emt, function filt) |  
bool | aux.CheckZonesReleaseSummonCheck(group must, group oneof, function checkfunc) | Auxiliary function called by "Duel.SelectReleaseGroupSummon".
bool | aux.CheckZonesReleaseSummonCheckSelection(group must, group oneof, function checkfunc) |  
bool | aux.ChkfMMZ(int sumcount)(Group sg, Effect e, int tp, Group mg) | "Check for Main Monster Zones". Used in rescon by default. 2nd parenthesis is not required as rescon/cancelcon in aux.SelectUnselectGroup. (Group sg) is the selected group when using aux.SelectUnselectGroup. Evaluates if a int sumcount number of Main Monsters zones are available and/or will be made available to summon the requiring card.
int | aux.ComposeNumberDigitByDigit(int tp, int min, int max) | (int tp) declares a number by digit with a minimum of (int min) and maximum of (int max)
function | aux.CostWithReplace(function base, int replacecode, function extracon, function alwaysexecute) |  
bool | aux.damcon1(Effect e, int tp, Group eg|nil, int ep, int ev, Effect re, int r, int rp) | Default condition for "If you would take effect damage"
void | aux.DeleteExtraMaterialGroups(group emt) |  
bool | aux.disfilter1(Card c) | Checks if (Card c) can be negated (for monsters)
bool | aux.disfilter2(Card c) | Checks if (Card c) can be negated (for Spell/Trap)
bool | aux.disfilter3(Card c) | Checks if (Card c) can be negated (return aux.disfilter1 OR aux.disfilter2)
function | aux.dncheck | Checks for cards with different names (usually be used with aux.SelectUnselectGroup)
bool | aux.dogcon(Effect e, int tp, Group eg\|nil, int ep, int ev, Effect re, int r, int rp) | SetCondition for "is destroyed by your opponent".
void | aux.DoubleSnareValidity(card c, int range, int property) | Registers that card c has an effect that can negate/destroy trap cards, while it is in the location defined in int range. Used by Double Snare to identify which cards it can destroy. Int property are additional properties other than the default EFFECT_FLAG_CANNOT_DISABLE\|EFFECT_FLAG_SINGLE_RANGE.

Return type | Function |Description
-- | -- | --
bool | aux.dpcheck(function f) | Checks for cards with different properties (the property defined in function f, for example, Card.GetLevel, GetAttribute, GetRace, GetCode, etc). Usually used with aux.SelectUnselectGroup.
function | aux.dxmcostgen(int min, int max, [function op]) | "Detach Xyz Material Cost Generator". Generates a function to be used by Effect.SetCost in order to detach a number of Xyz Materials from the Effect's handler. (int min) is the minimum number of materials to check for detachment. (int max) is the maximum number of materials to detach or a function that gets called as if by doing max(e,tp) in order to get the value of max detachments. (function op) is an optional function that gets called by passing the effect and the operated group of just detached materials in order to do some additional handling with them.
void | aux.EnableCheckReincarnation(Card c) | Auxiliary function for "Salamangreat" Reincarnation procedure. Enables reincarnation links.
void | aux.EnableExtraRules(c, card, init, ...) | Functions to automate consistent start-of-duel activations for Duel Modes like Speed Duel, Sealed Duel, etc
void | aux.EnableExtraRulesOperation(card,init,...) |  
void | aux.EnableGeminiAttribute(Card c) | Applies all the effects necessary for a Gemini monster to be used as one to (Card c).
void | aux.EnableNeosReturn(Card c[, int extracat, function extrainfo, function extraop]) | Adds the effect to shuffle the card into the Extra Deck at the End Phase (most commonly used by "Neos" Fusion Monsters). If provided, "extracat", "extrainfo" and "extraop" will add additional effect categories, operation info and operations respectively to the effect. The Condition, Target and Operation functions of this effect, named NeosReturnCondition1/2, NeosReturnTarget and NeosReturnOperation, are detailed in cards_specific_functions.lua.
void | aux.EnableSpiritReturn(Card c, int event1, int ...) | Sets up EVENT triggers to (Card c) so it returns to the hand during that End Phase, requires a minimum of 1 (int event1)
bool | aux.EquipByEffectAndLimitRegister(Card c, Effect e) |  
bool | aux.EquipByEffectLimit(Card c, Effect e, int tp, Card tc, int|nil code, bool mustbefaceup) | Equips (Card tc) to (Card c). Adding a (int code) will register that code as flag effect to the equipped card  (bool mustbefaceup) defines if the card to be equipped is required to be face-up.
void | aux.EquipEquip(Effect e, int tp, Group eg, int ep, int ev, Effect re, int r, int rp) | Used to equip the Equip Card to the targeted monster. This would be used if you cannot use the Equip Procedure for your Equip Card activation.
int | aux.EvilHeroLimit(e, se, sp, st) | Default SetValue for "Evil HERO" monsters's effect EFFECT_SPSUMMON_CONDITION. Must be used due to the existance of "Supreme King Castle"
bool | aux.evospcon(Effect e, int tp, Group eg|nil, int ep, int ev, Effect re, int r, int rp) | Default SetCondition for "Summoned by a "Evolsaur" monster"
bool | aux.exccon(Effect e) | SetCondition for "except the turn this card was sent to the Graveyard".
bool | aux.FALSE() | Function that returns false
bool | aux.FieldSummonProcTg(function f1, function f2) |  
bool | aux.FilterBoolFunction(function f, ...) | Used in filters (with parameter (Card c)) to check a function and its (...) parameters
bool | aux.FilterBoolFunctionEx(function f, int value) | Used filter for the Fusion, Xyz, Synchro and Link Procedures where (function f) can be Card.IsRace, Card.IsAttribute and Card.IsType and (int value) corresponds to the required Race, Attribute and Type.
bool | aux.FilterBoolFunctionEx2(function f, ...) |  
bool | aux.FilterEqualFunction(function f, int value, ...) | Used in filters (with parameter (Card c)) to check a function and its (...) parameters is equal to the inputted (int value).
function | aux.FilterFaceupFunction(function f, ...) | Filter to check face-up cards that match (function f) where (...) are extra parameters to f. Can be used as the function parameter in SelectMatchingCard/Target and IsExistingMatchingCard/Target.
bool | aux.FilterSummonCode(...) | used for Material Types Filter Bool (works for IsRace, IsAttribute, IsType)
function | aux.FunctionWithNamedArgs(function f, ...) |  
bool | aux.fuslimit(Effect e, Effect se, int sp, int st) | SPSUMMON condition "Must be Fusion Summoned"
bool | aux.gbspcon(Effect e, int tp, Group eg|nil, int ep, int ev, Effect re, int r, int rp) | Default SetCondition for "Summoned by a "Gladiator Beast" monster"
bool | aux.GeminiNormalCondition(Effect e) | Checks if a monster is face-up and is not a Gemini monster or has not been Normal Summoned on the field.
table | aux.GetAttributeStrings(int number) |  
int | aux.GetCover(card c, coverNum) | Used by the Skill procedure.
table,group | aux.GetExtraMaterials(int player, group mustg, group sc, int summon_type) |  
group | aux.GetMustBeMaterialGroup(int player, group eg, group sump, sc, group g, int r) |  
Group | aux.GetMustBeMaterialGroup(int tp, nil|Group eg, int sump, nil|Card sc, nil|Group g, int r) | Gets the group that must be used as material (Contacting "C"). (int tp) is the affected player, (nil|Group eg) is all detected materials, (int sump) is the Summoning player, (nil|Card sc) is the card to be Summoned, (nil|Group) g is all the valid usable materials, (int r) is the reason e.g. REASON_SYNCHRO, REASON_XYZ


Return type | Function |Description
-- | -- | --
bool | aux.dpcheck(function f) | Checks for cards with different properties (the property defined in function f, for example, Card.GetLevel, GetAttribute, GetRace, GetCode, etc). Usually used with aux.SelectUnselectGroup.
function | aux.dxmcostgen(int min, int max, [function op]) | "Detach Xyz Material Cost Generator". Generates a function to be used by Effect.SetCost in order to detach a number of Xyz Materials from the Effect's handler. (int min) is the minimum number of materials to check for detachment. (int max) is the maximum number of materials to detach or a function that gets called as if by doing max(e,tp) in order to get the value of max detachments. (function op) is an optional function that gets called by passing the effect and the operated group of just detached materials in order to do some additional handling with them.
void | aux.EnableCheckReincarnation(Card c) | Auxiliary function for "Salamangreat" Reincarnation procedure. Enables reincarnation links.
void | aux.EnableExtraRules(c,card,init,...) | Functions to automate consistent start-of-duel activations for Duel Modes like Speed Duel, Sealed Duel, etc
void | aux.EnableExtraRulesOperation(card,init,...) |  
void | aux.EnableGeminiAttribute(Card c) | Applies all the effects necessary for a Gemini monster to be used as one to (Card c).
void | aux.EnableNeosReturn(Card c[, int extracat, function extrainfo, function extraop]) | Adds the effect to shuffle the card into the Extra Deck at the End Phase (most commonly used by "Neos" Fusion Monsters). If provided, "extracat", "extrainfo" and "extraop" will add additional effect categories, operation info and operations respectively to the effect. The Condition, Target and Operation functions of this effect, named NeosReturnCondition1/2, NeosReturnTarget and NeosReturnOperation, are detailed in cards_specific_functions.lua.
void | aux.EnableSpiritReturn(Card c, int event1, int ...) | Sets up EVENT triggers to (Card c) so it returns to the hand during that End Phase, requires a minimum of 1 (int event1)
bool | aux.EquipByEffectAndLimitRegister(Card c, Effect e) |  
bool | aux.EquipByEffectLimit(Card c, Effect e, int tp, Card tc, int\|nil code, bool mustbefaceup) | Equips (Card tc) to (Card c). Adding a (int code) will register that code as flag effect to the equipped card  (bool mustbefaceup) defines if the card to be equipped is required to be face-up.
void | aux.EquipEquip(Effect e, int tp, Group eg, int ep, int ev, Effect re, int r, int rp) | Used to equip the Equip Card to the targeted monster. This would be used if you cannot use the Equip Procedure for your Equip Card activation.
int | aux.EvilHeroLimit(e,se,sp,st) | Default SetValue for "Evil HERO" monsters's effect EFFECT_SPSUMMON_CONDITION. Must be used due to the existance of "Supreme King Castle"
bool | aux.evospcon(Effect e, int tp, Group eg\|nil, int ep, int ev, Effect re, int r, int rp) | Default SetCondition for "Summoned by a "Evolsaur" monster"
bool | aux.exccon(Effect e) | SetCondition for "except the turn this card was sent to the Graveyard".
bool | aux.FALSE() | Function that returns false
bool | aux.FieldSummonProcTg(function f1, function f2) |  
bool | aux.FilterBoolFunction(function f, ...) | Used in filters (with parameter (Card c)) to check a function and its (...) parameters
bool | aux.FilterBoolFunctionEx(function f, int value) | Used filter for the Fusion, Xyz, Synchro and Link Procedures where (function f) can be Card.IsRace, Card.IsAttribute and Card.IsType and (int value) corresponds to the required Race, Attribute and Type.
bool | aux.FilterBoolFunctionEx2(function f, ...) | 


Return type | Function |Description
-- | -- | --
bool | aux.FilterEqualFunction(function f, int value, ...) | Used in filters (with parameter (Card c)) to check a function and its (...) parameters is equal to the inputted (int value).
function | aux.FilterFaceupFunction(function f, ...) | Filter to check face-up cards that match (function f) where (...) are extra parameters to f. Can be used as the function parameter in SelectMatchingCard/Target and IsExistingMatchingCard/Target.
bool | aux.FilterSummonCode(...) | used for Material Types Filter Bool (works for IsRace, IsAttribute, IsType)
function | aux.FunctionWithNamedArgs(function f, ...) |  
bool | aux.fuslimit(Effect e, Effect se, int sp, int st) | SPSUMMON condition "Must be Fusion Summoned"
bool | aux.gbspcon(Effect e, int tp, Group eg\|nil, int ep, int ev, Effect re, int r, int rp) | Default SetCondition for "Summoned by a "Gladiator Beast" monster"
bool | aux.GeminiNormalCondition(Effect e) | Checks if a monster is face-up and is not a Gemini monster or has not been Normal Summoned on the field.
table | aux.GetAttributeStrings(int number) |  
int | aux.GetCover(card c, coverNum) | Used by the Skill procedure.
table,group | aux.GetExtraMaterials(int player, group mustg, group sc, int summon_type) |  
group | aux.GetMustBeMaterialGroup(int player, group eg, group sump, sc, group g, int r) |  
Group | aux.GetMustBeMaterialGroup(int tp, nil\|Group eg, int sump, nil\|Card sc, nil\|Group g, int r) | Gets the group that must be used as material (Contacting "C"). (int tp) is the affected player, (nil\|Group eg) is all detected materials, (int sump) is the Summoning player, (nil\|Card sc) is the card to be Summoned, (nil\|Group) g is all the valid usable materials, (int r) is the reason e.g. REASON_SYNCHRO, REASON_XYZ
table | aux.GetRaceStrings(int number) |  
void | aux.GlobalCheck(s, function func) | Enables a global check to be used with function "func"
bool | aux.HarmonizingMagFilter(c,e,f) |  
bool | aux.HasCounterListed(card c, int counter_type) | Checks whether card c has an effect that mentions int counter_type counter. This includes adding, removing, gaining ATK/DEF per counter, etc. Corresponding table: "s.counter_list" ("s.counter_place_list" is already handled)
bool | aux.HasListedSetCode(Card c, int ...) | Retrurn if (Card c) lists any of the setcodes passed in (int ...), by iterating over Card c's listed_series.
bool | aux.imval1(Effect e, Card c) | default filter for EFFECT_CANNOT_BE_BATTLE_TARGET where (Card c) is checked to ensure it's not immune to (Effect e)
bool | aux.imval2(Effect e, Card c) | similar to aux.imval1, but also check if the monster is from opponent.
bool | aux.indoval(Effect e, Effect re, int rp) | Returns if the reason player is equal to 1-effect e's handler player. Commonly used as filter for EFFECT_INDESTRUCTABLE_EFFECT + opponent

Return type | Function |Description
-- | -- | --
bool | aux.indsval(Effect e, Effect re, int rp) | Returns if the reason player is equal to effect e's handler player. Commonly used as filter for EFFECT_INDESTRUCTABLE_EFFECT + self
bool | aux.IsArchetypeCodeListed(card c, int ...) | Returns if the (Card c) specifically lists the name of a card that is part of an archetype in "...", iterating over Card c's listed_names and checking if those cards belong to any of the archetypes passed.
bool | aux.IsCardTypeListed(Card c, int ...) | Returns true if (Card c) specifically lists any of the card types passed in (int ..), (which means that it iterates over Card c's listed_card_types)
bool | aux.IsCodeListed(Card c, int ...) | Checks if 1 of the codes in (int ...) is a listed card in (Card c)'s text
bool | aux.IsGeminiState(Effect e) | Checks if an effect's handler (corresponding card) is a Gemini monster applying its effect.
bool | aux.IsMaterialListCode(Card c, int ...) | Checks if 1 of the codes in (int ...) is a listed Fusion Material in (Card c)
bool | aux.IsMaterialListSetCard(Card c, int ...) | Checks if 1 of the setcodes in (int ...) is a listed archetype in a material of (Card c)
bool | aux.IsNotGeminiState(Effect e) | returns not aux.IsGeminiState(Effect e)
bool | aux.IsUnionState(Effect effect) | Used as a default condition to check if the handler of the effect is a Union monster equipped to another monster.
bool | aux.IsZone(card c, int zone, int tp) | Returns if (card c) is in the (int zone), (int tp) is the reference player.
bool | aux.KaijuCondition(e,c) | See cards_specific_functions.lua
bool | aux.LavaCheck(sg,e,tp,mg) | See cards_specific_functions.lua
bool | aux.LavaCondition(required, filter) | See cards_specific_functions.lua
void | aux.LavaOperation(required, filter) | See cards_specific_functions.lua
bool | aux.LavaTarget(required, filter) | See cards_specific_functions.lua
bool | aux.lnklimit(Effect e, Effect se, int sp, int st) | SPSUMMON condition "Must be Link Summoned"
int | aux.MainAndExtraGetSummonZones(card c, int mmz, int emz, effect e, int sumtype, int sump, int targetp, bool nocheck, bool nolimit, int pos, nc, ...) |  
bool, Group | aux.MainAndExtraSpSummonLoop(function\|nil func, int sumtype, int sump, int targetp, bool nocheck, bool nolimit, int pos, int mmz, int emz)(Effect e, int tp, Group eg, int ep,int ev, Effect re, int r, int rp, Group sg) | Loops Special Summoning (Group sg) to ensure they go in a valid zone (Extra Moster Zone and Main Monster Zones) where (function func) is a function called after each card in the Group is summoned with the parameters (Effect e, int tp, Group eg, int ep,int ev, Effect re, int r, int rp, Card sc) where (Card sc) is the card that's Summoned. (int sumtype) is the Summon Type. (int sump) is the Summoning player. (int targetp) is the target player. (bool nocheck) checks for "ignoring the Summoning conditions". And (bool nolimit) checks for "ignoring proper Summon". (int pos) is the position to be Summoned. (int mmz) is the zones where you can Special Summon monsters in (Group sg) to the Main Monster Zone, which defaults to all Main Monster Zones if there is no input or nil is inputed. (int emz) on the other is similar to (int mmz) excepts it checks for cards from the Extra Deck which Special Summons to the Extra Monster Zone.
bool | aux.MainAndExtraZoneCheckBool(card c, int mmz, int emz, effect e, int sumtype, int sump, int targetp, bool nocheck, bool nolimit, int pos, nc, ...) |  


Return type | Function |Description
-- | -- | --
function | aux.MaleficSummonCondition(cd, int loc, function excon) | Auxiliary function for the summoning procedure of "Malefic" monsters. Checks if the player has the zone to summon and the appropriate monster (cd) to banish.
function | aux.MaleficSummonFilter(c,cd) | Filter used with AddMaleficSummonProcedure. Returns if card (Card c)'s ID is (cd) and if c can be banished as cost
function | aux.MaleficSummonOperation(cd, int loc) | Auxiliary function to handle the summoning procedure of "Malefic" monsters. Performs the actual summon of the monster by removing the appropriate monster.
function | aux.MaleficSummonSubstitute(card c, card cd, int tp) | Used with the Summoning Procedure of "Malefic" monsters. Checks for the effect of "Malefic Paradox Gear"
function | aux.MaleficUniqueFilter(cc) | Used as filter for the uniqueness on field with the "Malefic" monsters
bool | aux.MZFilter(Card c, int tp) | Filter to check monsters if it's on a Main Monster Zone
bool | aux.NecroValleyFilter(function f)(Card target, ...) | Filter check "not affected by Necrovalley" in addition to its own filter, if used as function filter, (Card target, ...) is defined by default
bool | aux.NeosReturnSubstituteFilter(Card c) | Auxiliary filter used by NeosReturnOperation. Returns if Card c can be removed as cost and is Neos Fusion
iterator | aux.Next(Group g) | Iterates over the cards in (Group g) for use with for loops
bool | aux.NOT(function f)(...) | This is equivalent to not f(...), if used as filter checking, (...) is automatically applied
nil | aux.NULL() | Function that returns nil
bool | aux.NumeronDetachCost(int min[, int max=min]) | Auxiliary function to handle evaluate and execute detach costs for "Numeron" Xyz monsters that ignore costs due to the effect of "Numeron Network". Checks if player is affected by CARD_NUMERON_NETWORK, in which case it applies its effect. Otherwise, checks if the card using the function can detach a "min" number of materials to detach and then detaches up to "max" materials.
bool | aux.nvfilter(Card c) | Filter check "not affected by Necrovalley"
bool | aux.nzatk(Card c) | Filter checking if (Card c) is face-up and has more than 0 ATK
bool | aux.nzdef(Card c) | Filter checking if (Card c) is face-up and has more than 0 DEF
bool | aux.OR(...)(...) | First (...) is a list of functions which will be used to check the parameters in the second set of (...), separated with "or". The second set of (...) is applied automatically when used as a filter.
table element | aux.ParamsFromTable(table t, key, ...) |  
bool | aux.penlimit(Effect e, Effect se, int sp, int st) | SPSUMMON condition "Must be Pendulum Summoned"
bool | aux.PersistentTargetFilter(Effect e, Card c) | Default filter for checking if it's targeted by the Persistent Trap.
bool | aux.PlayFieldSpell(Card c,e,tp,eg,ep,ev,re,r,rp,target_p) | Activates a field spell Card "c". Already handles interactions with Field Spells that are already face up, rules for only 1 Field Spell at time, checks for costs and activated effects of the field spell and als the interaction with Ancient Pixie Dragon.
bool | aux.ProcCancellable | Used with the Xyz Summon procedure and a fw Xyz monsters. Defined as false.

Return type | Function |Description
-- | -- | --
table | aux.PropertyTableFilter(function f, ...) |  
void | aux.PuzzleOp(Effect e, int tp) | Used by aux.BeginPuzzle(), sets the first turn player's LP to 0
bool | aux.qlifilter(Effect e, Effect te) | Default filter used with "Qli" monsters for: "Unaffected by activated monster effects whose original Rank/Level is lower than this card's Level"
void | aux.RegisterClientHint(Card c, int property_code, int reg.player, int s, int o, str, int reset_code, int ct) | Auxiliary function to simplify registering EFFECT_FLAG_CLIENT_HINT to players. (Card c) is card that creates the hint message,  (int property_code) are additional properties like EFFECT_FLAG_OATH (PLAYER_TARGET and CLIENT_HINT are the flags registered by default). (int reg. player) is the player that is registering the hint, to himself (int s) and/or the opponent (int o), with a description called from a string defined in (str). Additional resets, other than the default RESET_PHASE+PHASE_END, can be passed in (int reset_code) and its reset count (int ct).
bool | aux.ReincarnationCheckTarget(Effect e, Card c) | Auxiliary function for "Salamangreat" Reincarnation procedure. Returns if (card c) is either a Fusion, Ritual or a Link.
function | aux.ReincarnationCheckValue(Effect e, Card c) | Auxiliary function for "Salamangreat" Reincarnation procedure. Registers CARD_SALAMANGREAT_SANCTUARY as flag  to (card c) if it is either a Link, Fusion or Ritual and has among its materials a card with the same ID as (card c).
bool | aux.ReincarnationRitualFilter(Effect e, Card c) | Auxiliary filter for "Salamangreat" Reincarnation procedure to handle the rituals.
bool | aux.RelCheckGoal(int player, group sg, group exg, group mustg, int count, int min, function specialchk, ...) |  
bool | aux.RelCheckRecursive(card c, int player, group sg, group mg, group exg, group mustg, int count, int min, function specialchk, ...) |  
bool | aux.ReleaseCheckMMZ(group sg, int player) |  
bool | aux.ReleaseCheckSingleUse(group sg, int player, group exg) |  
bool | aux.ReleaseCheckTarget(group sg, int player, group exg, group dg) |  
bool | aux.ReleaseCostFilter(card c, function f,...) |  
bool | aux.ReleaseNonSumCheck(card c, int player, effect e) | Auxiliary function called by "Duel.CheckReleaseGroupSummon" and Duel.SelectReleaseGroupSummon".
bool\|void | aux.RemainFieldCost(Effect e, int tp, Group\|nil eg, int ep, int ev, Effect re, int r, int rp, int chk) | Costs that is used in cards that stay on the field if they finish resolving. (e.g. Kunai with Chain, Different Dimension Burial)
void | aux.RemainFieldDisabled(Effect e, int tp, Group\|nil eg, int ep, int ev, Effect re, int r, int rp) |  
void | aux.ResetEffects(Group g, int eff) | Resets all effects with code (int eff) in a group of cards defined (Group g).
bool | aux.ritlimit(Effect e, Effect se, int sp, int st) | SPSUMMON condition "Must be Ritual Summoned"
int/nil | aux.SelectEffect(int player, ..) | Makes player (int player) select 1 option among possible effects. The ellipsis (...) allows tables in the form {bool condition, int stringid}. The function then makes the player select an effect, displaying the strings whose conditons are true, returning the index of the choosen element or nil.
bool\|Group | aux.SelectUnselectGroup(Group g, Effect e, int tp, int minc = 1, int maxc = 99, function\|nil rescon, int chk, int seltp, int hintmsg, function\|nil cancelcon, function\|nil breakcon, bool cancelable) | Recursion checking and selection. (Group g) is the group to check and choose from, with a minimum (int minc) that defaults to 1 if set to nil and maximum (int maxc) that defaults to 99 if set to nil. (function rescon) is the condition to check which is needed fulfill. (int chk) is set to 0 to check and 1 to select. (int seltp) is the selecting player. (int hintmsg) is the HINTMSG that will be displayed on selection. (function cancelcon) is the condition when fulfilled allows you to end selection. (function breakcon) when fulfilled ends the selection automatically.
function | aux.seqmovcon(e,tp,eg,ep,ev,re,r,rp) | Condition for effects that make the monster change its current sequence/column.
function | aux.seqmovop(e,tp,eg,ep,ev,re,r,rp) | Operation for effects that make the monster change its current sequence/column.

Return type | Function |Description
-- | -- | --
effect | aux.SetSkillOp(coverNum, drawless, skillcon, skillop, countlimit, efftype) |  
void | aux.SetUnionState(card c) | See proc_union.lua.
bool | aux.SpElimFilter(Card c, bool mustbefaceup, bool includemzone) | Spirit Elimination check to (Card c). It checks if controller is affected by Spirit Elimination. If so, it will only filter in the Monster Zone, otherwise in Graveyard. (bool mustbefaceup) means the filter is not generic (e.g. Banish 1 Dragon-Type monster) opposed to banish 1 monster. (bool includemzone) when set to true will check LOCATION_MZONE by default as opposed to filtering LOCATION_MZONE and LOCATION_GRAVE depending on affected by Spirit Elimination.
bool | aux.SpiritReturnCondition(e, tp, eg, ep, ev, re, r, rp) | Auxiliary condition. Not used directly by cards, only called by SpiritReturnReg
void | aux.SpiritReturnOperation(e, tp, eg, ep, ev, re, r, rp) | Auxiliary operation. Not directed used by cards.
void | aux.SpiritReturnReg(e, tp, eg, ep, ev, re, r, rp) | Auxiliary function registration. Not used directly by card, only called by aux.EnableSpiritReturn
void | aux.SpiritReturnTarget(e, tp, eg, ep, ev, re, r, rp, chk) | Auxiliary target. Not directed used by cards.
int | aux.Stringid(int code, int n) | Returns the description code using the database entry's code (int code) and from the nth position (int position) which can be 0-15 corresponding to the str in the database which are from str1 to str16
bool | aux.sumlimit(int sumtype) | helper function called by the various auxiliary function used as special summon conditions
void | aux.sumreg(Effect e, int tp, Group eg, int ep, int ev, Effect re, int r, int rp) | Used as SetOperation which registers a FlagEffect to cards in the event group with the same OriginalCode as itself
bool | aux.synlimit(Effect e, Effect se, int sp, int st) | SPSUMMON condition "Must be Synchro Summoned"
table | aux.tableAND(...) |  
table | aux.tableOR(...) |  
bool | aux.TargetBoolFunction(function f, ...) | Used in SetTarget filters (with parameters (e,c)) to check a function and its (...) parameters
bool | aux.TargetEqualFunction(function f, int value, ...) | Used in SetTarget filters (with parameters (e,c)) to check a function and its (...) parameters is equal to the inputted (int value).
bool | aux.TatsunecroFilter(Card c) | Returns is Card c has "3096468" as flag effect. Used in the Synchro summon procedure
bool | aux.tgoval(Effect e, Effect re, int rp) | filter for EFFECT_CANNOT_BE_EFFECT_TARGET, "cannot be targeted by your opponent's card effects"
void | aux.thoeSend(card c) | Sends (card c) to the grave. Function added to be used with aux.ToHandOrElse
void | aux.ToHandOrElse(card c\|group tc, int player, [function check, function oper, str],...) | Makes (int player) either add (card c\|group tg) to hand or perform a secondary action. If the optional parameters are not provided, the default secondary action is to send the card or group to the GY. If  the provided (function check) is true (for all the cards in the group) , the secondary action, with string called from (str), will be the one defined in (function oper).
bool | aux.TRUE() | Function that returns true. Can be used to return a whole group of cards in a certain location
void | aux.ValuesReset() |  
void | aux.WitchcrafterDiscardCost(f, int minc, int maxc) | Auxiliary function for the discard cost of "Witchcrafter" monsters. Performs the actual discard part, considering a minimum (minc) and maximum (maxc) amount of cards to discard. It also handles cards with EFFECT_WITCHCRAFTER_REPLACE, setting the reason for REASON_COST for those, or REASON_COST+REASON_DISCARD if a card is sent from hand instead.
bool | aux.WitchcrafterDiscardFilter(c) | Auxiliary function for the discard cost of "Witchcrafter" monsters. Returns if (Card c) can be either sent to the GY as a cost or has EFFECT_WITCHCRAFT_REPLACE.
bool | aux.WitchcrafterDiscardGroup(minc) | Auxiliary function for the discard cost of "Witchcrafter" monsters. Returns if there is a card with EFFECT_WITCHCRAFTER_REPLACE, that can be used as the whole cost, of if there is a (minc) number of cards to use as cost,  minc is the ammount the effect requires to discard.
bool | aux.xyzlimit(Effect e, Effect se, int sp, int st) | SPSUMMON condition "Must be Xyz Summoned"
int | aux.ZoneCheckFunc(card c, int player, int zone) | Auxiliary function called by "Duel.CheckReleaseGroupSummon" and Duel.SelectReleaseGroupSummon".
bool | aux.zptcon(function filter) | Used as condition for effects that check "if a [filter] monster is Special Summoned to a zone this card points to". Includes non-trivial handling of self-destructing Burning Abyss monsters. tp is passed to check control.
bool | aux.zptfilter(function filter) | Used as filter for effects that check "if [filter] monster is Special Summoned to a zone this card points to". Also includes non-trivial handling of self-destructing effects of "Burning Abyss" monsters.
group | aux.zptgroup(group eg, function filter, card c, int tp) | Filter for "If a (function filter) monster is Special Summoned to a zone this card points to". Includes non-trivial handling of self-destructing Burning Abyss monsters
bool | aux.zptgroupcon(group eg, function filter, card c, int tp) |  
bool | aux.CheckSkillNegation(e, tp) | Function to check whether the Skill would be negated by Anti Skill
bool | aux.NeosReturnCondition1(e, tp, eg, ep, ev, re, r, rp) | See cards_specific_functions.lua.
bool | aux.NeosReturnCondition2(e, tp, eg, ep, ev, re, r, rp) | See cards_specific_functions.lua.
void | aux.NeosReturnOperation(c, extraop) | See cards_specific_functions.lua.
void | aux.NeosReturnTarget(c, extrainfo) | See cards_specific_functions.lua.

### bit functions
Return type | Function |Description
-- | -- | --
int | bit.band(int a, int b) | Does a bitwise AND operation between 2 integers. (Deprecated, advised to use (int a)&(int b) instead.)
int | bit.bnot(int a) | Swaps the bits of an integer, 0 to 1 and 1 to 0. (Deprecated, advised to use ~(int a) instead.)
int | bit.bor(int a, int b) | Does a bitwise OR operation between 2 integers. (Deprecated, advised to use (int a)\|(int b) instead.)
int | bit.bxor(int a, int b) | Does a bitwise XOR operation between 2 integers. (Deprecated, advised to use (int a)~(int b) instead.)
int | bit.extract(int a, int b[, int width=1]) | Returns the field of (int a) with a width
int | bit.lshift(int a, int b) | Shifts all bits of an integer to the left by an amount (Deprecated, advised to use (int a)<<(int b) instead.)
int | bit.replace(int a, int b, int c[, int width=1]) | Returns a copy of (int a) with the field with a width changed to value (int b)
int | bit.rshift(int a, int b) | Shift all bits of an integer to the right by an amount (Deprecated, advised to use (int a)>>(int b) instead.)

### Card functions

Return type | Function |Description
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

Return type | Function |Description
-- | -- | --
Effect[, Group, int, int, Effect, int, int] | Card.CheckActivateEffect(Card c, bool neglect_con, bool neglect_cost, bool copy_info) | Checks a card (Card c)'s EFFECT_TYPE_ACTIVATE effect while checking for whether it can be activated. Returns _nil_ if effect condition is not met. Set _neglect_con_ to _true_ to ignore condition checking. Set _neglect_cost_ to _true_ to ignore cost payable checking. Set _copy_info_ to true to return the activate effect's supposed info, for other than EVENT_FREE_CHAIN usually (eg,ep,ev,r,re,rp)
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


Return type | Function |Description
-- | -- | --
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

Return type | Function |Description
-- | -- | --
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

Return type | Function |Description
-- | -- | --
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

Return type | Function |Description
-- | -- | --
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

Return type | Function |Description
-- | -- | --
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

Return type | Function |Description
-- | -- | --
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


Return type | Function |Description
-- | -- | --
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

Return type | Function |Description
-- | -- | --
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


Return type | Function |Description
-- | -- | --
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

Return type | Function |Description
-- | -- | --
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

Return type | Function |Description
-- | -- | --
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

Return type | Function |Description
-- | -- | --
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


### Debug functions
Return type | Function |Description
-- | -- | --
Card | Debug.AddCard(int code, int owner, int player, int location, int seq, int pos[, bool proc=false]) | Add a card of (int code), owned by (int owner) and under (int player)'s control, to (int seq) of (int location) in (int pos) position. If (bool proc) is true, it will be treated as properly summoned for the purposes of revive limits.
void | Debug.Message(any msg) | Sends (any msg) as a script error to the logs
void | Debug.PreAddCounter(Card c, int counter_type, int count) | Add (int count) counters of (int counter_type) to (Card c)
bool | Debug.PreEquip(Card equip_card, Card target) | Equip (Card equip_card) to (Card target)
void | Debug.PreSetTarget(Card c, Card target) | Set (Card c)'s target card to (Card target) (e.g. Call of the Haunted)
void | Debug.PreSummon(Card c, int sum_type[, int sum_location=0]) | Treat (Card c) as if it was summoned by (int sum_type), to (int sum_location)
void | Debug.ReloadFieldBegin(int flag, int rule) | Begin loading the field for a puzzle, with DUEL_ constants in (int flag) under Master Rule (int rule)
void | Debug.ReloadFieldEnd() | Stop loading the field for a puzzle.
void | Debug.SetAIName(string name) | Set the name of the AI to (string name)
void | Debug.SetPlayerInfo(int playerid, int lp, int startcount, int drawcount) | Set (int playerid) to have (int lp) LP, start with a (in startct) card hand, and draw (int drawcount) during the Draw Phase.
void | Debug.ShowHint(string msg) | Display a message on screen, saying (string msg)

### Duel functions
Return type | Function |Description
-- | -- | --
void | Duel.Activate(Effect e) | Activates an effect in a new chain link. If the effect is the activate effect of a spell/trap, that card is also activated.
void | Duel.AddCustomActivityCounter(int counter_id, int activity_type, function f) | Register an activity with type int activity_type, with id int counter_id, that matches function f
void | Duel.AdjustInstantly([Card c]) | Adjust the game state checking self destroy effects, continuous negation effects being applied, etc. If a card is passed, it also adjust immediately the properties of that card and cards related to it.
int | Duel.AnnounceAttribute(int player, int count, int available) | Asks (int player) to announce (int count) number of Attributes, amongst those specified in (int available).
int | Duel.AnnounceCard(int player[, ?]) | Makes the player declare a card name. With no extra parameters, the function allows declaring any monster, spell and trap card names. If a single int parameter is passed as second parameter, that parameter will be used to limit the types that are declarable (for example passing TYPE_MONSTER to only declare monster cards). If 3 or more parameters are passed, the function will use the OPCODE_ constants to build a filter based on the reverse polish notation to allow declaring cards with more specific restrictions (for example declaring cards of a specific archetype only). The opcode parameters can also be passed all in a table as the second parameter.
int | Duel.AnnounceCoin(int player) | Asks (int player) to call heads or tails
int\|nil,int\|nil | Duel.AnnounceLevel(int player[,int min = 1,int max=12, int exception=nil,...]) | Asks (int player) to announce a number between (int min) and (int max), except any (int exception)s. Returns the chosen number, and the index of that number amongst the choices.
int,int | Duel.AnnounceNumber(int player, int number, ...) | Asks (int player) to announce a number found amongst (int number)s. Returns the chosen number and its index amongst the options
int\|nil,int\|nil | Duel.AnnounceNumberRange(int player[,int min = 1,int max=12, int exception=nil,...]) | Asks (int player) to announce a number between (int min) and (int max), except any (int exception)s. Returns the chosen number, and the index of that number amongst the choices.
int | Duel.AnnounceRace(int player, int count, int available) | Asks (int player) to announce (int count) number of Races, amongst those specified in (int available).
int | Duel.AnnounceType(int player) | Makes int player declare a type
void | Duel.AssumeReset() | Manually resets assume effects. Usually used in syncro summon. (eg: it resets the applied effect of "Influence Dragon (Anime)" on the other materials in the Synchro Summon.)
void | Duel.AttackCostPaid([int paid=1]) | Register the status of payment of attack cost. A value of 2 means that the attack cost was not paid, 1 means the attack cost was paid.
void | Duel.BreakEffect() | Separates an effect for the purposes of timing (Reflects the effects of the conjunctives "then" and "also after that")
void | Duel.CalculateDamage(Card c1, Card c2\|nil) | Conduct damage calculation between (Card c1) as attacker and (Card c2) or opponent player (nil)
bool | Duel.CanPlayerSetMonster(int player[, Card sumcard, int sumtype]) | Returns if player can set a monster, if sumcard and sumtype are passed, those parameterers are also passed to the EFFECT_CANNOT_MSET effects.
bool | Duel.CanPlayerSetSpellTrap(int player[, Card setcard]) | Returns if player can set a spell/trap card, if setcard is passed, that parameterer is also passed to the EFFECT_CANNOT_SSET effects.

Return type | Function |Description
-- | -- | --
void | Duel.ChainAttack([Card c]) | Makes the currently attacking card attacks able to declare a consecutive attack after the current one. If a card is passed, the next attack will have to be against that specific card.
void | Duel.ChangeAttacker(Card c[, int ign = false]) | Changes the current monster attacking to another card (Card c), if ignore counts is set to true (int ign) it will ignore if the card can still attack.
bool | Duel.ChangeAttackTarget(Card c\|nil) | Changes the current monster being attacker to another card (or makes the attack a direct attack in case of no card being passed)
void | Duel.ChangeBattleDamage(int player, int value[, bool check=true]) | Changes the battle damage (int player) would take to (int value). If (bool check) == false, you are able change the battle damage that originally is 0.
void | Duel.ChangeChainOperation(int chain_idx, function f) | Replaces the operation executed by the effect at the specific chain index with the passed function.
int | Duel.ChangePosition(Card\|Group targets, int au[, int ad=au, int du=au, int dd=au, bool noflip=false]) | Changes the battle position of (Card\|Group targets). (int au), (int ad), int (du) and (int dd) are the positions cards in face-up attack, face-down attack, face-up defense, and face-down defense positions will be changed to, respectively. If (bool noflip) is true, FLIP effects will not be activated by this change. Returns the number of cards successfully affected.
void | Duel.ChangeTargetCard(int chainc, Group g) | Change the target cards for the specific chain link (0 is the currently resolving one). This alters the value that that chain link set with Duel.SetTargetCards
void | Duel.ChangeTargetParam(int chainc, int param) | Change the target parameter for the specific chain link (0 is the currently resolving one). This alters the value that that chain link set with Duel.SetTargetParam
void | Duel.ChangeTargetPlayer(int chainc, int player) | Change the target player for the specific chain link (0 is the currently resolving one). This alters the value that that chain link set with Duel.SetTargetPlayer
bool | Duel.CheckChainTarget(int chainc, Card c) | Checks if a card (Card c) can be a target for a chain's (int chainc) effect (via calling target(chkc) function of the effect)
bool | Duel.CheckChainUniqueness() | Checks if there is no card with the same name in the current chain
bool[, Group, int, int, Effect, int, int] | Duel.CheckEvent(int event[, bool get_info]) | Returns if, at the activation timing, the (int event) passed is available. If (bool get_info) is set to true, all the even info are returned as extra return values
bool | Duel.CheckLocation(int player, int location, int seq) | Checks if there is an position (int seq) available for the player (int player) in the location (int location). (The sequence (int seq) is used to indicate the specific position of the location, for example in the location of monsters the sequence would go from 0 to 7., etc.)
bool | Duel.CheckLPCost(int player, int cost) | Checks if a player (int player) can pay an amount (int cost) of LP
bool | Duel.CheckPhaseActivity() | Checks if the an "activity" was not performed yet which means that the player is at "the start" of the current phase. Used for effects like Pot of Extravagance, Soundproofed and Mimir of the Nordic Ascendant.


Return type | Function |Description
-- | -- | --
bool | Duel.CheckReleaseGroup(int player, function f, int count[, bool use_hand=false, int max=min, bool check_field=false, Card card_to_check=nil, int to_player=player, int zone=0xff, bool use_oppo=false], Group\|Card ex\|nil, ...) | Check if there is a monster that can be used as tribute from the int player, that satisfies function, having a min and a max of the count specified with the exception of some card/group if specified, ... are extra arguments. If use_hand is true, then cards in the hand are considered for the tribute. If use_oppo is true, opponent's cards are also considered for the tribute. If check_field is true and card_to_check is passed, the function will also take in account to check if there are free zones (int zone) left on to_player's field to summon that card after tributing the cards. Also effects of cards like "Lair of Darkness" are taken into account when performing those checks.
bool | Duel.CheckReleaseGroupCost(int player, function f, int minc[, int maxc=minc], bool use_hand, function spcheck, Card\|Group\|nil ex,...) | Check if the player can tribute cards on the field, excluding "ex" to activate the effect of a monster while also checking for applied effects of cards like "Lair of Darkness" (behaviour now also implemented in the normal CheckReleaseGroup). If function f is passed, the cards returned by Duel.GetReleaseGroup are filtered based on that function. The function spcheck is a callback function that gets passed the current checked group (sg) as first parameter, the checking player (tp) as second parameter, a group containing opponent's cards affected by EFFECT_EXTRA_RELEASE_NONSUM or EFFECT_EXTRA_RELEASE (exg) and the extra parameters passed to the function (...). The spcheck function has to return 1 or 2 boolean values indicating if the passed group (sg) satisfy the requirements as first return value and as optional second parameter to indicate if no matter how many new cards are added to (sg), the condition will never return true.
bool | Duel.CheckReleaseGroupEx(int player, function f, int count[, bool use_hand=true, int max=min, bool check_field=false, Card card_to_check=nil, int to_player=player, int zone=0xff, bool use_oppo=false], Group\|Card ex\|nil, ...) | Same as Duel.CheckReleaseGroup, except that the hand is included by default.
bool | Duel.CheckReleaseGroupSummon(card c, int player, effect e, function fil, int min, int max, function last,...) |  
bool | Duel.CheckRemoveOverlayCard(int player, int s, int o, int count, int reason[, Group ocard]) | Returns if (int player) can remove a total of (int count) cards attached, for reason (int reason) from your field (int s == 1) and/or opponent's (int o == 1). If group (ocard) is provided, only checks if cards can be detached from monsters that match said group.
bool | Duel.CheckSummonedCount([Card c]) | Check if the current reason player can still normal summon other monsters or has used that turn's summons, or if a card is passed and that card is affected by an EFFECT_EXTRA_SUMMON_COUNT effect allowing it to be summoned.
bool | Duel.CheckTiming(int timing) | Returns true if the current activation hint timing is one of the passed timings.
bool | Duel.CheckTribute(Card c, int min[, int max=min, Group\|nil mg, int tp=c:GetControler(), int zone=0x1f]) | Check if there are valid tributes on the field to summon Card c to tp's field in the zones specified by zone using the rules of a normal tribute summon.
void | Duel.ClearOperationInfo(int chainc) | Clear all the informations that were set by Duel.SetOperationInfo for the passed chain.
void | Duel.ClearTargetCard() | Remove all the targeted cards corresponding to the current resolving/building chain.
void | Duel.ConfirmCards(int player, Card\|Group targets) | Reveals the passed cards to the passed player if they are in a private knoweledge state.
void | Duel.ConfirmDecktop(int player, int count) | Reveals a number (int count) of cards from the top of a player's (int player) Deck to both players
void | Duel.ConfirmExtratop(int tp, int count) | Reveals a number (int count) of  facedown cards from the top of a player's (int player) Extra Deck to both players. (faceup pendulum monsters are ignored)
Card | Duel.CreateToken(int player, int code) | Creates a new instance of a card owned by player (int player) with card code (int code).
int | Duel.Damage(int player, int value, int reason[, bool is_step=false]) | Damages/Decreases player's (int player) Life Points by an amount (int value) for a reason (REASON_x). Setting is_step to true made the damage considered dealt at the call of Duel.RDComplete()
int | Duel.Destroy(Card\|Group targets, int reason[ ,int dest = LOCATION_GRAVE]) | Destroys a card or group (Card\|Group targets) with (int reason) as reason, and sends the card in the location specified by (int dest). Returns the number of cards successfully destroyed.

Return type | Function |Description
-- | -- | --

Return type | Function |Description
-- | -- | --

Return type | Function |Description
-- | -- | --

Return type | Function |Description
-- | -- | --

Return type | Function |Description
-- | -- | --
