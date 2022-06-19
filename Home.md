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

### 
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
bool | aux.CheckZonesReleaseSummonCheckSelection(group must, group oneof,function checkfunc) |  
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
void | aux.EnableExtraRules(c,card,init,...) | Functions to automate consistent start-of-duel activations for Duel Modes like Speed Duel, Sealed Duel, etc
void | aux.EnableExtraRulesOperation(card,init,...) |  
void | aux.EnableGeminiAttribute(Card c) | Applies all the effects necessary for a Gemini monster to be used as one to (Card c).
void | aux.EnableNeosReturn(Card c[, int extracat, function extrainfo, function extraop]) | Adds the effect to shuffle the card into the Extra Deck at the End Phase (most commonly used by "Neos" Fusion Monsters). If provided, "extracat", "extrainfo" and "extraop" will add additional effect categories, operation info and operations respectively to the effect. The Condition, Target and Operation functions of this effect, named NeosReturnCondition1/2, NeosReturnTarget and NeosReturnOperation, are detailed in cards_specific_functions.lua.
void | aux.EnableSpiritReturn(Card c, int event1, int ...) | Sets up EVENT triggers to (Card c) so it returns to the hand during that End Phase, requires a minimum of 1 (int event1)
bool | aux.EquipByEffectAndLimitRegister(Card c, Effect e) |  
bool | aux.EquipByEffectLimit(Card c, Effect e, int tp, Card tc, int|nil code, bool mustbefaceup) | Equips (Card tc) to (Card c). Adding a (int code) will register that code as flag effect to the equipped card  (bool mustbefaceup) defines if the card to be equipped is required to be face-up.
void | aux.EquipEquip(Effect e, int tp, Group eg, int ep, int ev, Effect re, int r, int rp) | Used to equip the Equip Card to the targeted monster. This would be used if you cannot use the Equip Procedure for your Equip Card activation.
int | aux.EvilHeroLimit(e,se,sp,st) | Default SetValue for "Evil HERO" monsters's effect EFFECT_SPSUMMON_CONDITION. Must be used due to the existance of "Supreme King Castle"
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
