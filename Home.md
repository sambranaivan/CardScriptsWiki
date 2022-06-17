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

## `Duel` methods:

### GetZoneWithLinkedCount
```c++
int Duel.GetZoneWithLinkedCount(int count, int tp)
```
Returns a zone flag including the tp's zones that are pointed by at least "count" Link Monsters.
### GoatConfirm
```c++
void Duel.GoatConfirm(int tp, int loc)
```
Used for goat versions of cards, handle the "fail to find" scenario. It confirms tp's LOCATION_DECK or LOCATION_HAND (passed in loc), the hand is revealed to the opposing player, the deck is revealed to tp.