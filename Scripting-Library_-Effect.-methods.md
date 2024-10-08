return type | function name | description
-- | -- | --
| bool | Effect.CheckCountLimit(int tp) | Checks if the effect can still be used by tp or the player has finished its uses. |
| Effect | Effect.Clone(Effect e) | Clone an effect object (Effect e), duplicating all except register status and assigned labels. |
| Effect | Effect.CreateEffect(Card c) | Creates a new effect object with a card (Card c) as its owner. |
| Effect | Effect.CreateMysteruneQPEffect(c, id, [uniquecat, uniquetg, uniqueop, rmcount, uniqueprop, uniquecode]) |
| Effect | Effect.CreateVernalizerSPEffect(c, id, desc, uniquecat, uniquetg, uniqueop) |
| Effect | Effect.FromLuaRef(int ref) | Returns a Effect object from a given lua reference. The function errors out if the reference is invalid or does not refer to a Effect object. |
| int | Effect.GetActivateLocation(Effect e) | Gets (Effect e)'s location when it was activated. |
| int | Effect.GetActivateSequence(Effect e) | Gets (Effect e)'s sequence when it was activated. |
| int | Effect.GetActiveType(Effect e) | Gets an effect's (Effect e) card type of activation effect. Activation type is often the effect handler's card type, or the owner's if not attached to a card. Exception for Pendulum scale activation (would return TYPE_SPELL+TYPE_PENDULUM). |
| int | Effect.GetCategory(Effect e) | Gets an effect's (Effect e) category |
| int | Effect.GetCode(Effect e) | Gets (Effect e)'s code |
| function | Effect.GetCondition(Effect e) | Gets an effect's (Effect e) condition function, returns nil if no function was set |
| function | Effect.GetCost(Effect e) | Gets an effect's (Effect e) cost function, returns nil if no function was set |
| int, int, int, int, int, int | Effect.GetCountLimit(Effect e) | Get (Effect e)'s: remaining usages maximum count limit its hopt identifier (e.g. detect "The effect of "card name" can only be used once per turn,  almost always you'd want to use the card's own id to be sure it's unique.) its count flags (e.g. EFFECT_COUNT_CODE_DUEL to indicate an effect that is n times per duel) its hopt index (that is used to handle cards that have multiple hopt effects where each can be used once,  the first will have an index of 0,  the second an index of 1,  etc, ) |
| int | Effect.GetDescription(Effect e) | Gets (Effect e)'s assigned description string id |
| int | Effect.GetFieldID(Effect e) | Gets a unique ID representing a certain instance of an effect. |
| Card | Effect.GetHandler(Effect e) | Gets an effect's (Effect e) card handler (that being the card on which the effect is registered on), if the effect is not attached to a card (i.e. registered to player) it returns its owner. |
| int | Effect.GetHandlerPlayer(Effect e) | Returns the controller of the handler of the effect (Effect e). If the effect is registered to a player, it returns the player it's registered to instead. |
| int, int | Effect.GetHintTiming(Effect e) | Returns a pair of integers with the hint timings set to Effect e. The first return value are the timings for the first player's turn and the second return are the hint timings set to the opponent |
| int,... | Effect.GetLabel(Effect e) | Gets an effect's (Effect e) internal labels. If no labels are present, it will return 0. |
| Card\|Group\|Effect\|table | Effect.GetLabelObject(Effect e) | Gets an effect's (Effect e) internal label object |
| int | Effect.GetLuaRef(Effect e) | Returns an integer representing the internal value used by lua to access the Effect e. |
| function | Effect.GetOperation(Effect e) | Gets an effect's (Effect e) operation function, returns nil if no function was set |
| Card | Effect.GetOwner(Effect e) | Gets an effect's (Effect e) card owner. If the effect was created as GlobalEffect then it returns an internal card object that shouldn't be used by the scripts. |
| int | Effect.GetOwnerPlayer(Effect e) | Returns the controller of the owner of the effect (Effect e). If the effect is registered to a player, it returns the player it's registered to instead. If the owner was changed by Effect.SetOwnerPlayer, then it will return the value set by that function. |
| int,int | Effect.GetProperty(Effect e) | Gets an effect's (Effect e) property |
| int | Effect.GetRange(Effect e) | Gets an effect's range (the value defined in SetRange) |
| int, int | Effect.GetReset(Effect e) | Gets (Effect e)'s reset flags and reset count. |
| function | Effect.GetTarget(Effect e) | Gets an effect's (Effect e) target function, returns nil if no function was set |
| int, int | Effect.GetTargetRange(Effect e) | Returns the pair of values set in (Effect e)'s SetTargetRange. |
| int | Effect.GetType(Effect e) | Gets an effect's (Effect e) type |
| function\|int | Effect.GetValue(Effect e) | Gets an effect's (Effect e) value or value function, returns nil if no function was set |
| Effect | Effect.GlobalEffect() | Creates a new effect object, not owned by any specific card. |
| bool | Effect.IsActivatable(Effect e,  int player[,  bool ignore_location=false,  bool ignore_target=false]) | Checks if an effect (Effect e) can be activated by a player (int player). If ignore location is true, the handler of the effect is not checked to be in a valid location for that effect to be activated. If ignore target is true, then the target function is not executed to check if the effect can be activated. |
| bool | Effect.IsActivated(Effect e) | Returns if an effect (Effect e) is an activated effect. Effectively, this checks if the effect has any of the following types: EFFECT_TYPE_ACTIVATE, EFFECT_TYPE_FLIP, EFFECT_TYPE_IGNITION, EFFECT_TYPE_TRIGGER_O, EFFECT_TYPE_QUICK_O, EFFECT_TYPE_TRIGGER_F or EFFECT_TYPE_QUICK_F |
| bool | Effect.IsActiveType(Effect e,  int type) | Compares (with OR) an effect's (Effect e) card type of activation effect with supplied type (int type). Activation type is often the handler's card type, or the owner's if not attached to a card. Exception for Pendulum scale activation (would return TYPE_SPELL+TYPE_PENDULUM). |
| bool | Effect.IsDeleted(Effect e) | Returns if the Effect object got internally deleted and remained as dangling reference inside the lua state. |
| bool | Effect.IsHasCategory(Effect e,  int cate) | Returns true if the effect (Effect e) has any category listed in (int cate), otherwise returns false |
| bool | Effect.IsHasProperty(Effect e,  int prop1[,  int prop2]) | Returns true if the effect (Effect e) has any property listed in (int prop1) or (int prop2), otherwise returns false |
| bool | Effect.IsHasType(Effect e,  int type) | Returns true if the effect (Effect e) has any type listed in (int type), otherwise returns false |
| bool | Effect.IsMonsterEffect(Effect e) | Returns if (Effect e) is a monster effect |
| bool | Effect.IsSpellEffect(Effect e) | Returns if (Effect e) is a Spell effect |
| bool | Effect.IsSpellTrapEffect(Effect e) | Returns if (Effect e) is an effect from a Spell or Trap card |
| bool | Effect.IsTrapEffect(Effect e) | Returns if (Effect e) is a Trap effect |
| void | Effect.Reset(Effect e) | Reset an effect (Effect e) and makes it collectible by the garbage collector. Even if the effect seems to be usable it **SHOULD NOT** be used in other places after calling this function. |
| void | Effect.SetAbsoluteRange(Effect e,  int playerid,  int s_range,  int o_range) | Sets an effect's (Effect e) target range in perspective of the supplied player (int playerid), s_range denotes the supplied player's range and o_range denotes the opponent's. |
| void | Effect.SetCategory(Effect e,  int cate) | Sets an effect's (Effect e) category. Refer to constant.lua for valid categories. |
| void | Effect.SetCode(Effect e,  int code) | Sets an effect's (Effect e) code. Refer to constant.lua and card scripts that has been already there for valid codes (or ask someone). |
| void | Effect.SetCondition(Effect e,  function con_func) | Sets (Effect e)'s condition function |
| void | Effect.SetCost(Effect e,  function cost_func) | Sets (Effect e)'s cost function |
| void | Effect.SetCountLimit(Effect e,  int count[,  int code=0\|{ int code,  int hopt_index },  int flag = 0]) | Sets an effect's (Effect e) use limit per turn to (int count). If "code" is supplied, then it would count toward all effects with the same count limit code (i.e. Hard OPT). If a card has multiple HOPT effects on it, then instead of passing "code" as integer, a table can be used as parameter, the first element of this table will be still "code", the second element will instead be the HOPT index of that effect, this is done to prevent the passed code from clashing with other HOPT effects. (e.g. calling "e:SetCountLimit(1, 1234)" is the same as calling "e:SetCountLimit(1, {1234, 0})". The flag parameter consists of the "EFFECT_COUNT_CODE_XXX" constants. |
| void | Effect.SetDescription(Effect e,  int desc) | Sets an effect's (Effect e) description string id with (int desc), you can use aux.Stringid() to reference strings in your database, use the "HINTMSG_" constants, or directly put the string number you want (it's not always recommended,  but it is possible if you need to use a system string that is defined in the strings.conf file but doesn't have an equivalent "HINTMSG_" constant). |
| void | Effect.SetHintTiming(Effect e,  int s_time[,  int o_time=s_time]) | Sets (Effect e)'s client usage hint timing. This is the timing where the game will prompt the player to activate that effect (in addition to regular timings) |
| void | Effect.SetLabel(Effect e,  int label[,  int ...]) | Sets an effect's (Effect e) internal labels to the integers passed as parameter (Multiple values and tables can used). This operation replaces previously set labels. |
| void | Effect.SetLabelObject(Effect e,  Card\|Group\|Effect\|table labelobject) | Sets an effect's (Effect e) internal label object to label object. This operation replaces a previously stored label object. |
| void | Effect.SetOperation(Effect e,  function op_func) | Sets (Effect e)'s operation function. |
| void | Effect.SetOwnerPlayer(Effect e,  int player) | Sets (int player) as the (Effect e)'s owner player. |
| void | Effect.SetProperty(Effect e,  int prop1[,  int prop2]) | Sets an effect's (Effect e) property. Refer to constant.lua and card scripts that has been already there for valid properties (or ask someone). |
| void | Effect.SetRange(Effect e,  int range) | Sets an effect's (Effect e) effective range (int range) i.e. LOCATION_MZONE. The location is the effect handler's location. |
| void | Effect.SetReset(Effect e,  int reset_flag[,  int reset_count=1]) | Sets the timing that the effect (Effect e) would be erased (with reset_flag) |
| void | Effect.SetTarget(Effect e,  function targ_func) | Sets (Effect e)'s target function. In a activate effects, the target function is the function used to do the activation legality check and to execute steps that must be done during the activation (e.g. targetting cards,  declaring names or numbers,  etc). |
| void | Effect.SetTargetRange(Effect e,  int s_range,  int o_range) | Sets (Effect e)'s target range, s_range denotes the effect's handler player's range and o_range denotes the opponent's. If the effect has "EFFECT_FLAG_PLAYER_TARGET" as property, then here 1 as "s_range" would mean it affect the handler and 0 would mean it doesn't, and "o_range" would refer to the opponent of the handler. |
| void | Effect.SetType(Effect e,  int type) | Sets an effect's (Effect e) type. constant.lua contains the list with all valid effect types but other cards' scripts can be used as reference |
| void | Effect.SetValue(Effect e,  function\|int\|bool val) | Sets (Effect e)'s value, or value function |
| void | Effect.UseCountLimit(Effect e,  int p [, int count=1,  bool oath_only=false]) | Decreases the remaining usages of the effect by the player "p" by "count", if "oath_only" is true, the function will do nothing unless the effect is an OATH effect. |
