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
effect | aux.AddContinuousSkillProcedure(c,coverNum, & drawless,flip) | Procedure for continuous Spell/Trap Skill-- c: the card (card)-- coverNum: the Number of the cover (int)-- drawless: if the player draw 1 less card at the start of the duel (bool)-- flip: if the continuous card get flipped at the start of the duel (bool)
void | aux.AddEquipProcedure(Card c, int\|nil p, function\|nil f, function\|nil eqlimit, function\|nil cost, function\|nil tg, function\|nil op, function\|nil con) | Adds the Equip Card Activation where (int p) is the player, setting 0 will limit to monsters you control, setting to 1 will be your opponent and PLAYER_ALL/nil will be for either player. (function f) is the filters on which monsters you can equip it to. (function eqlimit) if provided will that limitation on which monsters you can only equip it (e.g. Those that can only be equipped by this activation, e.g. Train Connection). (function cost) would be the cost to activate it. (function tg) are effects that applied to it after targeting the monster to equip, and also checking requirements. (function op) is any operation that is applied after the Equip Proc equips. (function con) returns a bool which are conditions that need to be fulfilled for the Equip Card to be activated.
void | aux.AddEREquipLimit(Card c, function\|nil con, function\|nil equipval, function equipop, Effect linkedeff, int\|nil prop, int\|nil resetflag, int\|nil resetcount) | Registers effects that need to be checked for the effect of "Millennium-Eyes Illusionist". (function con) is any conditions that need to be fulfilled in order to apply its "equipping" effect. (function equipval) is the filter of valid monsters you can equip to it. (function equipop) is the equipping by its effect. (Effect linkedeff) is the effect that equips. (int prop) is the list of additional properties for SetProperty to register effects. (int resetflag) and (int resetcount) is used if the effect would reset such as, until only the End Phase.
effect | aux.AddFieldSkillProcedure(card c, coverNum, drawless) | Procedure for Field skills--c: the skill (card)--coverNum: the cover corresponding to the back (int)--drawless: if the skill make you draw 1 less card at the start of the duel (bool)
effect, effect | aux.AddKaijuProcedure(card c) | Adds Kaiju's stardand procedure to the monster (which also includes the uniqueness on field condition). Calls the following auxilary function: KaijuCondition
effect | aux.AddLavaProcedure(card c, int required, int position, funtion filter, int value, int description) | Adds Lava Golem-like procedure (monster that tribute to Special Summon on opponent's field), int required is the amount of monster to tribute, position is which position is it summoned and filter specify the monster it must tribute, value sets the type of Special summon and description adds a description for it. Calls the following auxiliary functions: LavaCondition, LavaCheck, LavaTarget and LavOperation, defined in cards_specific_functions.lua.
function | aux.AddMaleficSummonProcedure(c,code,loc,excond) | Procedure for "Malefic" monsters' Special Summon (also includes handling of "Malefic Paradox Gear"'s effect)
effect | aux.AddNormalSetProcedure(card c, bool ns, bool opt, int min, int max, int sum_type_val, string desc, function f, function sumop) |  
effect | aux.AddNormalSummonProcedure(card c, bool ns, bool opt, int min, int max, int sum_type_val, string desc, function f, function sumop) |  


