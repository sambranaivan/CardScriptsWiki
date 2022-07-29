A filter function is a function that takes a card as its first parameter and returns a boolean (either `true` or `false`).
A simple example would be:
```lua
function s.lvfilter(c)
	return c:IsMonster() and c:IsLevel(4)
end
```
This returns `true` if the card `c` is a Level 4 monster.

## Using filters
Filters are mostly used with certain `Duel` and `Group` functions that collect or check for cards that fulfill the filter (in other words, cards that make the filter return `true`). Some of the most common functions that use a filter are [listed below](#appendix-a-some-common-functions-that-use-filters). These functions will call the filter passed to them for every card they are concerned with.

For example, we can use the `s.lvfilter` we have earlier to check if there are cards that fulfill it in certain locations. The following statement will be `true` if there is at least 1 Level 4 monster in either player's GY:
```lua
Duel.IsExistingMatchingCard(s.lvfilter,tp,LOCATION_GRAVE,LOCATION_GRAVE,1,nil)
```

We can also make a player select cards that fulfill a filter. Here, a player will select 1 Level 4 monster in their hand, and the selected card will be stored in a group called `g`:
```lua
local g=Duel.SelectMatchingCard(tp,s.lvfilter,LOCATION_HAND,0,1,1,nil)
```
> **NOTE:**
You can check the [scripting library](wiki/Scripting-Library) for more functions that use filters, and to learn what their other parameters do. By tweaking the other parameters, you can check cards in a different location, make the player select more than 1 card, etc.

### Studying Foolish Burial
Let's look at an official script, [<u>Foolish Burial</u>](https://github.com/ProjectIgnis/CardScripts/blob/master/official/c81439173.lua), and see how it uses a filter function.
The card text is simple:
> Send 1 monster from your Deck to the GY.

The script uses the following filter function, which returns `true` for cards that are monsters and can be sent to the GY:
```lua
function s.tgfilter(c)
	return c:IsMonster() and c:IsAbleToGrave()
end
```

To activate <u>Foolish Burial</u>, a player must be able to send a monster from their Deck to the GY. So before activation, the script must check if a valid card exists in the player's deck. This is its "activation legality check" and is done inside the `if chk==0 then` block in the target function (`s.target`):
```lua
	if chk==0 then return Duel.IsExistingMatchingCard(s.tgfilter,tp,LOCATION_DECK,0,1,nil) end
```
Here, `Duel.IsExistingMatchingCard` is used with the following arguments:
- `s.tgfilter` is the filter function explained earlier
- `tp` is the player activating the card.
- `LOCATION_DECK` is the location that will be checked in `tp`'s side of the board 
- `0` is the location in `tp`'s opponent's side of the board (`0` denotes that we're not checking any location in the opponent's side)
- `1` is the minimum number of cards that must fulfill `s.tgfilter`
- `nil` is the card(s) to be exempted from the check (`nil` denotes that there are no exceptions)

This means the entire line can be read as: *the activation of this card is legal if there is at least 1 card in the activating player's deck that is a monster and can be sent to the GY*

> **NOTE:**
You can read [Understanding a card script](https://github.com/ProjectIgnis/CardScripts/wiki/Parameter-naming-convention#understanding-a-card-script) to learn more about the different parts of a script (such as the `if chk==0 then` block). This page will only focus on the usage of filter functions.

Now that the script knows when it's legal to activate the card, let's look at what happens when the card is actually activated and the effect resolves. This is in the effect's operation function (`s.operation`):
```lua
function s.activate(e,tp,eg,ep,ev,re,r,rp)
	Duel.Hint(HINT_SELECTMSG,tp,HINTMSG_TOGRAVE)
	local g=Duel.SelectMatchingCard(tp,s.tgfilter,tp,LOCATION_DECK,0,1,1,nil)
	if #g>0 then
		Duel.SendtoGrave(g,REASON_EFFECT)
	end
end
```
First, it gives the player a "hint" that the selection is for cards that will be sent to the GY. Then, it calls `Duel.SelectMatchingCard` with the following arguments:
- the first `tp` is the player that will perform the selection
- `s.tgfilter` is the filter that the card choices must fulfill
- the next `tp` is the player who activated the card
- `LOCATION_DECK` is the location in `tp`'s side of the board where `tp` will select
- `0` is the location in `tp`'s opponent's side of the board (`0` denotes that `tp` will not be selecting opponent cards)
- the first `1` is the minimum number of cards to select
- the second `1` is the maximum number of cards to select (since it's equal to the minimum, the player will select exactly 1 card)
- `nil` is the card(s) to be exempted (`nil` denotes that there are no exceptions)

This means `Duel.SelectMatchingCard(tp,s.tgfilter,tp,LOCATION_DECK,0,1,1,nil)` can be read as: *make the player who activated this card select exactly 1 card in their deck that is a monster and can be sent to the GY*.

The selected card is stored in a group that is assigned to a local variable named `g`. If the group is not empty (`#g>0`), it is sent to the GY and <u>Foolish Burial</u>'s effect finishes resolving.

## Additional Filter Parameters
Sometimes, filters need additional details other than the card they're checking. For example, we may need to write a filter for a face-up monster with ATK higher than the activating player's LP - a value that changes throughout the duel. This is where having additional filter parameters comes in.

Filter functions always take a card as their first parameter (usually named `c` by convention), but they can take any amount of parameters after that. For the earlier example, we can create a filter that has an additional parameter called `minatk`. We then check inside the filter if `c`'s ATK is greater than or equal to `minatk`.
```lua
function s.atkfilter(c,minatk)
	return c:IsFaceup() and c:IsAttackAbove(minatk)
end
```
Now, for the filter to know what `minatk` is, **it needs to be passed to it**. This part is important. Otherwise, `minatk` would just be `nil`.

[Functions that use filters](#appendix-a-some-common-functions-that-use-filters) can take additional arguments. These functions will pass the additional arguments they receive (after the "exception" argument) to the filter they're using, and they become additional arguments of that filter.

To illustrate, say we have an effect with an activation condition that says `If you control a face-up monster with ATK higher than your LP:`. For this, we can use the `s.atkfilter` earlier like so:
```lua
function s.condition(e,tp,eg,ep,ev,re,r,rp)
	local lp=Duel.GetLP(tp)
	return Duel.IsExistingMatchingCard(s.atkfilter,tp,LOCATION_MZONE,0,1,nil,lp)
end
```
Here, we first obtained `tp`'s LP and assigned it to the variable named `lp`. Then, we passed that `lp` as an extra argument to `Duel.IsExistingMatchingCard`. Note that it counts as an extra argument since it comes after the "exception" argument, which is `nil` in this case.

Internally, `Duel.IsExistingMatchingCard` will call `s.atkfilter` using `lp` as an extra argument. This will correspond to the `minatk` parameter of the filter. In other words, the first extra argument passed to `Duel.IsExistingMatchingCard` (called `lp`) becomes the first argument passed to `s.atkfilter` (called `minatk`).

### Studying Deep Sea Diva
When Special Summoning monsters through a card effect, we need filters to check for cards that can be Special Summoned. Those filters will need to call `Card.IsCanBeSpecialSummoned` inside them, which in turn needs to know what effect and player is attempting the Special Summon. The filter wouldn't know what those are, so we need to pass them as additional arguments. Hence, Special Summon filters typically look like this:
```lua
function s.spfilter(c,e,tp)
    return c:IsCanBeSpecialSummoned(e,0,tp,false,false) --and other checks we want to perform
end
```
This filter is fulfilled by cards that can be Special Summoned by the player `tp` through the effect `e`.

> **NOTE:** You'll notice that we're actually calling `Card.IsCanBeSpecialSummoned` with more arguments (there's a `0` and two `false`s). However, those are just plain values that we don't need to pass to the filter. For the purposes of this guide, we'll only focus on how `e` and `tp` are being passed, but you can read more about `Card.IsCanBeSpecialSummoned`'s other parameters in the [scripting library](wiki/Scripting-Library).

Let's look at [the script for <u>Deep Sea Diva</u>](https://github.com/ProjectIgnis/CardScripts/blob/master/official/c81439173.lua) to see a Special Summon filter in action. <u>Deep Sea Diva</u> has this effect:
> When this card is Normal Summoned: You can Special Summon 1 Level 3 or lower Sea Serpent monster from your Deck.

For this, it uses the following filter, which returns `true` for Level 3 or lower Sea Serpent monsters that can be Special Summoned by player `tp` using effect `e`:
```lua
function s.spfilter(c,e,tp)
	return c:IsLevelBelow(3) and c:IsRace(RACE_SEASERPENT) and c:IsCanBeSpecialSummoned(e,0,tp,false,false)
end
```

For the effect to be activated legally, the player must have a valid monster in their deck that they can Special Summon (meaning, they must have a monster in their deck that fulfills `s.spfilter`). The player must also have a free Main Monster Zone that they can Special Summon to. These two things are checked by the script inside the `if chk==0 then` block of the target function (`s.sptg`).
```lua
function s.sptg(e,tp,eg,ep,ev,re,r,rp,chk)
	if chk==0 then return Duel.IsExistingMatchingCard(s.spfilter,tp,LOCATION_DECK,0,1,nil,e,tp)
		and Duel.GetLocationCount(tp,LOCATION_MZONE)>0 end
	--etc.
end
```
Here, the script calls `Duel.IsExistingMatchingCard` with two extra arguments, `e` and `tp`. Again, they come after the "exception" which is `nil`.
`e` is this effect of <u>Deep Sea Diva</u> that is being checked for activation legality, and `tp` is the activating player. Both values are automatically supplied through `s.sptg`'s own parameters (`e,tp,eg,ep,ev,re,r,rp,chk`).

Since `e` will also be the effect that would perform the Special Summon, 
the script passes it to `Duel.IsExistingMatchingCard` as an extra argument. Similarly, the activating player will also be the player that would perform the Special Summon, so it is also passed. **The order matters when passing additional arguments**. The first extra argument will become the filter's first extra argument, the second extra argument becomes the filter's second extra argument, and so on.

In this particular script, it so happens that the extra parameters of `s.spfilter` are also called `e` and `tp`, but the names don't really need to match. The extra arguments just have to be in the proper order that the filter expects them to be. The following usage is perfectly valid:
```lua
function s.spfilter(c,the_effect_that_would_summon,the_player_that_would_summon)
	return c:IsLevelBelow(3) and c:IsRace(RACE_SEASERPENT)
		and c:IsCanBeSpecialSummoned(the_effect_that_would_summon,0,the_player_that_would_summon,false,false)
end
function s.sptg(e,tp,eg,ep,ev,re,r,rp,chk)
	local this_effect_of_diva=e
	local the_activating_player=tp
	if chk==0 then return Duel.IsExistingMatchingCard(s.spfilter,tp,LOCATION_DECK,0,1,nil,this_effect_of_diva,the_activating_player)
		and Duel.GetLocationCount(tp,LOCATION_MZONE)>0 end
	--etc.
end
```
This illustrates that once passed to `Duel.IsExistingMatchingCard` (which passes it to `s.spfilter`), `this_effect_of_diva` becomes `the_effect_that_would_summon` because it's the first extra argument, while `the_activating_player` becomes `the_player_that_would_summon` because it's the second extra argument.

Now let's move to the effect resolution:
```lua
function s.spop(e,tp,eg,ep,ev,re,r,rp)
	if Duel.GetLocationCount(tp,LOCATION_MZONE)<=0 then return end
	Duel.Hint(HINT_SELECTMSG,tp,HINTMSG_SPSUMMON)
	local g=Duel.SelectMatchingCard(tp,s.spfilter,tp,LOCATION_DECK,0,1,1,nil,e,tp)
	if #g>0 then
		Duel.SpecialSummon(g,0,tp,tp,false,false,POS_FACEUP)
	end
end
```
First, it checks if `tp` has a free Main Monster Zone. If not, the effect stops resolving by having an early `return`. Then, it gives a "hint" to `tp` that the following card selection is for a Special Summon. Much like in `s.sptg`, the effect and player are already supplied (`e` and `tp`). This time, they are passed as extra arguments to `Duel.SelectMatchingCard` which passes them to `s.spfilter`. This allows `tp` to select a Level 3 or lower Sea Serpent monster that they can Special Summon from their deck. The selection is stored in a group called `g`, and `g` is finally Special Summoned if it's not empty (`#g>0`).

## Nesting Filters
TBA

## Auxiliary Filters and Helpers
TBA

## Other Insights
TBA

## Appendix A: Some common functions that use filters
- `Duel.IsExistingMatchingCard`
- `Duel.SelectMatchingCard`
- `Duel.IsExistingTarget`
- `Duel.SelectTarget`
- `Group.Filter`
- `Group.IsExists`