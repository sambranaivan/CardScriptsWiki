| Column1 | Column2 | Column3 |
| --- | --- | --- |
| value | name | desc |
| void | aux.AddAmazementQuickEquipEffect(Card c,  int id) | Adds the following effect to a card: "(Quick Effect): You can target 1 of your "Attraction" Traps that is equipped to a monster; equip it to 1 "Amazement" monster you control or 1 face-up monster your opponent controls." Parameters: (Card c) the card to add the effect to; (int id) the ID of the card to be used with HOPT effects. |
| void | aux.AddAttractionEquipProc(Card c) | Adds the following common equip effect shared by "Attraction" Traps: "Target 1 "Amazement" monster you control or 1 face-up monster your opponent controls; equip this card to it." Parameters: (Card c) the card to add the effect to |
| effect | aux.AddContinuousSkillProcedure(c,  coverNum,  drawless,  flip) | Procedure for continuous Spell/Trap Skill -- c: the card (card) -- coverNum: the Number of the cover (int) -- drawless: if the player draw 1 less card at the start of the duel (bool) -- flip: if the continuous card get flipped at the start of the duel (bool) |
| void | aux.AddDrawless(Card c,  int drawless_count) | Auxiliary function for skills that have "You daw 1 less card at the beginning of the duel". |
| void | aux.AddEquipProcedure(Card c,  int\|nil p,  function\|nil f,  function\|nil eqlimit,  function\|nil cost,  function\|nil tg,  function\|nil op,  function\|nil con) | Adds the Equip Card Activation where (int p) is the player, setting 0 will limit to monsters you control, setting to 1 will be your opponent and PLAYER_ALL/nil will be for either player. (function f) is the filters on which monsters you can equip it to. (function eqlimit) if provided will that limitation on which monsters you can only equip it (e.g. Those that can only be equipped by this activation,  e.g. Train Connection). (function cost) would be the cost to activate it. (function tg) are effects that applied to it after targeting the monster to equip, and also checking requirements. (function op) is any operation that is applied after the Equip Proc equips. (function con) returns a bool which are conditions that need to be fulfilled for the Equip Card to be activated. |
| void | aux.AddEREquipLimit(Card c,  function\|nil con,  function\|nil equipval,  function equipop,  Effect linkedeff,  int\|nil prop,  int\|nil resetflag,  int\|nil resetcount) | Registers effects that need to be checked for the effect of "Millennium-Eyes Illusionist". (function con) is any conditions that need to be fulfilled in order to apply its "equipping" effect. (function equipval) is the filter of valid monsters you can equip to it. (function equipop) is the equipping by its effect. (Effect linkedeff) is the effect that equips. (int prop) is the list of additional properties for SetProperty to register effects. (int resetflag) and (int resetcount) is used if the effect would reset such as, until only the End Phase. |
| effect | aux.AddFieldSkillProcedure(card c,  coverNum,  drawless) | Procedure for Field skills --c: the skill (card) --coverNum: the cover corresponding to the back (int) --drawless: if the skill make you draw 1 less card at the start of the duel (bool) |
| effect, effect | aux.AddKaijuProcedure(card c) | Adds Kaiju's stardand procedure to the monster (which also includes the uniqueness on field condition). Calls the following auxiliary function: KaijuCondition |
| effect | aux.AddLavaProcedure(card c,  int required,  int position,  funtion filter,  int value,  int description) | Adds Lava Golem-like procedure (monster that tribute to Special Summon on opponent's field), int required is the amount of monster to tribute, position is which position is it summoned and filter specify the monster it must tribute, value sets the type of Special summon and description adds a description for it. Calls the following auxiliary functions: LavaCondition, LavaCheck, LavaTarget and LavOperation, defined in cards_specific_functions.lua. |
| function | aux.AddMaleficSummonProcedure(c, code, loc, excond) | Procedure for "Malefic" monsters' Special Summon (also includes handling of "Malefic Paradox Gear"'s effect) |
| effect | aux.AddNormalSetProcedure(card c,  bool ns,  bool opt,  int min,  int max,  int sum_type_val,  string desc,  function f,  function sumop) | Adds a procedure to a monster that can be Normal Summoned/Set. (Card c) is the card receiving the effect. If both (bool ns) and (bool opt) are set to true, the effect is created with code EFFECT_SET_PROC, otherwise EFFECT_LIMIT_SET_PROC is used. (int min) and (int max) are the number of tributes to use. (int sum_type) is the type of the summon and defaults to SUMMON_TYPE_TRIBUTE. (string desc) is the description used when the player attempts the summon (usable via aux.Stringid). (function f) is a function that must be fulfilled by the tributes and (function sumop) is a special function that must be executed with the ttributes |
| effect | aux.AddNormalSummonProcedure(card c,  bool ns,  bool opt,  int min,  int max,  int sum_type_val,  string desc,  function f,  function sumop) |
| void | aux.AddPersistentProcedure(Card c,  int\|nil p,  function\|nil f,  int\|nil category,  int\|nil property,  int\|nil hint1,  int\|nil hint2,  function\|nil con,  function\|nil cost,  function\|nil tg,  function\|nil op,  bool\|nil anypos) | Adds the Persistent Trap Procedure where is the player, setting 0 will limit to monsters you control, setting to 1 will be your opponent and PLAYER_ALL/nil will be for either player. (function f) is the filters on which monsters you can target. (bool anypos) is a check if the target needs to be face-up. Setting this to true will allow it to be targeted even if it isn't face-up. |
| effect | aux.AddPreDrawSkillProcedure(c, coverNum, drawless, skillcon, skillop, countlimit) | Function for the skills that "trigger" at the start of the turn/Before the Draw -- c: the card (card) -- coverNum: the Number of the cover (int) -- drawless: if the player draw 1 less card at the start of the duel (bool) -- flip con: condition to activate the skill (function) -- flipOp: operation related to the skill activation (function) |
| effect | aux.AddSkillProcedure(c, coverNum, drawless, skillcon, skillop, countlimit) | Procedure for basic skill -- c: the card (card) -- coverNum: the Number of the cover (int) -- drawless: if the player draw 1 less card at the start of the duel (bool) -- flip con: condition to activate the skill (function) -- flipOp: operation related to the skill activation (function) |
| void | aux.AddUnionProcedure(Card c,  function f,  bool oldrule,  bool oldprotect) | Adds the Union Procedure to (Card c) where (function f) is the cards you can equip the Union monster to, and (bool oldrule) is a check to apply old rulings of the Union monster. if oldprotect is not nil, uses old rules for destroy replacement (If the equipped monster would be destroyed,  destroy this card instead.) |
| void | aux.AddValuesReset(function resetfunc) | Executes, at EVENT_TURN_END, the reset function(s) passed as argument (function resetfunc) |
| effect | aux.AddVrainsSkillProcedure(c, skillcon, skillop, efftype) | Procedure for Vrains Skills --flip con: condition to activate the skill (function) --flipOp: operation related to the skill activation (function) --efftype: Event to trigger the Skill, default to EVENT_FREE_CHAIN. Additionally accept EFFECT_NEGATE_SKILL for Anti Skill (int) |
| void | aux.AddZWEquipLimit(c, con, equipval, equipop, linkedeff, prop, resetflag, resetcount) | Equip Limit Proc for cards that equip themselves to another card: con = condition for when the card can equip to another 'f(e)'; equipval = filter for the equip target; equipop = what happens when the card is equipped to the target; tc = equip target; c = equip card; linkedeffect = usually the effect of Card c that equips, this ensures Phantom of Chaos handling; prop = extra effect properties; resetflag/resetcount = resets values |
| bool | aux.AND(...)(...) | First (...) is a list of functions which will be used to check the parameters in the second set of (...), separated with "and". The second set of (...) is applied automatically when used as a filter. |
| int | aux.AnnounceAnotherAttribute(Card c,  int player) | Function deprecated since version 40.0.0. Use "Card.AnnounceAnotherAttribute" instead |
| int | aux.AnnounceAnotherRace(Card c,  int player) | Function deprecated since version 40.0.0. Use "Card.AnnounceAnotherRace" instead |
| int | aux.AskAny(stringid) | Function deprecated since version 40.0.0. Use "Duel.AskAny" instead |
| int | aux.AskEveryone(stringid) | Function deprecated since version 40.0.0. Use "Duel.AskEveryone" instead |
| function | auxAttractionEquipCon(self) | Returns a function which checks if the card is equipped and if the equipped monster is controlled by the player (self=true) or by the opponent (self=false) |
| bool | aux.bdcon(Effect e,  int tp,  Group eg\|nil,  int ep,  int ev,  Effect re,  int r,  int rp) | Default condition of EVENT_BATTLE_DESTROYING. "When this card destroys a monster by battle" and checks if itself is still the same state after battle. |
| bool | aux.bdgcon(Effect e,  int tp,  Group eg\|nil,  int ep,  int ev,  Effect re,  int r,  int rp) | Condition of EVENT_BATTLE_DESTROYING. "When this card destroys a monster by battle and sends it to the Graveyard" and checks if itself is still the same state after battle. |
| bool | aux.bdocon(Effect e,  int tp,  Group eg\|nil,  int ep,  int ev,  Effect re,  int r,  int rp) | Condition of EVENT_BATTLE_DESTROYING. "When this card destroys an opponent's monster by battle" and checks if itself is still the same state after battle. |
| bool | aux.bdogcon(Effect e,  int tp,  Group eg\|nil,  int ep,  int ev,  Effect re,  int r,  int rp) | Condition of EVENT_BATTLE_DESTROYING. "When this card destroys an opponent's monster by battle and sends it to the Graveyard" and checks if itself is still the same state after battle. |
| void | aux.BeginPuzzle() | Sets up the beginning of a puzzle, causing the player to lose during the End Phase |
| bool | aux.bfgcost(Effect e,  int tp,  Group\|nil eg,  int ep,  int ev,  Effect re,  int r,  int rp,  int chk) | Default SetCost for "You can banish this card from your Graveyard" |
| table | aux.BitSplit(int number) | Auxiliary function to help printing hints for attribute-related cards such as Cynet Codec |
| bool | aux.CanActivateSkill(int player) | Adds a procedure to a monster that can be Normal Summoned/Set. (Card c) is the card receiving the effect. If both (bool ns) and (bool opt) are set to true, the effect is created with code EFFECT_SET_PROC, otherwise EFFECT_LIMIT_SET_PROC is used. (int min) and (int max) are the number of tributes to use. (int sum_type) is the type of the summon and defaults to SUMMON_TYPE_TRIBUTE. (string desc) is the description used when the player attempts the summon (usable via aux.Stringid). (function f) is a function that must be fulfilled by the tributes and (function sumop) is a special function that must be executed with the tributes |
| int | aux.cannotmatfilter(int val1,  [int ...]) | Return the value(s) passed formatted to be used for EFFECT_CANNOT_BE_MATERIAL. |
| bool | aux.CanPlaceCounter(card c, int counter_type) | Function deprecated since version 40.0.0. Use "Card.PlacesCounter" instead |
| void | aux.chainreg(Effect e,  int tp,  Group eg\|nil,  int ep,  int ev,  Effect re,  int r,  int rp) | Flag effect used for Spell Counter (that are put when the Spell card resolves) |
| int | aux.ChangeBattleDamage(int player,  int value) | Changes the battle damage that (int player) would have taken to (int value) |
| bool | aux.CheckPendulumZones(int player) | Function deprecated since version 40.0.0. Use "Duel.CheckPendulumZones" instead |
| bool | aux.CheckSkillNegation(e, tp) | Function to check whether the Skill would be negated by Anti Skill |
| bool | aux.CheckStealEquip(Card c,  Effect e,  int tp) |
| bool/int | aux.CheckSummonGate(tp, count) | If (int count) is provided, checks if the player (int player) is affected by Summon Gate and if that the argument surpass  the maximum number of summons before Summon Gate's effect applies. If (int count) is not provided, returns the remains number of summons that would cause Summon Gate's effect to apply |
| bool | aux.CheckValidExtra(card c,  int player,  group sg,  group mg,  lc,  group emt,  function filt) | Auxiliary function used by the Link Summon procedure. |
| bool | aux.CheckZonesReleaseSummonCheck(group must,  group oneof,  function checkfunc) | Auxiliary function called by "Duel.SelectReleaseGroupSummon". |
| bool | aux.CheckZonesReleaseSummonCheckSelection(group must,  group oneof, function checkfunc) |
| bool | aux.ChkfMMZ(int sumcount)(Group sg,  Effect e,  int tp,  Group mg) | "Check for Main Monster Zones". Used in rescon by default. 2nd parenthesis is not required as rescon/cancelcon in aux.SelectUnselectGroup. (Group sg) is the selected group when using aux.SelectUnselectGroup. Evaluates if a int sumcount number of Main Monsters zones are available and/or will be made available to summon the requiring card. |
| int | aux.ComposeNumberDigitByDigit(int tp,  int min,  int max) | (int tp) declares a number by digit with a minimum of (int min) and maximum of (int max) |
| function | aux.continuousOp(...) |
| function | aux.addContinuousLizardCheck(...) |
| function | aux.createTempLizardCheck(...) |
| function | aux.CostWithReplace(function base,  int replacecode,  function extracon,  function alwaysexecute) |
| effect | aux.CreateUrsarcticSpsummon(c, id) | Registers to (Card c) a Quick Effect that Special Summons itself from the hand by tributing another level 7 or higher monster from the hand. This is the common effect for "Ursarctic" monsters and already handles the cost replacement from "Ursarctic Big Dipper". (int id) is (Card c)'s ID, to register the effect as HOPT. |
| effect | aux.CreateWitchcrafterReplace(c, id) | Registers to (Card c) a Field effect (that applies from LOCATION_SZONE) that flags it as replacement for the discard cost of "Witchcrafter" monsters.  (int id) is (Card c)'s ID, to register the effect as HOPT. See "Witchcrafter Scroll" and "Witchcrafter Bystreet". |
| bool | aux.damcon1(Effect e,  int tp,  Group eg\|nil,  int ep,  int ev,  Effect re,  int r,  int rp) | Default condition for "If you would take effect damage" |
| bool | aux.DeckMill(p, num, reason) | proc_maximum (Rush function) |
| void | aux.DefaultFieldReturnOp(Group rg,  Effect e,  int tp) | An operation function to be used with `aux.RemoveUntil`. Return the banished cards to the monster zone. Makes the player select cards to return if there are less available zones than returnable cards. |
| effect | aux.DelayedOperation(card_or_group,  phase,  flag,  e,  tp , oper,  cond,  reset,  reset_count,  hint) |
| void | aux.DeleteExtraMaterialGroups(group emt) | Auxiliary function used by the Link Summon procedure |
| bool | aux.disfilter1(Card c) | Function deprecated since version 40.0.0. Use "Card.IsNegatableMonster" instead |
| bool | aux.disfilter2(Card c) | Function deprecated since version 40.0.0. Use "Card.IsNegatableSpellTrap" instead |
| bool | aux.disfilter3(Card c) | Function deprecated since version 40.0.0. Use "Card.IsNegatable" instead |
| function | aux.dncheck | Checks for cards with different names (usually be used with aux.SelectUnselectGroup) |
| bool | aux.dogcon(Effect e,  int tp,  Group eg\|nil,  int ep,  int ev,  Effect re,  int r,  int rp) | SetCondition for "is destroyed by your opponent". |
| void | aux.DoubleSnareValidity(card c,  int range,  int property) | Registers that card c has an effect that can negate/destroy trap cards, while it is in the location defined in int range. Used by Double Snare to identify which cards it can destroy. Int property are additional properties other than the default EFFECT_FLAG_CANNOT_DISABLE\|EFFECT_FLAG_SINGLE_RANGE. |
| bool | aux.DoubleTributeCon(e,  tp) |
| function | aux.drawlessop(...) | Auxiliary function for skills that have "You draw 1 less card at the beginning of the duel". |
| bool | aux.dpcheck(function f) | Checks for cards with different properties (the property defined in function f,  for example,  Card.GetLevel,  GetAttribute,  GetRace,  GetCode,  etc). Usually used with aux.SelectUnselectGroup. |
| function | aux.dxmcostgen(int min,  int max,  [function op]) | "Detach Xyz Material Cost Generator". Generates a function to be used by Effect.SetCost in order to detach a number of Xyz Materials from the Effect's handler. (int min) is the minimum number of materials to check for detachment. (int max) is the maximum number of materials to detach or a function that gets called as if by doing max(e, tp) in order to get the value of max detachments. (function op) is an optional function that gets called by passing the effect and the operated group of just detached materials in order to do some additional handling with them. |
| void | aux.EnableCheckReincarnation(Card c) | Auxiliary function for "Salamangreat" Reincarnation procedure. Enables reincarnation links. |
| void | aux.EnableExtraRules(c, card, init, ...) | Functions to automate consistent start-of-duel activations for Duel Modes like Speed Duel, Sealed Duel, etc |
| void | aux.EnableExtraRulesOperation(card, init, ...) |
| void | aux.EnableGeminiAttribute(Card c) | Function deprecated since version 40.0.0. Use "Gemini.AddProcedure" instead |
| void | aux.EnableNeosReturn(Card c[,  int extracat,  function extrainfo,  function extraop]) | Adds the effect to shuffle the card into the Extra Deck at the End Phase (most commonly used by "Neos" Fusion Monsters). If provided, "extracat", "extrainfo" and "extraop" will add additional effect categories, operation info and operations respectively to the effect. The Condition, Target and Operation functions of this effect, named NeosReturnCondition1/2, NeosReturnTarget and NeosReturnOperation, are detailed in cards_specific_functions.lua. |
| void | aux.EnableSpiritReturn(Card c,  int event1,  int ...) | Function deprecated since version 40.0.0. Use "Spirit.AddProcedure" instead |
| bool | aux.EquipFilter(Card c,  int player,  function f,  Effect e,  int tp) |
| bool | aux.EquipByEffectAndLimitRegister(Card c,  Effect e) | Function deprecated since version 40.0.0. Use "Card.EquipByEffectAndLimitRegister" instead |
| bool | aux.EquipByEffectLimit(Card c,  Effect e,  int tp,  Card tc,  int\|nil code,  bool mustbefaceup) | Function deprecated since version 40.0.0. Use "Card.EquipByEffectLimit" instead |
| void | aux.EquipEquip(Effect e,  int tp,  Group eg,  int ep,  int ev,  Effect re,  int r,  int rp) | Used to equip the Equip Card to the targeted monster. This would be used if you cannot use the Equip Procedure for your Equip Card activation. |
| bool | aux.EquipFilter(c, p, f, e, tp) |
| function | aux.EquipLimit(f) |
| function | aux.EquipTarget(tg, p, f) |
| int | aux.EvilHeroLimit(e, se, sp, st) | Default SetValue for the effect of "Evil HERO" monsters that use EFFECT_SPSUMMON_CONDITION. Must be used due to the existence of "Supreme King Castle" |
| bool | aux.evospcon(Effect e,  int tp,  Group eg\|nil,  int ep,  int ev,  Effect re,  int r,  int rp) | Default SetCondition for "Summoned by a "Evolsaur" monster" |
| bool | aux.exccon(Effect e) | SetCondition for "except the turn this card was sent to the Graveyard". |
| function | aux.FaceupFilter(function f,  ...) | Filter to check face-up cards that match (function f) where (...) are extra parameters to f. Can be used as the function parameter in SelectMatchingCard/Target and IsExistingMatchingCard/Target. |
| bool | aux.FALSE() | Function that returns false |
| bool | aux.fieldop(...) |
| bool | aux.FieldSummonProcTg(function f1,  function f2) |
| bool | aux.FilterBoolFunction(function f,  ...) | Used in filters (with parameter (Card c)) to check a function and its (...) parameters |
| bool | aux.FilterBoolFunctionEx(function f,  int value) | Used filter for the Fusion, Xyz, Synchro and Link Procedures where (function f) can be Card.IsRace, Card.IsAttribute and Card.IsType and (int value) corresponds to the required Race, Attribute and Type. |
| bool | aux.FilterBoolFunctionEx2(function f,  ...) |
| bool | aux.FilterEqualFunction(function f,  int value,  ...) | Used in filters (with parameter (Card c)) to check a function and its (...) parameters is equal to the inputted (int value). |
| function | aux.FilterFaceupFunction(function f) | Function deprecated since version 40.0.0. Use "aux.FaceupFilter" instead |
| function | aux.FilterMaximumSideFunction(f, ...) |
| function | aux.FilterMaximumSideFunctionEx(f, ...) |
| bool | aux.FilterSummonCode(...) | used for Material Types Filter Bool (works for IsRace,  IsAttribute,  IsType) |
| bool | aux.FossilLimit(e, se, sp, st) |
| function | aux.FunctionWithNamedArgs(function f,  ...) |
| function | aux.FusionProcedure() |
| bool | aux.fuslimit(Effect e,  Effect se,  int sp,  int st) | SPSUMMON condition "Must be Fusion Summoned" |
| bool | aux.gbspcon(Effect e,  int tp,  Group eg\|nil,  int ep,  int ev,  Effect re,  int r,  int rp) | Default SetCondition for "Summoned by a "Gladiator Beast" monster" |
| bool | aux.GeminiNormalCondition(Effect e) | Function deprecated since version 40.0.0. Use Gemini.NormalStatusCondition instead |
| table | aux.GetAttributeStrings() |
| table | aux.GetCoinEffectHintString() |
| int | aux.GetCover(card c,  coverNum) | Used by the Skill procedure. |
| table,group | aux.GetExtraMaterials(int player,  group mustg,  group sc,  int summon_type) |
| int | aux.GetMMZonesPointedTo(int player, [ function by_filter, int player_location,  int oppo_location,  int target_player,  ...]) | Returns the zone values (bitfield mask) of the Main Monster Zones on the field of "target_player" that are pointed to by any Link Cards, which match the "by_filter" function/filter, in the locations "player_location" and "oppo_location", from the perspective of "player". The filter by default checks that the card is face-up and is a Link Card, any additional check (e.g. archetype) is added onto that. Both locations default to LOCATION_MZONE if not provided since most cards care about zones that any Link Monster points to, if you want to include Link Spells then use LOCATION_ONFIELD, or LOCATION_SZONE to exclude Link Monsters and check for Link Spells only. The second location defaults to the first one if not provided, but 0 can be passed if you need to not count a side of the field for that location. "target_player" defaults to "player" if not provided. "..." are any additional parameters that "by_filter" might need. |
| Group | aux.GetMustBeMaterialGroup(int tp,  nil\|Group eg,  int sump,  nil\|Card sc,  nil\|Group g,  int r) | Gets the group that must be used as material (Contacting "C"). (int tp) is the affected player, (nil\|Group eg) is all detected materials, (int sump) is the Summoning player, (nil\|Card sc) is the card to be Summoned, (nil\|Group) g is all the valid usable materials, (int r) is the reason e.g. REASON_SYNCHRO, REASON_XYZ |
| table | aux.GetRaceStrings(int number) |
| void | aux.GlobalCheck(s,  function func) | Enables a global check to be used with function "func" |
| int | aux.GrouptoCardid() |
| bool | aux.HarmonizingMagFilter(c, e, f) |
| bool | aux.HarmonizingMagFilterXyz(c, e, f) |
| bool | aux.HasCounterListed(card c,  int counter_type) | Function deprecated since version 40.0.0. Use "Card.ListsCounter" instead |
| bool | aux.HasListedSetCode(Card c,  int ...) | Function deprecated since version 40.0.0. Use "Card.ListsArchetype" instead |
| function | aux.IceBarrierDiscardCost() |
| function | aux.IceBarrierDiscardFilter() |
| function | aux.IceBarrierDiscardGroup() |
| bool | aux.imval1(Effect e,  Card c) | default filter for EFFECT_CANNOT_BE_BATTLE_TARGET where (Card c) is checked to ensure it's not immune to (Effect e) |
| bool | aux.imval2(Effect e,  Card c) | similar to aux.imval1, but also check if the monster is from opponent. |
| bool | aux.indesfilter(...) | Called by proc_maximum.lua |
| bool | aux.indoval(Effect e,  Effect re,  int rp) | Returns if the reason player is equal to 1-effect e's handler player. Commonly used as filter for EFFECT_INDESTRUCTABLE_EFFECT + opponent |
| bool | aux.indsval(Effect e,  Effect re,  int rp) | Returns if the reason player is equal to effect e's handler player. Commonly used as filter for EFFECT_INDESTRUCTABLE_EFFECT + self |
| bool | aux.IsArchetypeCodeListed(card c,  int ...) | Function deprecated since version 40.0.0. Use "Card.ListsCodeWithArchetype" instead |
| bool | aux.IsCardTypeListed(Card c,  int ...) | Function deprecated since version 40.0.0. Use "Card.ListsCardType" instead |
| bool | aux.IsCodeListed(Card c,  int ...) | Function deprecated since version 40.0.0. Use "Card.ListsCode" instead |
| bool | aux.IsGeminiState(Card c) | Function deprecated since version 40.0.0. Use "Card.ListsCodeAsMaterial" instead |
| bool | aux.IsMaterialListCode(Card c,  int ...) | Function deprecated since version 40.0.0. Use "Card.ListsCodeAsMaterial" instead |
| bool | aux.IsMaterialListSetCard(Card c,  int ...) | Function deprecated since version 40.0.0. Use "Card.ListsArchetypeAsMaterial" instead. |
| bool | aux.IsMaximumMode(Card c) |
| bool | aux.IsNotGeminiState(Card c) |
| bool | aux.IsUnionState(Effect effect) | Used as a default condition to check if the handler of the effect is a Union monster equipped to another monster. |
| bool | aux.IsZone(card c,  int zone,  int tp) | Returns if (card c) is in the (int zone), (int tp) is the reference player. |
| bool | aux.KaijuCondition(e, c) | See cards_specific_functions.lua |
| bool | aux.LavaCheck(sg, e, tp, mg) | See cards_specific_functions.lua |
| bool | aux.LavaCondition(required, filter) | See cards_specific_functions.lua |
| void | aux.LavaOperation(required, filter) | See cards_specific_functions.lua |
| bool | aux.LavaTarget(required, filter) | See cards_specific_functions.lua |
| function | aux.LinkProcedure() |
| bool | aux.lnklimit(Effect e,  Effect se,  int sp,  int st) | SPSUMMON condition "Must be Link Summoned" |
| int | aux.MainAndExtraGetSummonZones(card c,  int mmz,  int emz,  effect e,  int sumtype,  int sump,  int targetp,  bool nocheck,  bool nolimit,  int pos,  nc,  ...) |
| bool, Group | aux.MainAndExtraSpSummonLoop(function\|nil func,  int sumtype,  int sump,  int targetp,  bool nocheck,  bool nolimit,  int pos,  int mmz,  int emz)(Effect e,  int tp,  Group eg,  int ep, int ev,  Effect re,  int r,  int rp,  Group sg) | Loops Special Summoning (Group sg) to ensure they go in a valid zone (Extra Monster Zone and Main Monster Zones) where (function func) is a function called after each card in the Group is summoned with the parameters (Effect e,  int tp,  Group eg,  int ep, int ev,  Effect re,  int r,  int rp,  Card sc) where (Card sc) is the card that's Summoned. (int sumtype) is the Summon Type. (int sump) is the Summoning player. (int targetp) is the target player. (bool nocheck) checks for "ignoring the Summoning conditions". And (bool nolimit) checks for "ignoring proper Summon". (int pos) is the position to be Summoned. (int mmz) is the zones where you can Special Summon monsters in (Group sg) to the Main Monster Zone, which defaults to all Main Monster Zones if there is no input or nil is inputed. (int emz) on the other is similar to (int mmz) but it checks for cards from the Extra Deck which Special Summons to the Extra Monster Zone. |
| bool | aux.MainAndExtraZoneCheckBool(card c,  int mmz,  int emz,  effect e,  int sumtype,  int sump,  int targetp,  bool nocheck,  bool nolimit,  int pos,  nc,  ...) |
| function | aux.MakeSpecialCheck() |
| function | aux.MaleficSummonCondition(cd,  int loc,  function excon) | Auxiliary function for the summoning procedure of "Malefic" monsters. Checks if the player has the zone to summon and the appropriate monster (cd) to banish. |
| function | aux.MaleficSummonFilter(c, cd) | Filter used with AddMaleficSummonProcedure. Returns if card (Card c)'s ID is (cd) and if c can be banished as cost |
| function  | aux.MaleficSummonOperation(cd,  int loc) | Auxiliary function to handle the summoning procedure of "Malefic" monsters. Performs the actual summon of the monster by removing the appropriate monster. |
| function | aux.MaleficSummonSubstitute(card c,  card cd,  int tp) | Used with the Summoning Procedure of "Malefic" monsters. Checks for the effect of "Malefic Paradox Gear" |
| function | aux.MaleficSummonTarget() |
| function | aux.MaleficUniqueFilter(c) | Used as filter for the uniqueness on field with the "Malefic" monsters |
| function | aux.MaximumProcedure() |
| bool | aux.MZFilter(Card c,  int tp) | Filter to check monsters if it's on a Main Monster Zone |
| bool | aux.NecroValleyFilter(function f)(Card target,  ...) | Filter check "not affected by Necrovalley" in addition to its own filter, if used as function filter, (Card target,  ...) is defined by default |
| bool | aux.NeosReturnCondition1(e, tp, eg, ep, ev, re, r, rp) | See cards_specific_functions.lua. |
| bool | aux.NeosReturnCondition2(e, tp, eg, ep, ev, re, r, rp) | See cards_specific_functions.lua. |
| void | aux.NeosReturnOperation(c, extraop) | See cards_specific_functions.lua. |
| bool | aux.NeosReturnSubstituteFilter(Card c) | Auxiliary filter used by NeosReturnOperation. Returns if Card c can be removed as cost and is Neos Fusion |
| void | aux.NeosReturnTarget(c, extrainfo) | See cards_specific_functions.lua. |
| iterator | aux.Next(Group g) | Iterates over the cards in (Group g) for use with for loops |
| function | aux.NormalSetCondition1() |
| function | aux.NormalSetCondition2() |
| function | aux.NormalSetTarget() |
| function | aux.NormalSummonCondition1() |
| function | aux.NormalSummonCondition2() |
|  |
| bool | aux.NOT(function f)(...) | This is equivalent to not f(...), if used as filter checking, (...) is automatically applied |
| nil | aux.NULL() | Function that returns nil |
| bool | aux.nvfilter(Card c) | Filter check "not affected by Necrovalley" |
| bool | aux.nzatk(Card c) | Function deprecated since version 40.0.0. Use "Card.HasNonZeroAttack" instead |
| bool | aux.nzdef(Card c) | Function deprecated since version 40.0.0. Use "Card.HasNonZeroDefense" instead |
| bool | aux.OR(...)(...) | First (...) is a list of functions which will be used to check the parameters in the second set of (...), separated with "or". The second set of (...) is applied automatically when used as a filter. |
| table element | aux.ParamsFromTable(table t,  key,  ...) |
| function | aux.PendulumProcedure(c) |
| bool | aux.penlimit(Effect e,  Effect se,  int sp,  int st) | SPSUMMON condition "Must be Pendulum Summoned" |
| function | aux.PersistentFilter(Effect e,  Card c) |
| function | aux.PersistentTarget(Effect e,  Card c) |
| bool | aux.PersistentTargetFilter(Effect e,  Card c) | Default filter for checking if it's targeted by the Persistent Trap. |
| function | aux.PersistentTgCon(Effect e,  Card c) |
| function | aux.PersistentTgOp(Effect e,  Card c) |
| bool | Xyz.ProcCancellable | Used with the Xyz Summon procedure and a fw Xyz monsters. Defined as false. |
| table | aux.PropertyTableFilter(function f,  ...) |
| void | aux.PuzzleOp(Effect e,  int tp) | Used by aux.BeginPuzzle(), sets the first turn player's LP to 0 |
| bool | aux.qlifilter(Effect e,  Effect te) | Default filter used with "Qli" monsters for: "Unaffected by activated monster effects whose original Rank/Level is lower than this card's Level" |
| void | aux.RegisterClientHint(Card c,  int property_code,  int reg.player,  int s,  int o,  str,  int reset_code,  int ct) | Auxiliary function to simplify registering EFFECT_FLAG_CLIENT_HINT to players. (Card c) is card that creates the hint message,  (int property_code) are additional properties like EFFECT_FLAG_OATH (PLAYER_TARGET and CLIENT_HINT are the flags registered by default). (int reg. player) is the player that is registering the hint, to himself (int s) and/or the opponent (int o), with a description called from a string defined in (str). Additional resets, other than the default RESET_PHASE+PHASE_END, can be passed in (int reset_code) and its reset count (int ct). |
| bool | aux.ReincarnationCheckTarget(Effect e,  Card c) | Auxiliary function for "Salamangreat" Reincarnation procedure. Returns if (card c) is either a Fusion, Ritual or a Link. |
| function | aux.ReincarnationCheckValue(Effect e,  Card c) | Auxiliary function for "Salamangreat" Reincarnation procedure. Registers CARD_SALAMANGREAT_SANCTUARY as flag  to (card c) if it is either a Link, Fusion or Ritual and has among its materials a card with the same ID as (card c). |
| bool | aux.ReincarnationRitualFilter(Effect e,  Card c) | Auxiliary filter for "Salamangreat" Reincarnation procedure to handle the rituals. |
| bool | aux.RelCheckGoal(int player,  group sg,  group exg,  group mustg,  int count,  int min,  function specialchk,  ...) |
| bool | aux.RelCheckRecursive(card c,  int player,  group sg,  group mg,  group exg,  group mustg,  int count,  int min,  function specialchk,  ...) |
| bool | aux.ReleaseCheckMMZ(group sg,  int player) |
| bool | aux.ReleaseCheckSingleUse(group sg,  int player,  group exg) |
| bool | aux.ReleaseCheckTarget(group sg,  int player,  group exg,  group dg) |
| bool | aux.ReleaseCostFilter(card c,  function f, ...) |
| bool | aux.ReleaseNonSumCheck(card c,  int player,  effect e) | Auxiliary function called by "Duel.CheckReleaseGroupSummon" and Duel.SelectReleaseGroupSummon". |
| bool\|void | aux.RemainFieldCost(Effect e,  int tp,  Group\|nil eg,  int ep,  int ev,  Effect re,  int r,  int rp,  int chk) | Costs that is used in cards that stay on the field if they finish resolving. (e.g. Kunai with Chain,  Different Dimension Burial) |
| void | aux.RemainFieldDisabled(Effect e,  int tp,  Group\|nil eg,  int ep,  int ev,  Effect re,  int r,  int rp) | to be added |
| void | aux.ResetEffects(Group g,  int eff) | Resets all effects with code (int eff) in a group of cards defined (Group g). |
| function | aux.RitualCheckAdditionalLevel() |
| function | aux.RitualProcedure() |
| function | aux.SecurityForceCost() |
| function | aux.SecurityTarget() |
| bool | aux.ritlimit(Effect e,  Effect se,  int sp,  int st) | SPSUMMON condition "Must be Ritual Summoned" |
| int/nil | aux.SelectEffect(int player,  ..) | Function deprecated since version 40.0.0. Use "Duel.SelectEffect" instead |
| bool\|Group | aux.SelectUnselectGroup(Group g,  Effect e,  int tp,  int minc = 1,  int maxc = 99,  function\|nil rescon,  int chk,  int seltp,  int hintmsg,  function\|nil cancelcon,  function\|nil breakcon,  bool cancelable) | Recursion checking and selection. (Group g) is the group to check and choose from, with a minimum (int minc) that defaults to 1 if set to nil and maximum (int maxc) that defaults to 99 if set to nil. (function rescon) is the condition to check which is needed fulfill. (int chk) is set to 0 to check and 1 to select. (int seltp) is the selecting player. (int hintmsg) is the HINTMSG that will be displayed on selection. (function cancelcon) is the condition when fulfilled allows you to end selection. (function breakcon) when fulfilled ends the selection automatically. |
| bool\|Group | aux.SelectUnselecLoop(...) |
| function | aux.selfreleasecost(...) | Auxiliary function that can be used as the cost function for effects that have as cost "You can tribute this card". |
| function | aux.seqmovcon(e, tp, eg, ep, ev, re, r, rp) | Condition for effects that make the monster change its current sequence/column. |
| function | aux.seqmovop(e, tp, eg, ep, ev, re, r, rp) | Operation for effects that make the monster change its current sequence/column. |
| function | aux.seqmovtg(e, tp, eg, ep, ev, re, r, rp) |
| function | aux.seqmovtgop(e, tp, eg, ep, ev, re, r, rp) |
| function | aux.SetVrainsSkillOp(...) |
| effect | aux.SetSkillOp(coverNum, drawless, skillcon, skillop, countlimit, efftype) |
| void | aux.SetUnionState(card c) | See proc_union.lua. |
| bool | aux.SpElimFilter(Card c,  bool mustbefaceup,  bool includemzone) | Spirit Elimination check to (Card c). It checks if controller is affected by Spirit Elimination. If so, it will only filter in the Monster Zone, otherwise in Graveyard. (bool mustbefaceup) means the filter is not generic (e.g. Banish 1 Dragon-Type monster) opposed to banish 1 monster. (bool includemzone) when set to true will check LOCATION_MZONE by default as opposed to filtering LOCATION_MZONE and LOCATION_GRAVE depending on affected by Spirit Elimination. |
| function | aux.SpiritReturnCondition(...) |
| void | aux.SpiritReturnOperation(e, tp, eg, ep, ev, re, r, rp) | Function deprecated since version 40.0.0. Use "Spirit.SummonRegister" |
| void | aux.SpiritReturnReg(e, tp, eg, ep, ev, re, r, rp) | Function deprecated since version 40.0.0. Use "Spirit.SummonRegister" |
| void | aux.SpiritReturnTarget(...) |
| void | aux.StardustCost(...) |
| int | aux.Stringid(int code,  int n) | Returns the description code using the database entry's code (int code) and from the nth position (int position) which can be 0-15 corresponding to the str in the database which are from str1 to str16 |
| function | aux.SynchroProcedure(...) |
| bool | aux.sumlimit(int sumtype) | helper function called by the various auxiliary function used as special summon conditions |
| bool | aux.summonproc(...) |
| void | aux.sumreg(Effect e,  int tp,  Group eg,  int ep,  int ev,  Effect re,  int r,  int rp) | Used as SetOperation which registers a FlagEffect to cards in the event group with the same OriginalCode as itself |
| bool | aux.synlimit(Effect e,  Effect se,  int sp,  int st) | SPSUMMON condition "Must be Synchro Summoned" |
| table | aux.tableAND(...) |
| table | aux.tableOR(...) |
| bool | aux.TargetBoolFunction(function f,  ...) | Used in SetTarget filters (with parameters (e,  c)) to check a function and its (...) parameters |
| bool | aux.TargetEqualFunction(function f,  int value,  ...) | Used in SetTarget filters (with parameters (e,  c)) to check a function and its (...) parameters is equal to the inputted (int value). |
| bool | aux.TatsunecroFilter(Card c) | Returns is Card c has "3096468" as flag effect. Used in the Synchro summon procedure |
| bool | aux.tgoval(Effect e,  Effect re,  int rp) | filter for EFFECT_CANNOT_BE_EFFECT_TARGET, "cannot be targeted by your opponent's card effects" |
| void | aux.thoeSend(card c) | Sends (card c) to the grave. Function added to be used with aux.ToHandOrElse |
| void | aux.ToHandOrElse(card c\|group tc,  int player,  [function check,  function oper,  str], ...) | Makes (int player) either add (card c\|group tg) to hand or perform a secondary action. If the optional parameters are not provided, the default secondary action is to send the card or group to the GY. If  the provided (function check) is true (for all the cards in the group) , the secondary action, with string called from (str), will be the one defined in (function oper). |
| function | aux.UnionFilter(...) |
| function | aux.UnionLimit(...) |
| function | aux.UnionOperation(...) |
| function | aux.UnionReplace(...) |
| function | aux.UnionSumOperation(...) |
| function | aux.UnionSumTarget(...) |
| function | aux.UnionTarget(...) |
| bool | aux.TRUE() | Function that returns true. Can be used to return a whole group of cards in a certain location |
| void | aux.ValuesReset() |
| function | aux.WelcomeLabrynthTrapDestroyOperation(...) |
| function | aux.WitchcrafterDiscardAndReleaseCost(...) |
| void | aux.WitchcrafterDiscardCost(f,  int minc,  int maxc) | Auxiliary function for the discard cost of "Witchcrafter" monsters. Performs the actual discard part, considering a minimum (minc) and maximum (maxc) amount of cards to discard. It also handles cards with EFFECT_WITCHCRAFTER_REPLACE, setting the reason for REASON_COST for those, or REASON_COST+REASON_DISCARD if a card is sent from hand instead. |
| bool | aux.xyzlimit(Effect e,  Effect se,  int sp,  int st) | SPSUMMON condition "Must be Xyz Summoned" |
| function | aux.XyzProcedure(...) | to be added |
| function | aux.ZWEquipLimit(...) | to be added |
| int | aux.ZoneCheckFunc(card c,  int player,  int zone) | Auxiliary function called by "Duel.CheckReleaseGroupSummon" and Duel.SelectReleaseGroupSummon". |
| bool | aux.zptcon(filter) | Used as condition for effects that check "if a [filter] monster is Special Summoned to a zone this card points to". Includes non-trivial handling of self-destructing Burning Abyss monsters. tp is passed to check control. |
| bool | aux.zptfilter(filter) | Used as filter for effects that check "if [filter] monster is Special Summoned to a zone this card points to". Also includes non-trivial handling of self-destructing effects of "Burning Abyss" monsters. |
| group | aux.zptgroup(group eg,  function filter,  card c,  int tp) | Filter for "If a (function filter) monster is Special Summoned to a zone this card points to". Includes non-trivial handling of self-destructing Burning Abyss monsters |
| bool | aux.zptgroupcon(group eg,  function filter,  card c,  int tp) |
| effect | aux.RemoveUntil(Card\|Group cg,  int\|nil pos,  int reason,  int phase,  effect e,  int player,  function oper,  function\|nil cond) | Banishes card(s) and applies an operation to them in a given phase (usually return them to their current location). (Card\|Group cg) are the cards to banish, (int\|nil pos) is the cards' position when banished (passing nil will use their current position),  (int reason) is the reason for banishing (for example,  REASON_COST,  REASON_EFFECT) and (int phase) is the phase when (function oper) will be applied to the banished cards. (effect e) is the effect performing the banishment, while (int tp) is the player performing the banishment, and that will later execute (function oper), a function with the signature (rg, e, tp, eg, ep, ev, re, r, rp), where `rg` is the group of cards that can be returned. (function\|nil con) is an additional condition function with the signature (rg, e, tp, eg, ep, ev, re, r, rp). By default, `rg` is automatically checked if it's not empty. |