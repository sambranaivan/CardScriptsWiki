# Duel
Skill are placed near the Field Zone unless said otherwise at the start of the duel (before the draw)
Skills Don't use the Chain (Activation Circle appear next to the Skill if you can activate it)
![](https://cdn.discordapp.com/attachments/282741557797453825/674577472720732167/unknown.png)


# Scripting
## Skill Proc
There is 3 different procedure for Skills
### Field Spell Skill Procedure
Auxiliary.AddFieldSkillProcedure(c,coverNum,drawless)
- c: the skill (card)
- coverNum: the cover corresponding to the back (int), for ex, to add the first Cover of the Character, put "1" as parameter, for the second "2", etc
- drawless: if the skill make you draw 1 less card at the start of the duel (bool)

The Procedure place the Skill in the Field Zone at the start of the duel, then Flip it
If the Skill get bounced, the player can activate it like a regular card

![](https://cdn.discordapp.com/attachments/282741557797453825/674581832812986378/unknown.png)

### Continuous Spell/Trap Skill
Auxiliary.AddContinuousSkillProcedure(c,coverNum,drawless,flip)
- c: the card (card)
- coverNum: the cover corresponding to the back (int), for ex, to add the first Cover of the Character, put "1" as parameter, for the second "2", etc
- drawless: if the player draw 1 less card at the start of the duel (bool)
- flip: if the continuous card get flipped at the start of the duel (bool)

The procedure place the card in the Middle Zone of the Spell/Trap Zone, then flip it if required
![](https://cdn.discordapp.com/attachments/282741557797453825/674581500771041280/unknown.png)

### Predraw Skill Procedure
Function for the skills that "trigger" at the start of the turn/Before the Draw
Auxiliary.AddPreDrawSkillProcedure(c,coverNum,drawless,skillcon,skillop,countlimit)
- c: the card (card)
- coverNum: the cover corresponding to the back (int), for ex, to add the first Cover of the Character, put "1" as parameter, for the second "2", etc
- drawless: if the player draw 1 less card at the start of the duel (bool)
- skillcon: condition to activate the skill (function)
- skillOp: operation related to the skill activation (function)
- countlimit: if the skill have a soft OPT limite, you put a int as parameter, otherwise, leave it nil

When you are able to activate the Skill, the game will ask you before your draw, then the operation function is used

### Other Skill Procedure
Auxiliary.AddSkillProcedure(c,coverNum,drawless,skillcon,skillop,countlimit)
- c: the card (card)
- coverNum: the cover corresponding to the back (int), for ex, to add the first Cover of the Character, put "1" as parameter, for the second "2", etc
- drawless: if the player draw 1 less card at the start of the duel (bool)
- skillcon: condition to activate the skill (function)
- skillOp: operation related to the skill activation (function)
- countlimit: if the skill have a soft OPT limite, you put a int as parameter, otherwise, leave it nil

## Hint
Values
HINT_SKILL = 200
HINT_SKILL_COVER = 201
HINT_SKILL_FLIP  = 202
HINT_SKILL_REMOVE = 203

HINT_SKILL sets the code of the skill, if it's called first, the skill is created faceup
ex: Duel.Hint(HINT_SKILL,1,FrontID)

HINT_SKILL_COVER sets the cover and id for the skill, cover is value & 0xffffffff, code is (value>>32) & 0xffffffff. if called first, the skill is created facedown.
ex: Duel.Hint(HINT_SKILL_COVER,1,coverID|(BackEntryID<<32))

HINT_SKILL_FLIP changes the position of the skill facedown/faceup, updating the code aswell, the core is value&0xffffffff, then 0x100000000 is faceup and 0x200000000 is facedown
ex: Duel.Hint(HINT_SKILL_FLIP,0,id|(1<<32))

HINT_SKILL_REMOVE remove the skill from the location, it is not useful right now, but it was added in case one day we get a skill that move itself from the skill zone into the field.

HINT_SKILL is only sent to the team corresponding to teh playerid, the others to every player, so usage would be use cover first, and put the cover as both the card and the cover (so you'll see the description of the cover), then send hint_skill to the players with the actual skill, and use flip when needed, passing the skill code so it's updated for the oppo as well

## Other Useful Functions
- Auxiliary.GetCover(c,coverNum) : function that return the ID of the cover in function of the Character of the skill (Character value being placed as Race in cdb atm since it don't have value atm)
- Auxiliary.CanActivateSkill(tp) : function used to check if the player can activate the skill (no chain active and it is currently the main phase)
- aux.RegisterDrawless(c): function to generate the "Draw 1 less card at the start of the duel", it create a dummy card on top of the deck which is sent to limbo as soon as it is draw

# CDB handling
There is two kind of entries
- The Front Entry: Display the card text of both side, have the Character as a Race
- The Back/Character Entry: Display the card text of the back side, have the Character as a Race

The ID is following the logic:
For the Front of the Skills:
Prefix = 300 
Middle on the product, 1XX is booster, 2XX is decks and 3XX is other (promo for ex), XX being incremented each new product
Suffix is place order of the card in the product

For the Back entry of the skills
they are based on 30X0YYYYY entries
X being the "Number" of the Cover, YYYYY being the character Value
the Race is used as a placeholder for the "Character"
ex: the second cover of Mako would be 302000128
since Mako character is "Pyro" so with the value 0x80=128


# Proxy/Cover handling
There is three pics needed for a Skill:
- The Pic of the Front of the Skill (displayed in card info and on the field)
- The pic of the Back of the Skill (displayed in the card info windows)
- The pic of the Back of the Skill placed in Cover (displayed on the field)
