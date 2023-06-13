## Debug functions
| return type | function | description |
| --- | --- | --- |
| Card | Debug.AddCard(int code,  int owner,  int player,  int location,  int seq,  int pos[,  bool proc=false]) | Adds a card of (int code), owned by (int owner) and under (int player)'s control, to (int seq) of (int location) in (int pos) position. If (bool proc) is true, it will be treated as properly summoned for the purposes of revive limits. |
| void | Debug.Message(any msg) | Sends (any msg) as a script error to the logs |
| void | Debug.PreAddCounter(Card c,  int counter_type,  int count) | Adds (int count) counters of (int counter_type) to (Card c) |
| bool | Debug.PreEquip(Card equip_card,  Card target) | Equips (Card equip_card) to (Card target) |
| void | Debug.PreSetTarget(Card c,  Card target) | Sets (Card c)'s target card to (Card target) (e.g. Call of the Haunted) |
| void | Debug.PreSummon(Card c,  int sum_type[,  int sum_location=0,  int summon_sequence=0,  bool summon_pzone=false]) | Treats (Card c) as if it was summoned by (int sum_type). If (int sum_location) is provided, treats it as summoned from that location. If (int sum_sequence) is provided, treats it as summoned in that sequence. I(bool summon_pzone) is required to be true if the card is to be considered to be summoned from the Pendulum Zone. |
| void | Debug.ReloadFieldBegin(int flag,  int rule[,  bool ignore_rule=false]) | Begins loading the field for a puzzle, with DUEL_ constants in (int flag) under Master Rule (int rule). If (bool ignore_rule) is set to true, then the master rules from (int flag) are ignored and the field is constructed only from the duel flags provided |
| void | Debug.ReloadFieldEnd() | Stops loading the field for a puzzle. |
| void | Debug.SetAIName(string name) | Sets the name of the AI to (string name) |
| void | Debug.SetPlayerInfo(int playerid,  int lp,  int startcount,  int drawcount) | Sets (int playerid) to have (int lp) LP, start with a (in startct) card hand, and draw (int drawcount) during the Draw Phase. |
| void | Debug.ShowHint(string msg) | Displays a message (string msg) on the screen. |

