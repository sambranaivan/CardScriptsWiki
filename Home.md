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

Return type | Function |Description
-- | -- | --
int | bit.replace(int a, int b, int c[, int width=1]) | Returns a copy of (int a) with the field with a width changed to value (int b)
int | bit.extract(int a, int b[, int width=1]) | Returns the field of (int a) with a width
int | Card.GetLuaRef(Card c) | Returns an integer representing the internal value used by lua to access the Card c.
Card | Card.FromLuaRef(int ref) | Returns a Card object from a given lua reference. The function errors out if the reference is invalid or does not refer to a Card object.
bool | Card.IsDeleted(Card c) | Returns if the Card object got internally deleted and remained as dangling reference inside the lua state.
int | Group.GetLuaRef(Group g) | Returns an integer representing the internal value used by lua to access the Group g.
Group | Group.FromLuaRef(int ref) | Returns a Group object from a given lua reference. The function errors out if the reference is invalid or does not refer to a Group object.
bool | Group.IsDeleted(Group g) | Returns if the Group object got internally deleted and remained as dangling reference inside the lua state.
int | Effect.GetLuaRef(Effect e) | Returns an integer representing the internal value used by lua to access the Effect e.
Effect | Effect.FromLuaRef(int ref) | Returns a Effect object from a given lua reference. The function errors out if the reference is invalid or does not refer to a Effect object.
bool | Effect.IsDeleted(Effect e) | Returns if the Effect object got internally deleted and remained as dangling reference inside the lua state.
table, int | GetID() | Returns two values, a card object and its ID, used before the initial effect.
int[,int] | Card.GetCode(Card c) | Returns the current code (ID/name) of the card "c".
int | Card.GetOriginalCode(Card c) | Returns the original printed code (ID/name) of the card "c".
int, int | Card.GetOriginalCodeRule(Card c) | Returns the original code (ID/name) of the card "c" while taking into account name clauses/alias (used for the "original name" wording).
int, int ... | Card.GetFusionCode(Card c) | Returns the code/ID that "c" has as a Fusion Material (see "Fusion Tag").
int, int ... | Card.GetLinkCode(Card c) | Returns the code/ID that "c" has as a Link Material (see "Formud Skipper").
bool | Card.IsSummonCode(Card c, Card sc\|nil, int sumtype, int playerid, int ...) | Checks if "c" has a specific code from the "..." list if it is to be used as material for the Summon type "sumtype" of "sc" performed by the player "playerid".
bool | Card.IsFusionCode(Card c, int ...) | Checks if "c" has a specific code from the "..." list as a Fusion Material.
bool | Card.IsLinkCode(Card c, int ...) | Checks if "c" has a specific code from the "..." list as a Link Material.
bool | Card.IsSetCard(Card c, int setname[, Card scard\|nil, int sumtype = 0, int playerid = PLAYER_NONE]) | Checks if "c" is part of the archetype "setname" (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
bool | Card.IsOriginalSetCard(Card c, int setname) | Checks if "c" is originally part of the archetype "setname".
bool | Card.IsPreviousSetCard(Card c, int setname) | Checks if "c" was previously part of the archetype "setname".
bool | Card.IsFusionSetCard(Card c, int setname) | Checks if "c" is part of the archetype "setname" if it is to be used as a Fusion Material.
int ... | Card.GetSetCard(Card c[, Card\|nil scard, int sumtype=0, int playerid=PLAYER_NONE]) | Returns the archetype(s) that "c" has (if it is to be used as material for "scard" with Summon type "sumtype" by player "playerid").
int ... | Card.GetOriginalSetCard(Card c) | Returns the original archetype(s) that "c" is a part of.
int ... | Card.GetPreviousSetCard(Card c) | Returns the archetype(s) that "c" was part of previously.
int ... | Card.GetFusionSetCard(Card c) | Returns the archetype(s) that "c" is a part of if it is to be used as a Fusion Material.
bool | Card.IsLinkSummonable(Card c[, Group\|Card\|nil must_use, Group\|Card\|nil  mg, int min=0, int max=0]) | Checks if "c" can be Link Summoned using "must_use" as part of its materials, choosing among "mg", with "min" and "max" materials to be used for the Link Summon.
bool | Card.IsLinkSetCard(Card c, int setname) | Checks if "c" is part of the archetype "setname" as a Link Material.