Return type | Function |Description
-- | -- | --
void | aux.AddPersistentProcedure(Card c, int\|nil p, function\|nil f, int\|nil category, & int\|nil property, int\|nil hint1, int\|nil hint2, function\|nil con, function\|nil cost, function\|nil tg, function\|nil op, bool\|nil anypos) | Adds the Persistent Trap Procedure where is the player, setting 0 will limit to monsters you control, setting to 1 will be your opponent and PLAYER_ALL/nil will be for either player. (function f) is the filters on which monsters you can target. (bool anypos) is a check if the target needs to be face-up. Setting this to true will allow it to be targeted even if it isn't face-up.
effect | aux.AddPreDrawSkillProcedure(c,coverNum,drawless,skillcon,skillop,countlimit) | Function for the skills that "trigger" at the start of the turn/Before the Draw-- c: the card (card)-- coverNum: the Number of the cover (int)-- drawless: if the player draw 1 less card at the start of the duel (bool)-- flip con: condition to activate the skill (function)-- flipOp: operation related to the skill activation (function)
effect | aux.AddSkillProcedure(c,coverNum,drawless,skillcon,skillop,countlimit) | Procedure for basic skill-- c: the card (card)-- coverNum: the Number of the cover (int)-- drawless: if the player draw 1 less card at the start of the duel (bool)-- flip con: condition to activate the skill (function)-- flipOp: operation related to the skill activation (function)
void | aux.AddUnionProcedure(Card c, function f, bool oldrule, bool oldprotect) | Adds the Union Procedure to (Card c) where (function f) is the cards you can equip the Union monster to, and (bool oldrule) is a check to apply old rulings of the Union monster. if oldprotect is not nil, uses old rules for destroy replacement (If the equipped monster would be destroyed, destroy this card instead.)
void | aux.AddValuesReset(resetfunc) |  
effect | aux.AddVrainsSkillProcedure(c,skillcon,skillop,efftype) | Procedure for Vrains Skills--flip con: condition to activate the skill (function)--flipOp: operation related to the skill activation (function)--efftype: Event to trigger the Skill, default to EVENT_FREE_CHAIN. Additionally accept EFFECT_NEGATE_SKILL for Anti Skill (int)
bool | aux.AND(...)(...) | First (...) is a list of functions which will be used to check the parameters in the second set of (...), separated with "and". The second set of (...) is applied automatically when used as a filter.
int | aux.AnnounceAnotherAttribute(group g, int player) | Makes (int player) announce an attribute different from the one(s) already among the members of (group g)
int | aux.AnnounceAnotherRace(group g, int player) | Makes (int player) announce a monster type (Race) different from the one(s) already among the members of (group g)
int | aux.AskAny(stringid) |  
int | aux.AskEveryone(stringid) |  
bool | aux.bdcon(Effect e, int tp, Group eg\|nil, int ep, int ev, Effect re, int r, int rp) | Default condition of EVENT_BATTLE_DESTROYING. "When this card destroys a monster by battle" and checks if itself is still the same state after battle.
bool | aux.bdgcon(Effect e, int tp, Group eg\|nil, int ep, int ev, Effect re, int r, int rp) | Condition of EVENT_BATTLE_DESTROYING. "When this card destroys a monster by battle and sends it to the Graveyard" and checks if itself is still the same state after battle.
bool | aux.bdocon(Effect e, int tp, Group eg\|nil, int ep, int ev, Effect re, int r, int rp) | Condition of EVENT_BATTLE_DESTROYING. "When this card destroys an opponent's monster by battle" and checks if itself is still the same state after battle.
bool | aux.bdogcon(Effect e, int tp, Group eg\|nil, int ep, int ev, Effect re, int r, int rp) | Condition of EVENT_BATTLE_DESTROYING. "When this card destroys an opponent's monster by battle and sends it to the Graveyard" and checks if itself is still the same state after battle.
void | aux.BeginPuzzle() | Sets up the beginning of a puzzle, causing the player to lose during the End Phase
bool | aux.bfgcost(Effect e, int tp, Group\|nil eg, int ep, int ev, Effect re, int r, int rp, int chk) | Default SetCost for "You can banish this card from your Graveyard"
table | aux.BitSplit(int number) | Auxiliary function to help printing hints for attribute-related cards such as Cynet Codec
void | aux.CallToken(int code) | Function is used mostly for Anime Cards calling 419/420 to enable more functions. Also used in Anime Numbers with alias to prevent errors made by alias.
bool | aux.CanActivateSkill(int player) |  

Return type | Function |Description
-- | -- | --