## Fusion-related functions
| return type | function | description |
| --- | --- | --- |
| void | Fusion.AddContactProc(Card c,  function group,  function op,  function sumcon,  function\|nil condition,  int sumtype = 0,  int\|nil desc) | Adds a Contact Fusion Procedure to a Fusion monster which is a Summoning Procedure without having to use "Polymerization". (function group) is a function with (int tp) parameter which returns a Group of usable materials. (function op) is the operation that will be applied to the selected materials. (function sumcon) adds a limitation on a Fusion monster which applies to EFFECT_SPSUMMON_CONDITION. (function condition) is an additional condition to check. (int sumtype) is the Summon Type of the Contact Fusion, which defaults to 0. (int desc) is the description of the Summoning Procedure when selecting it. |
| void | Fusion.AddProcCode2(c, code1, code2, sub, insf) | Recipe for Fusion monsters that have code1 + code2 as materials. Example: Beast Machine King Barbaros Ür (Manga) |
| void | Fusion.AddProcCode2FunRep(c, code1, code2, f, minc, maxc, sub, insf) | Fusion monster, name + name + condition * minc to maxc |
| void | Fusion.AddProcCode3(c, code1, code2, code3, sub, insf) | Recipe for Fusion monsters that have code1+ code2 + code3 as materials. Not used by any cards. |
| void | Fusion.AddProcCode4(c, code1, code2, code3, code4, sub, insf) | Recipe for Fusion monsters that have code1+ code2 + code3 + code4 as materials. Not used by any cards. |
| void | Fusion.AddProcCodeFun(c, code1, f, cc, sub, insf) | Fusion monster, name + condition * n |
| void | Fusion.AddProcCodeFunRep(c, code1, f, minc, maxc, sub, insf) | Fusion monster, name + condition * minc to maxc |
| void | Fusion.AddProcCodeRep(c,  code1,  n,  sub,  insf) | Recipe for Fusion monsters that have n "code1" cards as material. Not directly called by any card. |
| void | Fusion.AddProcCodeRep2(c, code1, minc, maxc, sub, insf) | Fusion monster, name * minc to maxc. not used by any card |
| void | Fusion.AddProcFun2(c, f1, f2, insf) | Fusion monster, condition + condition |
| void | Fusion.AddProcFunFun(c, f1, f2, cc, insf) | Fusion monster, condition1 + condition2 * n |
| void | Fusion.AddProcFunFunRep(c, f1, f2, minc, maxc, insf) | Fusion monster, condition1 + condition2 * minc to maxc |
| void | Fusion.AddProcFunRep(c, f, cc, insf) | Fusion monster, condition * n |
| void | Fusion.AddProcFunRep2(c, f, minc, maxc, insf) | Fusion monster, condition * minc to maxc |
| void | Fusion.AddProcMix(Card c,  bool sub,  bool insf,  int\|function ...) | Adds a Fusion Procedure where (bool sub) is a check if Fusion Substitutes are allowed. (bool insf) is a check if using no materials are allowed (e.g. Instant Fusion). (int\|function ...) is a list of any number of codes/conditions as Fusion Materials. Member function from the Fusion namespace. Definition available in proc_fusion.lua. |
| void | Fusion.AddProcMixN(Card c,  bool sub,  bool insf,  int\|function,  int ...) | Adds a Fusion Procedure where (bool sub) is a check if Fusion Substitutes are allowed. (bool insf) is a check if using no materials are allowed (e.g. Instant Fusion). (int\|function ...) is a list of any number of codes/conditions as Fusion Materials, by pairs wherein the first value is int/function which is the code or condition, and the second value is an int which corresponds to the number of fixed materials. |
| void | Fusion.AddProcMixRep(Card c,  bool sub,  bool insf,  function fun1,  int minc,  int maxc,  int\|function ...) | Adds a Fusion Procedure where (bool sub) is a check if Fusion Substitutes are allowed. (bool insf) is a check if using no materials are allowed (e.g. Instant Fusion). (function fun1) is a condition for a Fusion Material with a minimum (int minc) and maximum (int maxc) and (int\|function ...) is a list of any number of codes/conditions as Fusion Materials. |
| void | Fusion.AddProcMixRepUnfix(c, sub, insf, ...) |
| void | Fusion.AddShaddolProcMix(Card c,  bool insf,  function f,  int att) | Adds a Fusion Procedure where (bool insf) is a check if using no materials are allowed (e.g. Instant Fusion) and accepts 1 condition (function f) and 1 Attribute (int att). |
| void | Fusion.BanishMaterial(e, tc, tp, group sg) | Banishes (group sg), face-up, with REASON_EFFECT+REASON_MATERIAL+REASON_FUSION. Then clears the group sg. Used by the Fusion Summon procedure. |
| nil\|function | Fusion.CheckAdditional | A variable used temporarily to add further checks (e.g. only up to 2 materials from the Extra Deck: Odd-Eyes Fusion) |
| nil\|int | Fusion.CheckExact | A variable used temporarily to limit the usable materials' number |
| bool | Fusion.CheckWithHandler(fun, ...) | Used by the Fusion Summon procedure. |
| effect | Fusion.CreateSummonEff(Card c,  function fusfilter,  function matfilter,  function extrafil,  function extraop,  Group\|Card gc,  function stage2,  int exactcount,  int value,  int location,  int chkf,  string desc,  function preselect,  bool nosummoncheck,  function extratg,  int mincount,  int maxcount,  int sumpos) | Function that generates a Fusion Summon effect, called from the Fusion Summon Procedure defined in "proc_fusion.lua" and "proc_fusion2.lua". By default it's usable for Spells/Traps; usage in monsters requires changing type and code afterwards. [Card c]: card that uses the effect [fusfilter]: filter for the monster to be Fusion Summoned [matfilter]: filter for the default materials returned by GetFusionMaterial [extrafil]: function that returns a group of extra cards that can be used as materials, and as second optional return an additional filter function [extraop]: function to perform a different operation on the materials [gc]: mandatory card or function returning a group to be used (Soprano the Melodious Songtress) [stage2]: function called after the summon (Shaddol Ruq,  Instant Fusion) [exactcount]: exact number of materials that must be used (Ostinato) [location]: the monster's summoning location (LOCATION_EXTRA by default) [chkf]: FUSPROC flags for the Fusion Summon [desc]: string for the effect's description [preselect]: function that is executed after selecting the monster but before performing the Fusion Summon (Clock Lizard) [nosummoncheck]: boolean, if true then the procedure won't check if the monster can be Special Summoned in its current state (Clock Lizard) [extratg]: additional target function that will be executed when activating the effect (Miracle Fusion) [mincount]: min number of materials [maxcount]: max number of materials [sumpos]: the monster's summoning position (POS_FACEUP by default) |
| bool | Fusion.ForcedHandler(effect e) | Used by the Fusion Summon procedure. |
| bool | Fusion.InHandMat(filter, ...) | Used by the Fusion Summon procedure. |
| bool | Fusion.IsMonsterFilter(function f, ...) | Used by the Fusion Summon procedure. |
| bool | Fusion.OnFieldMat(filter, ...) | Used by the Fusion Summon procedure. |
| void | Fusion.ShuffleMaterial(e, tc, tp, group sg) | Sends (group sg) to the Deck with REASON_EFFECT+REASON_MATERIAL+REASON_FUSION. Then clears the group sg. Used by the Fusion Summon procedure. |
| effect | Fusion.SummonEffOP(...) |
| effect | Fusion.SummonEffTG(...) |


