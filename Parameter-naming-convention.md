## Parameter naming convention
The functions passed to Effect.SetCondition, Effect.SetCost, Effect.SetTarget and Effect.SetOperation usually receive the following parameters:
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
- chkc: used in effects that target cards. This parameter is required so cards that are able to redirect target (e.g. `Cairngorgon, Antiluminescent Knight`) can indentify the effect and what would be a correct new target.

### Commonly used variable names
While Lua allows you to name your variables in almost any way you want, reading scripts for official cards one can notice that there are commonly used variable names. Some and what they usually are used for are the following:
- `g`: group, `sg`: summon group, `dg`: destroy/discard group, `mg`: material group, `rg`: group of cards to be removed/banished or returned
- `tc`: target card, `tg`: target group
- `ct`: count, ammount, number of
- `ft`: (the number of) free zones
- `rc`: reason card (usually defined as `rc=re:GetHandler()`
Those are the usual meanings, but these variable names can be used in other contexts, and it's up to the user to use these names or not.

## Understanding a card script
Here's an example in Galactic Charity's script:
```lua
--銀河の施し
--Galactic Charity
local s,id=GetID()
function s.initial_effect(c)
	--Activate
	local e1=Effect.CreateEffect(c)
	e1:SetCategory(CATEGORY_DRAW)
	e1:SetType(EFFECT_TYPE_ACTIVATE)
	e1:SetCode(EVENT_FREE_CHAIN)
	e1:SetCountLimit(1,id,EFFECT_COUNT_CODE_OATH)
	e1:SetCondition(s.condition)
	e1:SetCost(s.cost)
	e1:SetTarget(s.target)
	e1:SetOperation(s.activate)
	c:RegisterEffect(e1)
end
s.listed_series={0x7b}
function s.cfilter(c)
	return c:IsFaceup() and c:IsSetCard(0x7b) and c:IsType(TYPE_XYZ)
end
function s.condition(e,tp,eg,ep,ev,re,r,rp)
	return Duel.IsExistingMatchingCard(s.cfilter,tp,LOCATION_MZONE,0,1,nil)
end
function s.cost(e,tp,eg,ep,ev,re,r,rp,chk)
	if chk==0 then return Duel.IsExistingMatchingCard(Card.IsDiscardable,tp,LOCATION_HAND,0,1,e:GetHandler()) end
	Duel.DiscardHand(tp,Card.IsDiscardable,1,1,REASON_COST+REASON_DISCARD,nil)
end
function s.target(e,tp,eg,ep,ev,re,r,rp,chk)
	if chk==0 then return Duel.IsPlayerCanDraw(tp,2) end
	Duel.SetTargetPlayer(tp)
	Duel.SetTargetParam(2)
	Duel.SetOperationInfo(0,CATEGORY_DRAW,nil,0,tp,2)
end
function s.activate(e,tp,eg,ep,ev,re,r,rp)
	local p,d=Duel.GetChainInfo(0,CHAININFO_TARGET_PLAYER,CHAININFO_TARGET_PARAM)
	Duel.Draw(p,d,REASON_EFFECT)
	if e:IsHasType(EFFECT_TYPE_ACTIVATE) then
		local e1=Effect.CreateEffect(e:GetHandler())
		e1:SetType(EFFECT_TYPE_FIELD)
		e1:SetCode(EFFECT_CHANGE_DAMAGE)
		e1:SetProperty(EFFECT_FLAG_PLAYER_TARGET+EFFECT_FLAG_CLIENT_HINT)
		e1:SetDescription(aux.Stringid(id,1))
		e1:SetTargetRange(0,1)
		e1:SetValue(s.val)
		e1:SetReset(RESET_PHASE+PHASE_END,1)
		Duel.RegisterEffect(e1,tp)
	end
end
function s.val(e,re,val,r,rp,rc)
	return math.floor(val/2)
end

```
To verify if the card can be activated, the game first checks the condition, the function called in `e1:SetCondition(s.condition)`.
`s.condition` is said to pass (meaning it returns `true`) if there is at least 1 card in player `tp`'s monster zone that matches the function `s.cfilter`.

Next the game checks for the cost. For that, the function called in `e1:SetCost(s.cost)` is executed. First `chk` is passed as `0` and the line
```lua
if chk==0 then return Duel.IsExistingMatchingCard(Card.IsDiscardable,tp,LOCATION_HAND,0,1,e:GetHandler()) end
```
is executed. In this test, if there is at least 1 card in player `tp`'s hand that can be discarded (except Galactic Charity itself, `e:GetHandler()`) the test is true and the game knows that the cost can be paid.

The following step is to verify the activation legality ("can the player resolve this effect?"). For this, the function defined in `e1:SetTarget(s.target)` is executed. For the activation legality the `chk` parameter here is passed as `0` again and the line
```lua
if chk==0 then return Duel.IsPlayerCanDraw(tp,2) end
```
is executed. Here, if player `tp` can draw 2 cards the test returns true and the game decides that the activation is legal.

After those steps, since condition, cost and activation legality are all true, the player can activate the card. When they do, the cost function is executed once again. Now the `chk` parameter is no longer `0`, so the first line in that function is not executed (because `if chk==0` is false) and instead the game runs the function that will make the player pay the cost (via `Duel.DiscardHand`).

After that, the `s.target` function is executed. The same situation with `chk` happens here: it is passed as `1` so the first line is no longer executed and the game instead only calls the functions Duel.SetTargetPlayer, Duel.SetTargetParam and Duel.SetOperationInfo.

Finally, when the effect resolves, the `s.activate` function is called, executing the actual effect of the card.

## Other insights
After the coments, in the script shown above you have:
- The definition of 2 local variables, `s` and `id`, that receive the return values from the `GetID` function: `local s,id=GetID()`

`s` will be a card object, and `id` will be an int containing that card's passcode.

- The declaration of the initial effect, with only 1 effect in this card `e1`
```lua
function s.initial_effect(c)
	--Activate
	local e1=Effect.CreateEffect(c)
	...
	c:RegisterEffect(e1)
end
```

In e1, you have:

- The category of the effect (defined via Effect.SetCategory): `e1:SetCategory(CATEGORY_DRAW)`

This tells the game what the effect includes and it is also used because there are cards that need to detect such categories like Ash Blossom & Joyous Spring (detecting CATEGORY_DRAW and CATEGORY_SEARCH).

- The code of the effect (defined via Effect.SetCode): `e1:SetCode(EVENT_FREE_CHAIN)`

This tells the game that the card can be activated in a open game state, when no chain is resolving (because Galactic Charity is a normal Spell). Other codes might include any event that the card needs to detect (for example EVENT_SUMMON_SUCCESS)
- The ammount of times the effect can be used (defined via Effect.SetCountLimit): `e1:SetCountLimit(1,id,EFFECT_COUNT_CODE_OATH)
`

This tells the game that `e1` can be **activated** once per turn, for the card that has `id` as passcode. If the EFFECT_COUNT_CODE_OATH flag was not there, then the player would be able to **use** the effect once per turn (in Yu-Gi-Oh, "use" counts any attempts to apply that effect, even the ones that were negated, while **activate** will only count the ones that didn't have their activation negated).
Examples: a count limit defined as `e1:SetCountLimit(1)`, which translates to "Once per turn" (per copy of the card);  `e1:SetCountLimit(1,id)` would be "You can only use this effect of CARD_NAME once per turn". `e1:SetCountLimit(1,id,EFFECT_COUNT_CODE_DUEL)` would be "You can only use this effect of CARD_NAME once per duel". 

- The condition to be able to activate the card or effect (defined via Effect.SetCondition): `e1:SetCondition(s.condition)`
- The cost function, that checks if the cost can be paid and also executes such cost (defined via Effect.SetCost): `e1:SetCost(s.cost)`
- The target function, that performs the activation legality check and also does the actions that must be done during the activation (defined via Effect.SetTarget): `e1:SetTarget(s.target)`
- The operation function, that executes all the steps that are done when the card or effect **resolves** (defined via Effect.SetOperation): `e1:SetOperation(s.activate)`

## WIP
### Commonly used variable names table
This is a non-exhaustive list of variables names and what they might represent.

type | variable name| description
-- | -- | --
string | any msg | An arbitrary string (can also include variables: 'Debug.Message("string1"..var1.."string2")')
bool | cancel | Determines if it's cancelled or not
bool | check | Checks if the battle damage is 0 and cancels the effect if it is
bool | copy_info | Copys the effects information if the effect is duplicated
bool | enable | Applys the status to the card
bool | enabled | Enables field effects
bool | ex | Excludes mg from the effect targets
bool | forced | The effects registration will be forced
bool | get_info | Gets the event's information
bool | ignore_count | Ignores the amount of cards
bool | ignore_field | Ignores if there is a free space on the field
bool | ignore_mon | Ignores fusion material monsters
bool | is_step | Equips multiple cards (in one step, which is concluded with 'Duel.EquipComplete()')
bool | monsteronly | Can only attack monsters
bool | neglect_con | Ignores if it meets the effects condition(s) or not
bool | neglect_cost | Ignores the effects costs
bool | nocheck | Ignoring summoning conditions
bool | noflip | Flip effects are not activated at this time
bool | nolimit | Ignoring the revive limit
bool | proc | The card is treated as if it was summoned by its proper summoning procedure (used in puzzles)
bool | setavailable | Raises a "set" event (cards/effects that activate if one of the targets is set are triggered)
bool | up | Set to true if the card itself is equipped, to false if it gets equipped
bool | use_hand | Includes player's hand
Card | equip_card | The card which is equipped to the target
Card | ex | Excluded cards which will not be affected
Card | c | Any single card (The interpreter will complain if you use a Card which is still treated as a Group. Use Group.GetFirst(Group g) to convert it)
Card | fc | A fusion card (fusion monster)
Card | gc | -
Card | rc | A ritual card (ritual monster)
Card | sc | The effects target card
Card | smat | A single synchro material card (ignored if there is a mg, which is then used as synchro material)
Card | tuner | Tuner card
Card | xyzc | An Xyz monster card

type | variable name| description
-- | -- | --
Card\|Group | targets | A card or group which will be affected by the effect
Card\|Group\|Effect | labelobject | Object to embed in the effect, accepts Card, Group, or Effect (In case of group from outside the effect, don't forget to keep the group alive)
Effect | e | Any effect
Effect | re | The reason effect which caused a certain event
function | f | Any function which returns a boolean value(s)
function | op_func | An operation function (with these parameters:)
function | targ_func | A target function (with these parameters:)
function | con_func | A condition function (with these parameters depending on the effect's code:)
function | cost_func | A cost function (with these parameters:)
function\|int\|bool | val | A boolean or integer value or a function with these parameters:
Group | g | Any amount of cards
Group | mg | A matching group of cards which are targets for the effect
Group | ocard | Group of cards to overlay to the card


type | variable name| description
-- | -- | --
int | ac | The attack chain number to check
int | activity_type | Type of activity to check (for example: ACTIVITY_SUMMON)
int | ad | Facedown attack position monsters are changed to this position
int | assume_type | Type of assuming to be done by the card (ASSUME_x)
int | assume_value | value of assuming (for example: if assume_type is ASSUME_LEVEL, assume_value would be the assumed level)
int | atk | Value of Attack Points
int | attack | Value of Attack Points
int | attribute | Attribute (for example: ATTRIBUTE_WATER)
int | au | Faceup attack position monsters are changed to this position
int | available | Options for player to choose between (E.G. in AnnounceRace, the sum of all races to choose from).
int | cate | Category of effect (CATEGORY_x)
int | chainc |  -
int | check_player | The player that checks
int | chkf | Checking function
int | code | Either a card's ID (for example: 1855932) or an Effect (for example: EFFECT_UPDATE_ATTACK), depending on usage
int | controler | The player that will get control
int | cost | Cost function
int | count | Amount
int | counter | The value of the turn counter to be set
int | counter_id | ID of Activity Counter (for example: ACTIVITY_SUMMON)
int | countertype | Type of counter (0x3001=Spell Counter, etc. Look at strings.conf for official available counters)
int | cp | The owner of zones that will be returned
int | dd | Facedown Defense Position monsters are changed to this position
int | def | Value of Defense Points
int | defense | Value of Defense Points
int | desc | Description (commonly represented by 'aux.Stringid(code, id)' which pulls the description text from the cdb) (It will show "???" if your ID is outside the allowed range: See ".constant GetDesc()")
int | dest | Destination (a location, for example: LOCATION_MZONE)
int | drawcount | Sets Player's Draw count to the number
int | du | Faceup defense position monsters are changed to this position
int | ep | Sets the Event Player for the raised event
int | ev | Event value
int | event | Event
int | extra_type | Additional Card Types for Trap Monster
int | filter | A bitflag denoting disabled field positions (for example: '0b00101' = '0x7' means Position 0 and 2 is disabled)
int | flag | Reload files with these Flags
int | global_flag | Global flag(s) to enable (for example: GLOBALFLAG_DECK_REVERSE_CHECK+GLOBALFLAG_SCRAP_CHIMERA)
int | hint_type | Type of Hint
int | label | A value
int | level | Level
int | location | Location (for example: LOCATION_DECK)
int | lp | Amount of Lifepoints
int | lv | Level
int | max | Maximum amount
int | markers | The Link Markers to check if the card has
int | min | Minimum amount
int | move_player | Sets the player that moves the card
int | number | An integer number


type | variable name| description
-- | -- | --
int | o | Opponent's player's Field Bitflags
int | o_range | Opposing player's locations affected by the effect (for example: LOCATION_SZONE+LOCATION_DECK)
int | o_time | Timing of effect in opposing player's turn (TIMING_x)
int | owner | Owner of the added card
int | param | The chain's new parameter
int | player | Any player
int | playerid | Player whose info would be set
int | pos | Position (for example: POS_FACEUP)
int | prop | Property for effect (for example: EFFECT_FLAG_x)
int | property | Property for the flag effect (for example: EFFECT_FLAG_x)
int | r | reason, the cause of the event
int | race | Race (for example: RACE_FISH)
int | range | Location of handler card where the effect can be applied or activated
int | rank | Rank
int | reason | Reason
int | res | New result of coin/dice
int | reset | Timing of NegateRelatedChain to reset (RESET_x)
int | reset_code | Code for Effect Resetting. May be various things depending on reset_type
int | reset_count | How many times after hitting phase reset will the effect or relation be finally truly reset. A value of 0 or 1 means the effect resets immediately after meeting the reset condition
int | reset_flag | Flag for conditions of resetting the effect or relation (for example: RESET_EVENT+0x1fe0000+RESET_PHASE+PHASE_DAMAGE)
int | reset_phase | The phase the effect will reset.
int | reset_type |  -

type | variable name| description
-- | -- | --
int | rp | reason player, the player that triggered the event
int | s | Selected player's Field Bitflags
int | s_range | Selected player's Field Bitflags
int | s_time | Bitflag denoting timing for selected player's turn
int | seq | Sequence in Deck, or sequence on the field
int | setcode | Card's SetCode (Archetype)
int | setname | Card's SetCode (Archetype)
int | singly | How many counters to place at once, or if to place them group-by-group at all
int | sort_player | The player sorting the Decktop
int | spsummon_code | The code of the card that can only be Special Summoned once per turn
int | startcount | Player's starting hand count
int | status | A status (e.g. STATUS_DISABLED)
int | sum | The target value for the sum of function returns in a group (see functions named WithSumEqual)
int | sumplayer | The player conducting a summon
int | sumpos | The position in which a monster will be summoned
int | sumtype | The type of summon with which a monster will be summoend
int | target_player | The player to whose side of the field a monster will be summoned
int | timing | When things happen (for example: TIMING_DRAW)
int | type | The effect's type (for example: EFFECT_TYPE_SINGLE/FIELD/TRIGGER_F)
int | unique_code | Card code to be unique
int | unique_location | The location where the card should be unique
int | use_player | The Player that will use the location
int | value | An integer value
int | win_reason | Reason of winning
nil | nil | Empty/Undefined/Nothing
string | msg | Any message
string | name | Any String

