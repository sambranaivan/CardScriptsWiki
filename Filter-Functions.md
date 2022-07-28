A filter function is a function that takes a card as its first parameter and returns a boolean (either `true` or `false`).
A simple example would be:
```lua
function s.lvfilter(c)
	return c:IsMonster() and c:IsLevel(4)
end
```
This returns `true` if the card `c` is a Level 4 monster.

## Using filters
Filters are mostly used with certain `Duel` and `Group` functions that collect or check for cards that fulfill the filter (in other words, cards that make the filter return `true`). Some of the most common functions that use a filter are [listed below](#). These functions will call the filter passed to them for every card they are concerned with.

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
Let's look at an official script, **[Foolish Burial](https://github.com/ProjectIgnis/CardScripts/blob/master/official/c81439173.lua)**, and see how it uses a filter function.
The card text is simple:
> Send 1 monster from your Deck to the GY.

The script uses the following filter function, which returns `true` for cards that are monsters and can be sent to the GY:
```lua
function s.tgfilter(c)
	return c:IsMonster() and c:IsAbleToGrave()
end
```

To activate **Foolish Burial**, a player must be able to send a monster from their Deck to the GY. So before activation, the script must check if a valid card exists in the player's deck. This is its "activation legality check" and is done inside the `if chk==0 then` block in the target function (`s.target`):
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

> You can read [Understanding a card script](https://github.com/ProjectIgnis/CardScripts/wiki/Parameter-naming-convention#understanding-a-card-script) to learn more about the different parts of a script (such as the `if chk==0 then` block). This page will only focus on the usage of filter functions.

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
- `0` is the location in `tp`'s opponent's side of the board (`0` denotes that the `tp` will not be selecting opponent cards)
- the first `1` is the minimum number of cards to select
- the second `1` is maximum number of cards to select (since it's equal to the minimum, the player will select exactly 1 card)
- `nil` is the card(s) to be exempted (`nil` denotes that there are no exceptions)

This means `Duel.SelectMatchingCard(tp,s.tgfilter,tp,LOCATION_DECK,0,1,1,nil)` can be read as: *make the player who activated this card select exactly 1 card in their deck that is a monster and can be sent to the GY*.

The selected card is stored in a group that is assigned to a local variable named `g`. If the group is not empty (`#g>0`), it is sent to the GY and **Foolish Burial**'s effect finishes resolving.

## Additional Filter Parameters
Sometimes, filters need additional details other than the card they're checking. For example, we may need to write a filter for a face-up monster with ATK higher than the activating player's LP - a value that changes throughout the duel. This is where having additional filter parameters comes in.

Filter functions always take a card as their first parameter (usually named `c` by convention), but they can take any amount of parameters after that. For the earlier example, we can create a filter that has an additional parameter called `minatk`. We then check inside the filter if `c`'s ATK is greater than or equal to `minatk`.
```lua
function s.atkfilter(c,minatk)
	return c:IsFaceup() and c:IsAttackAbove(minatk)
end
```
Now, for the filter to know what `minatk` is, **it needs to be passed to it**. This part is important. Otherwise, `minatk` would just be `nil`.

[Functions that use filters](#) can take additional arguments. These functions will pass the additional arguments they receive (after the "exception" argument) to the filter they're using, and they become additional arguments of that filter.

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
TBA

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