## Gemini-related functions
| return type | function | description |
| --- | --- | --- |
| void | Gemini.AddProcedure(Card c) | Applies all the effects necessary for a Gemini monster to be used as one to (Card c). |
| bool | Gemini.EffectStatusCondition(Effect e) | Checks if an effect's handler (corresponding card) is a Gemini monster applying its effect. |
| bool | Gemini.NormalStatusCondition(Effect e) | Checks if a monster is face-up and is not a Gemini monster or has not been Normal Summoned on the field. |

## Link-related functions
| return type | function | description |
| --- | --- | --- |
| void | Link.AddProcedure(Card c,  function\|nil f,  int min,  int max = c:GetLink(),  function\|nil specialchk,  int desc) | Adds a Link Procedure where (function f) is the required material with a minimum (int min) and maximum (int max) where (function specialchk) is an additional check after obtaining all materials (e.g. Akashic Magician) and (int desc) is the description to its Link Summoning Procedure, |

## Pendulum-related functions
| return type | function | description |
| --- | --- | --- |
| void | Pendulum.AddProcedure(Card c[,  bool reg=true,  int\|nil desc]) | Applies to (Card c) all the effects necessary for a Pendulum card to be used as one. Setting (bool reg) to false will not register the activation effect, which is used in cards that cannot be activated since you don't have them in your hand (e.g. Xyz/Pendulums). (int desc) is an optional parameter adding a description that will be called when you try to activate in in the Pendulum Zone. |

## Ritual-related functions
| return type | function | description |
| --- | --- | --- |
| effect | Ritual.AddProc(card c, int _type,  function filter,  int lv,  string desc,  function extrafil,  function extraop,  function matfilter,  function stage2,  int location, group forcedselection,  function customoperation, group specificmatfilter) | Underlying function called by the Ritual Summon Procedure. Should not be directly called. Instead, use the "Ritual.AddProc" family of functions (or Ritual.CreateProc) to define an effect that performs a Ritual Summon. |
| effect | Ritual.AddProcCode(card c,  int ritproctyp,  int lv,  string desc,  ...) | Underlying function called by Ritual.AddProcGreaterCode and Ritual.AddProcEqualCode. Should not be directly called as the previously mentioned functions already call it with the correct ritproctyp |
| void | Ritual.AddProcEqual(Card c,  function filter,  int lv[,  string desc,  function extrafil,  function extraop,  matfilter,  function stage2,  int location,  forcedselection,  customoperation,  function specificmatfilter]) | Adds a Ritual Summoning activation, requiring Tributes that meet (function filter), and with levels exactly equal to the Ritual Monster's level or if (int lv) is provided, with level equal to that value. (int desc) is the description when activating the Ritual Spell. |
| void | Ritual.AddProcEqualCode(Card c,  int lv,  int desc,  [...]) | Adds a Ritual Summoning activation, requiring Tributes with any of the card names of code (int ...), and with levels exactly equal to the Ritual Monster's level or if (int lv) is provided, with level equal to that value. (int desc) is the description when activating the Ritual Spell when provided. |
| effect | Ritual.AddProcGreater(Card c,  function filter,  int lv,  string desc,  function extrafil,  function extraop,  function matfilter,  function stage2,  int location,  forcedselection,  function customoperation,  function specificmatfilter) | Adds a Ritual Summoning activation requiring Tributes that meet (function filter), and with levels equal to or greater than the Ritual Monster's level |
| void | Ritual.AddProcGreaterCode(Card c,  int lv,  string desc, ...) | Adds a Ritual Summoning activation requiring Tributes for a Ritual monster with any of the card names of code (int ...), and with levels equal to or greater than the Ritual Monster's level |
| effect | Ritual.AddWholeLevelTribute(card c,  function cond) | The current total level to match for the monster being summoned, to be used with monsters that can be used as whole tribute |
| effect | Ritual.CreateProc(card c, int _type,  function filter,  int lv,  string desc,  function extrafil,  function extraop,  function matfilter,  function stage2, int location, group forcedselection,  function customoperation,  function specificmatfilter) | Creates an effect that performs a Ritual Summon. c is the card generating the effect, int _type is either RITPROC_EQUAL or RITPROC_GREATER, function filter defines the monsters can be summoned, int lv is the level of the monster(s) that must be tributed (but can be a function like GetLevel/GetOriginalLevel,  a fixed level,  or nil,  in which case it defaults to to GetLevel), string desc is the description that will be used for that effect, function extrafil must return an extra group that can also be used as tributed, function extraop is a custom operation to perform on the tributes (shuffle into the deck,  banish, etc), function matfilter is ... . Supports named arguments for all parameters (See Revendread Evolution) |

