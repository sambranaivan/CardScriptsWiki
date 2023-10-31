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
- `rc`: reason card (usually defined as `rc=re:GetHandler()`.

Those are the usual meanings, but these variable names can be used in other contexts, and it's up to the user to use these names or not.