## Spirit-related functions
| return type | function | description |
| --- | --- | --- |
| void | Spirit.AddProcedure(Card c,  int event1,  int ...) | Sets up EVENT triggers to (Card c) so it returns to the hand during that End Phase, requires a minimum of 1 (int event1) |
| void | Spirit.ReturnOperation(e, tp, eg, ep, ev, re, r, rp) | Auxiliary operation. Not directed used by cards. |
| void | Spirit.SummonRegister(e, tp, eg, ep, ev, re, r, rp) | Auxiliary function registration. Not used directly by card, only called by aux.EnableSpiritReturn |

## Synchro-related functions
| return type | function | description |
| --- | --- | --- |
| void | Synchro.AddDarkSynchroProcedure(Card c,  function f1,  function f2,  int plv,  int nlv,  function ...) | Adds a Synchro Procedure to (Card c) used by Dark Synchros where (function f1) is the first material, usually used by the non-Tuner and (function f2) as the Dark Tuner, whose Level to be subtracted from the first material. (int plv) is the target level when both materials are of positive value while (int nlv) is the target value if the first material is affected by Dark Wave. (int plv) defaults to the Synchro monster's level while (int nlv) defaults to the (int plv) if not supplied. (function ...) is the list of required materials during the Summon. |
| void | Synchro.AddMajesticProcedure(Card c,  function f1,  bool cbt1,  function f2,  bool cbt2,  function f3,  bool cbt3,  function ...) | Adds a Synchro Procedure to (Card c) used by Majestic Star Dragon where (function f1,  f2 and f3) are the required material and (bool cbt1,  cbt2 and cbt3) are a check if the respective material can be used as the Tuner in the Summon since rulings for Majestic Star/Red Dragon state that either or both Majestic Dragon (f1) and/or Stardust Dragon/Red Dragon Archfiend (f2) can be used as the Tuner, but the non-Tuner, for the case of using Phantom King Hydride (f3) cannot be treated as the Tuner for the Summon. You require a minimum of 1 among these 3 to be the Tuner. (function ...) is the list of required materials during the Summon. |
| void | Synchro.AddProcedure(Card c,  function f1,  int min1,  int max1,  function f2,  int min2,  int max2,  function sub1,  function sub2,  function req1,  int reqct1,  function req2,  int reqct2,  function reqm) | Adds a Synchro Procedure to (Card c) where (function f1) is the required Tuner, with a minimum (int min1) and maximum (int max1). (function f2) is the second material (which usually is a non-Tuner, with a minimum (int min2) and maximum (int max2). (function sub1) is a Tuner substitute (e.g. Nirvana High Paladin) while (function sub2) is a substitute to the second material(s). (function req1) are required Tuners to be used in that Summon, with a fixed number (int reqct1) on how many are needed to be used. (function req2) follows the same pattern but for the secondary material (e.g. Crystal Wing Synchro Dragon (Anime)). (function reqm) is the required material needed to be used in that Summon regardless if it's a Tuner or the second material (e.g. function overwrite by Blackwing - Gofu the Vague Shadow (Anime)). |
| bool | Synchro.NonTuner(function f,  a,  b,  c) | A filter used in a Synchro procedure when a material is supposed to be non-Tuner. It also has to satisfy condition of (function f) if provided with (a,  b,  c) parameters. |
| bool | Synchro.NonTunerCode(table params) | Used in the Synchro Summon procedure. |
| bool | Synchro.NonTunerEx(function f,  int val) | A filter used in a Synchro procedure when a material is supposed to be non-Tuner. It also has to satisfy condition of (function f) which has to be Card.IsRace, Card.IsAttribute or Card.IsType, or a function that would use any of these 3. Also, (int val) is a parameter that is used in checking the (function f). |
| int | Synchro.Send | a number representing how and where the Synchro Materials would be sent. 0 - (default) to grave, 1- to grave, returned from banished, 2 - banished face-up, 3 - banished face-down, 4 - sent to hand, 5, sent to Deck, 6 - destroyed. |
| string | type(var o) | Returns the type of "o" in a string format. This function has been overloaded to also support objects that are Card, Group or Effect |


## Xyz-related functions
| return type | function | description |
| --- | --- | --- |
| void | Xyz.AddProcedure(Card c,  function\|nil f,  int\|nil lv,  int ct,  f\|nil alterf,  int desc,  int maxct=ct,  function op,  bool mustbemat,  function exchk) | Adds an Xyz Procedure where (function f) is the required Xyz Material, and (int lv) is the required level, but it can also be nil if there is no required Level. (int ct) is the required number of materials. (function alterf) is the alternate material, e.g. Number C39: Utopia Ray. (int desc) is the description shown when attempting to Xyz Summon using (function alterf). (int maxct) is the maximum number of materials, which defaults to (int ct). (function op) is used by some monsters do something else in addition to using an Xyz Material (e.g. Digital Bug Corebage (detach 2 materials) or Number 99: Utopic Dragon (discard 1 "Rank-Up-Magic")). (bool mustbemat) is used if you can only use the listed materials during the Xyz Summon, this disallows Anime effects such as Orichalcum Chain (minus 1 material) or Triangle Evolution (triple material). (function exchk) is an additional check at the end of selecting materials (e.g. Number F0: Utopic Future (checks if the materials have the same Rank) |


## Assorted functions
| return type | function | description |
| --- | --- | --- |
| table, int | GetID() | Returns two values, a card object and its ID, used before the initial effect. |
| void | initial_effect(Card c) | The function that will be called for each card's initialization. |
| bool | setcodecondition(effect e) | Returns if the code of the handler of "effect e" is the same as the originalcoderule of the handler of "effect e" |


## bit-related functions
| return type | function | description |
| --- | --- | --- |
| int | bit.band(int a,  int b) | Does a bitwise AND operation between 2 integers. (Deprecated,  advised to use (int a)&(int b) instead.) |
| int | bit.bnot(int a) | Swaps the bits of an integer, 0 to 1 and 1 to 0. (Deprecated,  advised to use ~(int a) instead.) |
| int | bit.bor(int a,  int b) | Does a bitwise OR operation between 2 integers. (Deprecated,  advised to use (int a)\|(int b) instead.) |
| int | bit.bxor(int a,  int b) | Does a bitwise XOR operation between 2 integers. (Deprecated,  advised to use (int a)~(int b) instead.) |
| int | bit.extract(int a,  int b[,  int width=1]) | Returns the field of (int a) with a width |
| int | bit.lshift(int a,  int b) | Shifts all bits of an integer to the left by an amount (Deprecated,  advised to use (int a)<<(int b) instead.) |
| int | bit.replace(int a,  int b,  int c[,  int width=1]) | Returns a copy of (int a) with the field with a width changed to value (int b) |
| int | bit.rshift(int a,  int b) | Shift all bits of an integer to the right by an amount (Deprecated,  advised to use (int a)>>(int b) instead.) |

