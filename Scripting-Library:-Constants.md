- For a list of the constants used to represent archetypes in scripts see [archetype_setcode_constants](https://github.com/ProjectIgnis/CardScripts/blob/master/archetype_setcode_constants.lua) file

- For a list of the commonly used card names that have a constant as well as constant for some counters and tokens, see the [card_counter_constants](https://github.com/ProjectIgnis/CardScripts/blob/master/card_counter_constants.lua) file

- This is the [main constant](https://github.com/ProjectIgnis/CardScripts/blob/master/constant.lua) file


### Locations, positions, sequences
| Value | Name | Description |
| --- | --- | --- |
| 0x1 | LOCATION_DECK | The Deck. If it is used as Location Redirect, the card is placed on the top. (decimal value= 1) |
| 0x2 | LOCATION_HAND | The hand  (decimal value= 2) |
| 0x4 | LOCATION_MZONE | The Monster Zone  (decimal value= 4) |
| 0x8 | LOCATION_SZONE | The Spell\|Trap Zones. It includes the Field Spell Zone and the Pendulum Zones (<=MR3). (decimal value= 8) |
| 0x10 | LOCATION_GRAVE | The graveyard\|GY (decimal value= 16) |
| 0x20 | LOCATION_REMOVED | The area where banished card go (decimal value= 32) |
| 0x40 | LOCATION_EXTRA | The Extra Deck (decimal value= 64) |
| 0x80 | LOCATION_OVERLAY | The location for cards attached as Xyz Material. Also the location used for "stacked" cards  (for anime-only cards) (decimal value= 128) |
| 0x0c | LOCATION_ONFIELD | All locations on the field. The sum of LOCATION_MZONE+LOCATION_SZONE. (decimal value= 192 ) |
| 0x3c | LOCATION_PUBLIC | Used for scripting purposes. The sum of locations (LOCATION_ONFIELD+LOCATION_REMOVED+LOCATION_GRAVE) where cards are, usually, public knowledge. |
| 0x3ff | LOCATION_ALL | All possible locations. This is the sum of LOCATION_ONFIELD, LOCATION_DECK, LOCATION_HAND, LOCATION_GRAVE, LOCATION_REMOVED, LOCATION_EXTRA and LOCATION_OVERLAY |
| 0x10001 | LOCATION_DECKBOT | The Bottom of Deck. Used only in Location Redirect |
| 0x20001 | LOCATION_DECKSHF | Location for cards that are place in Deck and then the Deck is shuffled. Used only in Location Redirect |
| 0x100 | LOCATION_FZONE | The Field Spell zone |
| 0x200 | LOCATION_PZONE | The Pendulum Zone |
| 0x400 | LOCATION_STZONE | The Spell\|Trap Zone (without the Field Zone). Symbolic location. Can be used in functions expecting a location and also in SetRange (except with trigger effects) |
| 0x800 | LOCATION_MMZONE | The Main Monster Zones. Symbolic location. Can be used in functions expecting a location and also in SetRange (except with trigger effects) |
| 0x1000 | LOCATION_EMZONE | The Extra Monster Zones. Symbolic location. Can be used in functions expecting a location and also in SetRange (except with trigger effects) |
| 0x1f | ZONES_MMZ | Constant to be used as mask to filter for main monster zones |
| 0x60 | ZONES_EMZ | Constant to be used as mask to filter for extra monster zones |
| 0 | SEQ_DECKTOP | Sequence to be used with Duel.SendtoDeck. Sends the card to the top of the Deck |
| 1 | SEQ_DECKBOTTOM | Sequence to be used with Duel.SendtoDeck. Sends the card to the bottom of the Deck |
| 2 | SEQ_DECKSHUFFLE | Sequence to be used with Duel.SendtoDeck. Sends the card to the top of the Deck, then suffles it |
| 0 | COIN_HEADS | Value for coin results |
| 1 | COIN_TAILS | Value for coin results |
| 0x5 | POS_FACEUP | Face-up position, attack + defense if on field.  (decimal value= 5) |
| 0xa | POS_FACEDOWN | Face-down position, attack + defense if on field  (decimal value= 10) |
| 0x1 | POS_FACEUP_ATTACK | Face-up attack position (decimal value= 1) |
| 0x2 | POS_FACEDOWN_ATTACK | Face-down attack position. Used with "Darkness Approaches" (Pre-Errata) |
| 0x4 | POS_FACEUP_DEFENSE | Face-up defense position (decimal value= 4) |
| 0x8 | POS_FACEDOWN_DEFENSE | Face-down defense position (decimal value= 8) |
| 0x3 | POS_ATTACK | Attack position, face-up + face-down (decimal value= 3) |
| 0xc | POS_DEFENSE | Defense position, face-up + face-down  (decimal value= 12) |
| 0x10000 | NO_FLIP_EFFECT | Applies position change without triggering FLIP effects |


### Card types, attributes and monster type
| Value | Name | Description |
| --- | --- | --- |
| 0x1 | TYPE_MONSTER | A Monster card  (decimal value= 1) |
| 0x2 | TYPE_SPELL | A Spell card  (decimal value= 2) |
| 0x4 | TYPE_TRAP | A Trap card (decimal value= 4) |
| 0x10 | TYPE_NORMAL | A Normal monster (decimal value= 16) |
| 0x20 | TYPE_EFFECT | A card with effect (decimal value= 32) |
| 0x40 | TYPE_FUSION | A Fusion (monster) (decimal value= 64) |
| 0x80 | TYPE_RITUAL | A Ritual card (decimal value= 128) |
| 0x100 | TYPE_TRAPMONSTER | A Trap monster, e.g. Embodiment of Apophis. NOTE: This is not used in addition to the default card types.  (decimal value= 256) |
| 0x200 | TYPE_SPIRIT | Spirit monster (decimal value= 512) |
| 0x400 | TYPE_UNION | Union monster (decimal value= 1024) |
| 0x800 | TYPE_GEMINI | A Gemini monster (decimal value= 2048) |
| 0x1000 | TYPE_TUNER | Tuner (decimal value=4096) |
| 0x2000 | TYPE_SYNCHRO | A Synchro (decimal value= 8192) |
| 0x4000 | TYPE_TOKEN | A token  (decimal value= 16384) |
| 0x8000 | TYPE_MAXIMUM | A Maximum Monster  (decimal value= 32768) |
| 0x10000 | TYPE_QUICKPLAY | A Quick Play card  (decimal value= 65536) |
| 0x20000 | TYPE_CONTINUOUS | A Continuous card (decimal value=131072 ) |
| 0x40000 | TYPE_EQUIP | An equip card (decimal value= 262144) |
| 0x80000 | TYPE_FIELD | A field card (decimal value= 524288) |
| 0x100000 | TYPE_COUNTER | A counter card, used for Counter Trap cards (decimal value=1048576 ) |
| 0x200000 | TYPE_FLIP | Flip (decimal value= 2097152) |
| 0x400000 | TYPE_TOON | Toon (decimal value= 4194304) |
| 0x800000 | TYPE_XYZ | An Xyz (decimal value= 8388608) |
| 0x1000000 | TYPE_PENDULUM | Pendulum (decimal value= 16777216) |
| 0x2000000 | TYPE_SPSUMMON | An Special Summon-only monster. Used for Nomi\|Semi-Nomi Main Deck monsters (decimal value= 33554432) |
| 0x4000000 | TYPE_LINK | A Link (decimal value= 67108864) |
| 0x8000000 | TYPE_SKILL | A Skill Card. (decimal value= 134217728) |
| 0x10000000 | TYPE_ACTION | An Action card. (decimal value= 268435456) |
| 0x4011 | TYPES_TOKEN | Constant used to simplify cards that summon tokens. Sum of the following values: Monster + Normal + Token (decimal value= 16401) |
| 0x4802040 | TYPE_EXTRA | And extra deck monster card that. This is the summon of TYPE_FUSION+TYPE_SYNCHRO+TYPE_XYZ+TYPE_LINK (decimal value= 75505728) |
| 0x20000000 | TYPE_PLUS | Plus Type, only usable if 419 is called |
| 0x40000000 | TYPE_MINUS | Minus Type, only usable if 419 is called |
| 0x80000000 | TYPE_ARMOR | Armor Type, only usable if 419 is called |
| 0x1 | ATTRIBUTE_EARTH | The EARTH attribute for monsters  (decimal value= 1) |
| 0x2 | ATTRIBUTE_WATER | The WATER attribute for monsters (decimal value= 2) |
| 0x4 | ATTRIBUTE_FIRE | The FIRE attribute for monsters (decimal value= 4) |
| 0x8 | ATTRIBUTE_WIND | The WIND attribute for monsters (decimal value= 8) |
| 0x10 | ATTRIBUTE_LIGHT | The LIGHT attribute for monsters (decimal value= 16) |
| 0x20 | ATTRIBUTE_DARK | The DARK attribute for monsters (decimal value= 32) |
| 0x40 | ATTRIBUTE_DIVINE | The DIVINE attribute for monsters (decimal value= 64) |
| 0x80 | ATTRIBUTE_LAUGH | The LAUGH attribute, only usable if the 419 script is called |
| 0x7f | ATTRIBUTE_ALL | The sum of all official monster attributes (including divine) |
| 0x3ffffff | RACE_ALL | A constant that includes all monster types from Warrior to Illusionist |
| 0x1 | RACE_WARRIOR | Warrior type monster (decimal value= 1) |
| 0x2 | RACE_SPELLCASTER | Spellcaster type monster (decimal value= 2) |
| 0x4 | RACE_FAIRY | Fairy type monster (decimal value= 4) |
| 0x8 | RACE_FIEND | Fiend type monster (decimal value= 8) |
| 0x10 | RACE_ZOMBIE | Zombie type monster (decimal value= 16) |
| 0x20 | RACE_MACHINE | Machine type monster (decimal value= 32) |
| 0x40 | RACE_AQUA | Aqua type monster (decimal value=64 ) |
| 0x80 | RACE_PYRO | Pyro type monster (decimal value=128 ) |
| 0x100 | RACE_ROCK | Rock type monster (decimal value= 256) |
| 0x200 | RACE_WINGEDBEAST | Winged Beast type monster (decimal value= 512) |
| 0x400 | RACE_PLANT | Plant type monster (decimal value= 1024) |
| 0x800 | RACE_INSECT | Insect type monster (decimal value= 2048) |
| 0x1000 | RACE_THUNDER | Thunder type monster (decimal value=4096) |
| 0x2000 | RACE_DRAGON | Dragon type monster (decimal value= 8192) |
| 0x4000 | RACE_BEAST | Beast type monster (decimal value= 16384) |
| 0x8000 | RACE_BEASTWARRIOR | Beast-Warrior type monster (decimal value= 32768) |
| 0x10000 | RACE_DINOSAUR | Dinosaur type monster (decimal value= 65536) |
| 0x20000 | RACE_FISH | Fish type monster (decimal value= 131072) |
| 0x40000 | RACE_SEASERPENT | Sea Serpent type monster (decimal value= 262144) |
| 0x80000 | RACE_REPTILE | Reptile type monster (decimal value= 524288) |
| 0x100000 | RACE_PSYCHIC | Psychic type monster (decimal value= 1048576) |
| 0x200000 | RACE_DIVINE | Divine-Beast type monster (decimal value= 2097152) |
| 0x400000 | RACE_CREATORGOD | Creator God type monster (decimal value= 4194304) |
| 0x800000 | RACE_WYRM | The Wyrm monster type (decimal value= 8388608) |
| 0x1000000 | RACE_CYBERSE | The Cyberse monster type (decimal value= 16777216) |
| 0x2000000 | RACE_ILLUSION | The Illusion monster type (decimal value= 33554432) |
| 0x4000000 | RACE_CYBORG | Rush duel monster type (race) |
| 0x8000000 | RACE_MAGICALKNIGHT | Rush duel monster type (race) |
| 0x10000000 | RACE_HIGHDRAGON | Rush duel monster type (race) |
| 0x20000000 | RACE_OMEGAPSYCHIC | Rush duel monster type (race) |
| 0x40000000 | RACE_CELESTIALWARRIOR | Rush duel monster type (race) |
| 0x80000000 | RACE_GALAXY | Rush duel monster type (race) |
| 0x4000000000000000 | RACE_YOKAI | Yokai type monster, only usable if token 419 is called. |
| 0xc200 | RACES_BEAST_BWARRIOR_WINGB | Union of Beast, Beast-Warrior and Winged Beast types, for the many cards that support all 3 at once. |


### Reasons, summon types, status and assume values
| Value | Name | Description |
| --- | --- | --- |
| 0x1 | REASON_DESTROY | The card being destroyed (decimal value= 1) |
| 0x2 | REASON_RELEASE | The card being tributed (decimal value= 2) |
| 0x4 | REASON_TEMPORARY | The card being  temporary banished (decimal value= 4) |
| 0x8 | REASON_MATERIAL | Used as Fusion/Synchro/Xyz/Link material, etc. (decimal value= 8) |
| 0x10 | REASON_SUMMON | Used for a summon (decimal value= 16) |
| 0x20 | REASON_BATTLE | The card being destroyed by battle (decimal value= 32) |
| 0x40 | REASON_EFFECT | The reason that causes the event is a card effect (decimal value= 64) |
| 0x80 | REASON_COST | The reason used for costs. It is also the same used to destroy/send to the GY cards that fail to pay their maintenance costs (decimal value= 128) |
| 0x100 | REASON_ADJUST | Adjustment (Royal before the test) (decimal value= 256) |
| 0x200 | REASON_LOST_TARGET | Equip Target stops being face-up, either by leaving the field or being flipped face-down (decimal value= 512) |
| 0x400 | REASON_RULE | The value used for reasons associated with game mechanics (decimal value= 1024) |
| 0x800 | REASON_SPSUMMON | The reason for the event is an Special Summon (decimal value= 2048) |
| 0x1000 | REASON_DISSUMMON | The reason for the event is a Summon being negated (dissummon= disabled summon) (decimal value= 4096) |
| 0x2000 | REASON_FLIP | Being flipped (decimal value= 8192) |
| 0x4000 | REASON_DISCARD | The reason for the even is a card being discarded (decimal value= 16384) |
| 0x8000 | REASON_RDAMAGE | Reversal Damage: gain LP becomes damage - used only in the core |
| 0x10000 | REASON_RRECOVER | Reversal Recovery: damage becomes gain LP - used only in the core |
| 0x20000 | REASON_RETURN | Return from banished to Graveyard (decimal value= 131072) |
| 0x40000 | REASON_FUSION | Used for Fusion Summon (decimal value= 262144) |
| 0x80000 | REASON_SYNCHRO | Used for Synchro Summon (decimal value= 524288) |
| 0x100000 | REASON_RITUAL | Used for Ritual Summon (decimal value= 1048576) |
| 0x200000 | REASON_XYZ | Used for Xyz Summon (decimal value= 2097152) |
| 0x400000 | REASON_REPLACE | Event is happening because of an effect that states "If X would be destroyed, do this instead." (decimal value= 4194304) |
| 0x800000 | REASON_DRAW | Event is a card being drawn (decimal value= 8388608) |
| 0x1000000 | REASON_REDIRECT | Sent to a location other than intended, eg "Banish this card if it leaves the field." (decimal value= 16777216) |
| 0x8000000 | REASON_REVEAL | Used by cards that require being sent to the GY after being excavated. See "Sylvan" monsters |
| 0x10000000 | REASON_LINK | Used for Link Summon (decimal value= 67108864) |
| 0x1 | LOCATION_REASON_TOFIELD | Default reason for Duel.GetLocationCount(), counts for Kaiser Colosseum |
| 0x2 | LOCATION_REASON_CONTROL | Used by Card.IsControlerCanBeChanged() |
| 0x4 | LOCATION_REASON_COUNT | Duel.GetLocationCount() for DisableField |
| 0x10000000 | SUMMON_TYPE_NORMAL | Normal summoned (EFFECT_SUMMON_PROC, EFFECT_SET_PROC can use SetValue to modify the value) |
| 0x11000000 | SUMMON_TYPE_ADVANCE | Tribute Summon, an specific type of Normal Summon. |
| 0x12000000 | SUMMON_TYPE_GEMINI | Normal Summoned Gemini Monster. |
| 0x20000000 | SUMMON_TYPE_FLIP | Flip Summon |
| 0x40000000 | SUMMON_TYPE_SPECIAL | Special summon (EFFECT_SPSUMMON_PROC, EFFECT_SPSUMMON_PROC_G can use SetValue to modify the value) |
| 0x43000000 | SUMMON_TYPE_FUSION | Fusion Summon |
| 0x45000000 | SUMMON_TYPE_RITUAL | Ritual Summon |
| 0x46000000 | SUMMON_TYPE_SYNCHRO | Synchro Summon |
| 0x49000000 | SUMMON_TYPE_XYZ | Xyz Summon |
| 0x4a000000 | SUMMON_TYPE_PENDULUM | Pendulum Summon |
| 0x4c000000 | SUMMON_TYPE_LINK | Link Summon |
| 0x4e000000 | SUMMON_TYPE_MAXIMUM | Maximum Summon (Rush duel summon type) |
| 0x1 | STATUS_DISABLED | Effect is negated |
| 0x2 | STATUS_TO_ENABLE | Effect negation would be removed |
| 0x4 | STATUS_TO_DISABLE | Effect would be negated |
| 0x8 | STATUS_PROC_COMPLETE | The card has been summoned properly  (usually by its own condition) |
| 0x10 | STATUS_SET_TURN | Spell/Traps set this turn |
| 0x20 | STATUS_NO_LEVEL | The card is treated as having Level/Rank/Link 0 |
| 0x40 | STATUS_BATTLE_RESULT | Destroyed by battle at the end of damage calculation |
| 0x80 | STATUS_SPSUMMON_STEP | Special Summon not yet finished aka "Step" |
| 0x100 | STATUS_FORM_CHANGED | A monster that had his position manually changed in the current turn |
| 0x200 | STATUS_SUMMONING | The timing for when a monster "Would be Summoned" |
| 0x400 | STATUS_EFFECT_ENABLED | Usable card on field (has activated, already Summoned, effects applied) |
| 0x800 | STATUS_SUMMON_TURN | The monster was Normal Summoned/Set in the current turn |
| 0x1000 | STATUS_DESTROY_CONFIRMED | The card is going to be destroyed |
| 0x2000 | STATUS_LEAVE_CONFIRMED | After the chain resolves, an activated card with this status would immediately go to Graveyard |
| 0x4000 | STATUS_BATTLE_DESTROYED | Already destroyed by battle (during battle) |
| 0x8000 | STATUS_COPYING_EFFECT | A card with this status is copying the effect of another card |
| 0x10000 | STATUS_CHAINING | A card wiith this status has one of its effects on the current Chain |
| 0x20000 | STATUS_SUMMON_DISABLED | A monster which had its summon negated |
| 0x40000 | STATUS_ACTIVATE_DISABLED | A card that had its activation negated |
| 0x80000 | STATUS_EFFECT_REPLACED | A card affected by ReplaceEffect |
| 0x100000 | STATUS_FUTURE_FUSION | Future Materials wouldn't trigger after Fusion Monster is Summoned |
| 0x200000 | STATUS_ATTACK_CANCELED | Attack was negated |
| 0x400000 | STATUS_INITIALIZING | Cards which are at "initial_effect" state |
| 0x1000000 | STATUS_JUST_POS | A monster that had just changed its position |
| 0x2000000 | STATUS_CONTINUOUS_POS | Set again after changing to other positions |
| 0x4000000 | STATUS_FORBIDDEN | A card that cannot be used (for example, if it was declared by Prohibition or Psi-Blocker) |
| 0x8000000 | STATUS_ACT_FROM_HAND | A card with this sattus can be activated from hand |
| 0x10000000 | STATUS_OPPO_BATTLE | Has destroyed an opponent's monster by battle |
| 0x20000000 | STATUS_FLIP_SUMMON_TURN | A card with this status was Flip Summoned in the current turn |
| 0x40000000 | STATUS_SPSUMMON_TURN | A card with this status was Special Summoned in the current turn |
| 1 | ASSUME_CODE | Temporarily assumes that the affected card has a given code (ID/name) |
| 2 | ASSUME_TYPE | Temporarily assumes that the affected card has a given Type |
| 3 | ASSUME_LEVEL | Temporarily assumes that the affected card has a given level |
| 4 | ASSUME_RANK | Temporarily assumes that the affected card has a given rank |
| 5 | ASSUME_ATTRIBUTE | Temporarily assumes that the affected card has a given attribute |
| 6 | ASSUME_RACE | Temporarily assumes that the affected card has a given race |
| 7 | ASSUME_ATTACK | Temporarily assumes that the affected card has a given ATK |
| 8 | ASSUME_DEFENSE | Temporarily assumes that the affected card has a given DEF |
| 9 | ASSUME_LINK | Temporarily assumes that the affected card has a given Link Rating |
| 10 | ASSUME_LINKMARKER | Temporarily assumes that the affected card has given Link Markers |


### link markers, counter permissions, phases and players
| Value | Name | Description |
| --- | --- | --- |
| 0x1 | LINK_MARKER_BOTTOM_LEFT | Has this link arrow: ↙ |
| 0x2 | LINK_MARKER_BOTTOM | Has this link arrow: ⬇ |
| 0x4 | LINK_MARKER_BOTTOM_RIGHT | Has this link arrow: ↘ |
| 0x8 | LINK_MARKER_LEFT | Has this link arrow: ⬅ |
| 0x20 | LINK_MARKER_RIGHT | Has this link arrow: ➡ |
| 0x40 | LINK_MARKER_TOP_LEFT | Has this link arrow: ↖ |
| 0x80 | LINK_MARKER_TOP | Has this link arrow: ⬆ |
| 0x100 | LINK_MARKER_TOP_RIGHT | Has this link arrow: ↗ |
| 0x1000 | COUNTER_WITHOUT_PERMIT | Added to counter value to allow counters for any card (does not require Card.EnableCounterPermit) |
| 0x2000 | COUNTER_NEED_ENABLE | Added to counter value to require target to require its effects not negated |
| 0x01 | PHASE_DRAW | The Draw Phase of a player (decimal value= 1) |
| 0x02 | PHASE_STANDBY | The Standby Phase (decimal value= 2) |
| 0x04 | PHASE_MAIN1 | The Main Phase 1 (decimal value= 4) |
| 0x08 | PHASE_BATTLE_START | The Start Step, first step of the Battle Phase (decimal value= 8) |
| 0x10 | PHASE_BATTLE_STEP | The Battle Step (decimal value= 16) |
| 0x20 | PHASE_DAMAGE | The Damage Step (decimal value= 32) |
| 0x40 | PHASE_DAMAGE_CAL | The Damage Calculation (decimal value= 64) |
| 0x80 | PHASE_BATTLE | Battle Phase/End of Battle Phase (decimal value= 128) |
| 0x100 | PHASE_MAIN2 | The Main Phase 2 (decimal value= 256) |
| 0x200 | PHASE_END | The End Phase of a turn (decimal value= 512) |
| 2 | PLAYER_NONE | No player |
| 3 | PLAYER_ALL | Both players |
| 4 | PLAYER_EITHER | Any player |

###  Chaininfo
| Value | Name | Description |
| --- | --- | --- |
| 0x1 | CHAININFO_CHAIN_COUNT | Chain Link Number |
| 0x2 | CHAININFO_TRIGGERING_EFFECT | The effect that triggered the current Chain Link |
| 0x4 | CHAININFO_TRIGGERING_PLAYER | The player that triggered the current Chain Link |
| 0x8 | CHAININFO_TRIGGERING_CONTROLER | The controller of the card that triggered the current Chain Link |
| 0x10 | CHAININFO_TRIGGERING_LOCATION | The location of the card that triggered the current Chain Link |
| 0x11 | CHAININFO_TRIGGERING_LOCATION_SYMBOLIC |
| 0x20 | CHAININFO_TRIGGERING_SEQUENCE | The sequence (zone within a location) that triggered the current Chain Link |
| 0x21 | CHAININFO_TRIGGERING_SEQUENCE_SYMBOLIC |
| 0x40 | CHAININFO_TARGET_CARDS | Cards targeted by the effect of the current Chain Link |
| 0x80 | CHAININFO_TARGET_PLAYER | Player targeted by the effect of the current Chain Link |
| 0x100 | CHAININFO_TARGET_PARAM | Get Value set in Duel.SetTargetParam() |
| 0x200 | CHAININFO_DISABLE_REASON | The reason that disabled the effect/card/summon |
| 0x400 | CHAININFO_DISABLE_PLAYER | The player that disabled the effect/card/summon |
| 0x800 | CHAININFO_CHAIN_ID | Chain ID |
| 0x1000 | CHAININFO_TYPE | Chain type |
| 0x2000 | CHAININFO_EXTTYPE | Chain extra type |
| 0x4000 | CHAININFO_TRIGGERING_POSITION | The position of the card that triggered the current Chain Link |
| 0x8000 | CHAININFO_TRIGGERING_CODE | The id of the card that triggered the current Chain Link |
| 0x10000 | CHAININFO_TRIGGERING_CODE2 |
| 0x40000 | CHAININFO_TRIGGERING_LEVEL | The level of the card that triggered the current Chain Link |
| 0x80000 | CHAININFO_TRIGGERING_RANK | The rank of the card that triggered the current Chain Link |
| 0x100000 | CHAININFO_TRIGGERING_ATTRIBUTE | The attribute of the card that triggered the current Chain Link |
| 0x200000 | CHAININFO_TRIGGERING_RACE | The type (warrior, zombie, etc) of the card that triggered the current Chain Link |
| 0x400000 | CHAININFO_TRIGGERING_ATTACK | The attack of the card that triggered the current Chain Link |
| 0x800000 | CHAININFO_TRIGGERING_DEFENSE | The defense of the card that triggered the current Chain Link |


### Reset values
| Value | Name | Description |
| --- | --- | --- |
| 0x1000 | RESET_EVENT | Reset when a given event occurs (add the event value) |
| 0x2000 | RESET_CARD | Reset Owner to specify the effect of the card |
| 0x4000 | RESET_CODE | Reset the single effect of the specified Code (excluding EFFECT_FLAG_SINGLE_RANGE) |
| 0x8000 | RESET_COPY | Reset to copy the effect achieved |
| 0x10000 | RESET_DISABLE | Reset when the card's effect is negated |
| 0x20000 | RESET_TURN_SET | Reset when turned face-down ("Set") |
| 0x40000 | RESET_TOGRAVE | Reset when the card goes to the graveyard |
| 0x80000 | RESET_REMOVE | Reset when the card is banished |
| 0x100000 | RESET_TEMP_REMOVE | Reset when the card is temporarily banished |
| 0x200000 | RESET_TOHAND | Reset when the card is sent to the hand |
| 0x400000 | RESET_TODECK | Reset when the card is sent to the deck |
| 0x800000 | RESET_LEAVE | Resets when the card leaves the field (the card moves to a different location from LOCATION_MZONE or LOCATION_SZONE) |
| 0x1000000 | RESET_TOFIELD | Reset when the card moves to the field (the card moves to LOCATION_MZONE or LOCATION_SZONE from a different location. Returning to the field is not included) |
| 0x2000000 | RESET_CONTROL | Reset when control of the card changes |
| 0x4000000 | RESET_OVERLAY | Reset when the card is used as Xyz Material |
| 0x8000000 | RESET_MSCHANGE | Reset when moving between the monster zones and spell/trap zones (MoveToField(), Crystal Beasts) |
| 0x10000000 | RESET_SELF_TURN | Reset on your turn |
| 0x20000000 | RESET_OPPO_TURN | Reset on the opponent's turn |
| 0x40000000 | RESET_PHASE | Resets at a given phase (add the phase value) |
| 0x80000000 | RESET_CHAIN | Reset at the end of the resolving Chain |
| 0x01fe0000 | RESETS_STANDARD | Complex reset. The sum of RESET_TURN_SET, TOGRAVE, REMOVE, TEMP_REMOVE, TOHAND, TODECK, LEAVE and TOFIELD, to be used with RESET_EVENT |
| 0x01ff0000 | RESETS_STANDARD_DISABLE | Complex reset. The sum of RESETS_STANDARD+RESET_DISABLE, used with RESET_EVENT. Used for effects that need to reset when the monster's effects are negated (eg a monster changing its ATK/DEF or Level with its own effect). |
| 0x047e0000 | RESETS_REDIRECT | Complex reset. The sum of RESETS_STANDARD+RESET_OVERLAY-RESET_TOFIELD-RESET_LEAVE, most often used for EFFECT_LEAVE_FIELD_REDIRECT resets |
| 0x17e0000 | RESETS_CANNOT_ACT | Complex reset. The sum of RESETS_STANDARD-RESET_LEAVE, used in thing like ancient gear drill and troymare maybe. |
| 0x17a0000 | RESETS_STANDARD_EXC_GRAVE | Complex reset. The sum of  RESETS_STANDARD-RESET_TOGRAVE-RESET_LEAVE, mainly used for card that negate effect of card they destroy by battle. |


### Effect types and effect flags
| Value | Name | Description |
| --- | --- | --- |
| 0x1 | EFFECT_TYPE_SINGLE | An effect that applies only to itself. When used with trigger effects, this makes the card look for the event only when it happens to itself. |
| 0x2 | EFFECT_TYPE_FIELD | An effect that applies to the whole field.When used with trigger effects, this makes the effect look for the event when it happens to anything |
| 0x4 | EFFECT_TYPE_EQUIP | An effect that applies when the card is an Equip card. |
| 0x8 | EFFECT_TYPE_ACTIONS | Effects that trigger. (Added to effects automatically) |
| 0x10 | EFFECT_TYPE_ACTIVATE | Spell/Trap Activation |
| 0x20 | EFFECT_TYPE_FLIP | Trigger effect that adds EFFECT_TYPE_TRIGGER_F to SetType and EVENT_FLIP to SetCode by default |
| 0x40 | EFFECT_TYPE_IGNITION | An effect that the turn player chooses to apply during their Main Phase, in a open game state. It is Speed Spell 1 |
| 0x80 | EFFECT_TYPE_TRIGGER_O | Optional Trigger effect |
| 0x100 | EFFECT_TYPE_QUICK_O | Optional Quick effect |
| 0x200 | EFFECT_TYPE_TRIGGER_F | Mandatory Trigger effect |
| 0x400 | EFFECT_TYPE_QUICK_F | Mandatory Quick Effect (such as Light and Darkness Dragon) |
| 0x800 | EFFECT_TYPE_CONTINUOUS | Auxiliary effect / persistent effect triggered by an event |
| 0x1000 | EFFECT_TYPE_XMATERIAL | Applies an effect to a monster that has this card as Xyz Material (see "Zoodiac" cards) |
| 0x2000 | EFFECT_TYPE_GRANT | Provides an effect to other cards (see "The Weather" cards) |
| 0x4000 | EFFECT_TYPE_TARGET | Currently not used by any cards. Evaluated by the core in the following functions: effect::is_target, effect::is_available, card::add_effect and card::remove_effect |
| 0x1 | EFFECT_FLAG_INITIAL | Original effect of a card (automatically applied) |
| 0x2 | EFFECT_FLAG_FUNC_VALUE | The Value property of this effect is a function |
| 0x4 | EFFECT_FLAG_COUNT_LIMIT | The number of times an effects can be triggered |
| 0x8 | EFFECT_FLAG_FIELD_ONLY | This effect is registered to the global environment |
| 0x10 | EFFECT_FLAG_CARD_TARGET | The effect includes targetting a card |
| 0x20 | EFFECT_FLAG_IGNORE_RANGE | Card affecting all areas "(Prohibition", "Imperial Iron Wall") |
| 0x40 | EFFECT_FLAG_ABSOLUTE_TARGET | Target Range does not change due to changes in control |
| 0x80 | EFFECT_FLAG_IGNORE_IMMUNE | Effect applies regardless of a card being "Unaffected by card effects" |
| 0x100 | EFFECT_FLAG_SET_AVAILABLE | Effect applies to face-down ("Set") cards |
| 0x200 | EFFECT_FLAG_CANNOT_NEGATE | For effects that say "This effect cannot be negated." in their text |
| 0x400 | EFFECT_FLAG_CANNOT_DISABLE | Effect cannot be negated |
| 0x800 | EFFECT_FLAG_PLAYER_TARGET | Effect targets a player (Mystical Refpanel) |
| 0x800 | EFFECT_FLAG_BOTH_SIDE | Effect affects both sides of the field |
| 0x2000 | EFFECT_FLAG_COPY_INHERIT | Effect is inherited by a card that copies it |
| 0x4000 | EFFECT_FLAG_DAMAGE_STEP | Effect can activate during the Damage Step |
| 0x8000 | EFFECT_FLAG_DAMAGE_CAL | Effect can activate during Damage Calculation, a sub-step of the Damage Step. |
| 0x10000 | EFFECT_FLAG_DELAY | By adding this delay flag, the effect is prevented from missing the timing |
| 0x20000 | EFFECT_FLAG_SINGLE_RANGE | The effect that has this flag is only valid for the card itself |
| 0x40000 | EFFECT_FLAG_UNCOPYABLE | The effect that has this flag cannot be copied |
| 0x80000 | EFFECT_FLAG_OATH | Oath effect |
| 0x100000 | EFFECT_FLAG_SPSUM_PARAM | Flag to indicate in a special summon in which zone(s) of the field and to which player. (eg. SetTargetRange in "Lava Golem") |
| 0x200000 | EFFECT_FLAG_REPEAT | God's incarnation's attack power is double counted |
| 0x400000 | EFFECT_FLAG_NO_TURN_RESET | Flag used for effects that "can only be used once while this card is face-up on the field", e.g. Wind-Up monsters. |
| 0x800000 | EFFECT_FLAG_EVENT_PLAYER | As the other player's effect (action?) |
| 0x1000000 | EFFECT_FLAG_OWNER_RELATE | Continues to be the object |
| 0x2000000 | EFFECT_FLAG_CANNOT_INACTIVATE | An effect with this flag cannot have its activation negated |
| 0x4000000 | EFFECT_FLAG_CLIENT_HINT | A client prompt/description |
| 0x8000000 | EFFECT_FLAG_CONTINUOUS_TARGET |
| 0x10000000 | EFFECT_FLAG_LIMIT_ZONE | When this flag is added to an effect, using that effect would cause the number of zones available to decrease (see Draco Face-off). The SetValue must be used to define the zones that will still be available with the activation. |
| 0x80000000 | EFFECT_FLAG_IMMEDIATELY_APPLY | The effect of the card immediately when launched (Toon Kingdom) |
| 0x001 | EFFECT_FLAG2_CONTINUOUS_EQUIP | This flag allows Continuous Traps that equip themselves to use their trigger/quick effects while equipped |
| 0x0002 | EFFECT_FLAG2_COF | Normal Spell that activates during the Standby Phase (Curse of Fiend) |
| 0x0004 | EFFECT_FLAG2_CHECK_SIMULTANEOUS |
| 0x40000000 | EFFECT_FLAG2_FORCE_ACTIVATE_LOCATION |
| 0x80000000 | EFFECT_FLAG2_MAJESTIC_MUST_COPY | If flag is used, effect will be copied in MajesticCopy wherein normally only trigger effects will be copied. |

### Effect codes
| Value | Name | Description |
| --- | --- | --- |
| 1 | EFFECT_IMMUNE_EFFECT | Affected card is unaffected by card effects. The SetValue of this effect takes the following parameters: e: this effect itself re: the effect that would affect the card. c: the card that would be affected (uncertain, to be confirmed) |
| 2 | EFFECT_DISABLE | Ineffective (skills extraction) |
| 3 | EFFECT_CANNOT_DISABLE | The affected card cannot have its effects negated |
| 4 | EFFECT_SET_CONTROL | The affected card's control is set to a given player. The player should be defined in SetValue (SetValue receives e and c) |
| 5 | EFFECT_CANNOT_CHANGE_CONTROL | Control of the affected card cannot change. Does not take a SetTarget or Setvalue. |
| 6 | EFFECT_CANNOT_ACTIVATE | The affected player(s) cannot activate the effects that match this effect's SetValue. SetValue takes the following parameters: e = this effect re = the effect would be activated tp = the player that would activate the effect |
| 7 | EFFECT_CANNOT_TRIGGER | The affected card cannot activate its effects. Usually used as EFFECT_TYPE_SINGLE. If a field version is used, cards that return true for the SetTarget are the ones that cannot activate their effects. In this card, SetTarget receives e and c as parameters. |
| 8 | EFFECT_DISABLE_EFFECT | The affected card has its effects negated |
| 9 | EFFECT_DISABLE_CHAIN | Affected card has its activation negated |
| 10 | EFFECT_DISABLE_TRAPMONSTER | Negates Trap monsters |
| 12 | EFFECT_CANNOT_INACTIVATE | Affected cards (single range or via set target range) cannot have the activation of their effect(s) negated. If SetValue is used, it receives the following parameters: e: this effect itself chaincount: |
| 13 | EFFECT_CANNOT_DISEFFECT | Affected cards cannot have the resolution of their effects negated. If SetValue is used, it receives the following parameters: e: this effect itself chaincount: the chain associated with the effect. Can be used in Duel.GetChainInfo |
| 14 | EFFECT_CANNOT_CHANGE_POSITION | Affected card cannot change its battle position. Usually used as a single effect but if a field version is used, SetTarget receives e and c as parameters. |
| 15 | EFFECT_TRAP_ACT_IN_HAND | The affected Trap Card can be activated from the hand. If the card is not TYPE_TRAP, this effect is skipped. Usually used as EFFECT_TYPE_SINGLE if a field version is used SetTarget receives e and c as parameters. It is suggested that SetDescription is also applied with this effect, for the scenarios where multiple similar effects are available, to allow the player to choose which one to apply. |
| 16 | EFFECT_TRAP_ACT_IN_SET_TURN | Affected Trap Card can be activated the turn it was set. If the card is not TYPE_TRAP and/or does not have STATUS_SET_TURN, this effect is skipped. The property EFFECT_FLAG_SET_AVAILABLE should be set. Usually used as EFFECT_TYPE_SINGLE if a field version is used SetTarget receives e and c as parameters. It is suggested that SetDescription is also applied with this effect, for the scenarios where multiple similar effects are available, to allow the player to choose which one to apply. |
| 17 | EFFECT_REMAIN_FIELD | Affected card remains on the field (e.g. Swords of Revealing Light) |
| 18 | EFFECT_MONSTER_SSET | The affected monster can be placed in the Spell/Trap zone. SetValue should hold the type the card is set as (for example, TYPE_SPELL). See Artifact monsters |
| 19 | EFFECT_QP_ACT_IN_SET_TURN | Allows Quick-Play Spells to be activated the turn they are set. This effect is skipped if any of the following 3 tests is false: the card is TYPE_SPELL, the card is TYPE_QUICKPLAY or has EFFECT_BECOME_QUICK, the card has STATUS_SET_TURN. Usually used as EFFECT_TYPE_SINGLE if a field version is used SetTarget receives e and c as parameters. It is suggested that SetDescription is also applied with this effect, for the scenarios where multiple similar effects are available, to allow the player to choose which one to apply. |
| 20 | EFFECT_CANNOT_SUMMON | The affected player cannot Normal Summon. A field effect that requires EFFECT_FLAG_PLAYER_TARGET to be set and the players to be defined in SetTargetRange. SetTarget receives the following parameters: e: this effect itself c: the card that would be summoned sump: the player that would Summon sumtyp: the summon type sumpos: the summon position (fixed as POS_FACEUP in the core) tp: the target player (the player that would get the monster) |
| 21 | EFFECT_CANNOT_FLIP_SUMMON | The affected player cannot Flip Summon.The target function of this effect receives the following parameters: |
| e = this effect (EFFECT_CANNOT_FLIP_SUMMON) |
| c = the card that would be affected by it (the ones that cannot be Special Summoned) |
| playerid = the player that would do the summon |
| 22 | EFFECT_CANNOT_SPECIAL_SUMMON | The affected player cannot Special Summon. Requires the property EFFECT_FLAG_PLAYER_TARGET and the players defined via SetRange. The target function of this effect receives the following parameters: e = this effect (EFFECT_CANNOT_SPECIAL_SUMMON) c = the card that would be affected by it (the ones that cannot be Special Summoned) playerid = the player that would do the summon sumtype = the type of the summon sumpos = the position in which the monster would be summoned in toplayer = the player that would receive the monster sumeff = the effect that would summon |
| 23 | EFFECT_CANNOT_MSET | Affected player cannot Set monsters. This effect's SetTarget takes the following parameters: -e: this effect itself -c: the cards affected by it -playerid: the player that would Set -sumtype: the summon type -toplayer: the player that would receive the monster -sumpos: the position in which the monsters would be summoned (fixed as POS_FACEDOWN by the core) |
| 24 | EFFECT_CANNOT_SSET | The affected player (set via SetTargetRange, with EFFECT_FLAG_PLAYER_TARGET as property) cannot set Spell/Trap cards. If a target function is used, the following parameters are passed to it: -e: this effect itself -c: the card(s) that cannot be set -tp: the player that cannot set  (to be confirmed, might be player whose field cannot have cards set) |
| 25 | EFFECT_CANNOT_DRAW | The affected player cannot draw cards |
| 26 | EFFECT_CANNOT_DISABLE_SUMMON | The affected monster cannot have its Normal Summon negated |
| 27 | EFFECT_CANNOT_DISABLE_SPSUMMON | The affected monster cannot have its Special Summon negated |
| 28 | EFFECT_SET_SUMMON_COUNT_LIMIT | Limit the number of monsters placed per turn |
| 29 | EFFECT_EXTRA_SUMMON_COUNT | Increases the number of Normal Summons the player can make. The value should be set in SetValue. |
| 30 | EFFECT_SPSUMMON_CONDITION | The affected monster has an Special Summon condition that must be fulfilled. Cards/effects that return true for the SetValue are allowed to Special Summmon the monster. SetValue for this function takes the following parameters: -effect: this effect itself -sum_effect: the effect that would summon -sum_player: the player that would summon -sum_type: the summon type what would be used for the summon -sum_pos: the position in which the monster would be summoned -toplayer: the player that would receive the monster |
| 31 | EFFECT_REVIVE_LIMIT | The affected card must be Special Summoned properly before being Special Summoned from public locations |
| 32 | EFFECT_SUMMON_PROC | Specifies a special method through which the affected card can be Normal Summoned |
| 33 | EFFECT_LIMIT_SUMMON_PROC | Specifies a special method through which the affected card must be Normal Summoned |
| 34 | EFFECT_SPSUMMON_PROC | Specifies a special method through which the affected card can be Special Summoned |
| 35 | EFFECT_EXTRA_SET_COUNT | Increase the number of monsters the player can set (usually 1 Normal Summon/Set per turn) |
| 36 | EFFECT_SET_PROC | Specifies a special method through which the affected card can be Normal Set |
| 37 | EFFECT_LIMIT_SET_PROC | Specifies a special method through which the affected card must be Normal Set |
| 38 | EFFECT_LIGHT_OF_INTERVENTION | Monsters can be Normal Summoned in face-up Defense Position (Light of Intervention). |
| 39 | EFFECT_CANNOT_DISABLE_FLIP_SUMMON | The Flip Summon of the affected monster cannot be negated (Spell Wall) |
| 40 | EFFECT_INDESTRUCTABLE | Affected card cannot be destroyed. SetValue receives the following parameters: |
| e: this effect itself |
| re: reason effect, the effect that would cause the destruction |
| r: reason, always considered as REASON_EFFECT by the core rp: reason player |
| 41 | EFFECT_INDESTRUCTABLE_EFFECT | Affected card cannot be destroyed by card effect. SetValue receives the following parameters: |
| e: this effect itself |
| re: reason effect, the effect that would cause the destruction |
| rp: reason player, the player that would cause the destruction |
| c: this card (to be confirmed) |
| 42 | EFFECT_INDESTRUCTABLE_BATTLE | Affected card cannot be destroyed by battle |
| 43 | EFFECT_UNRELEASABLE_SUM | Affected card cannot be tributed for a Tribute Summon. SetValue in this effect receives only `e` and `c` as parameters. |
| 44 | EFFECT_UNRELEASABLE_NONSUM | Affected card cannot be tributed for effects. SetValue in this effect receives only `e` and `c` as parameters. |
| 45 | EFFECT_DESTROY_SUBSTITUTE | Required alternative to destruction (this card is destroyed with other cards instead). SetValue receives the following parameters: |
| e: this effect itself |
| re: reason effect (confirm in the core, might default to current.reason_effect) r: reason  (confirm in the core, might default to current.reasont) |
| rp: reason player (confirm in the core, might default to current.reason_player) |
| 46 | EFFECT_CANNOT_RELEASE | Affected player cannot tribute monsters. Requires the players to be set via SetTargetRange (and the EFFECT_FLAG_PLAYER_TARGET flag). Cards that return true for the SetTarget in this effect cannot be tributed by that player. SetTarget takes the following parameters: -e: this effect itself -c: the card(s) that would be tributed (to be confirmed) -tp: the player that would tribute |
| 47 | EFFECT_INDESTRUCTABLE_COUNT | Affected card cannot be destroyed up to a given number of times. SetValue receives the following parameters: e: this effect itself re: reason effect, the effect that would cause the destruction rp: reason player, the player that would cause the destruction c: this card (to be confirmed) |
| 48 | EFFECT_UNRELEASABLE_EFFECT | Affected card cannot be Tributed by card effects.  SetValue receives the following parameters: |
| e: this effect itself |
| re: reason effect, the effect that would tribute the card |
| rp: reason player, the player that would tribute the card |
| c: this card (to be confirmed) |
| 50 | EFFECT_DESTROY_REPLACE | If the affected card would be destroyed, perform a given operation instead |
| 51 | EFFECT_RELEASE_REPLACE | If the affected card would be Tributed, perform a given operation instead |
| 52 | EFFECT_SEND_REPLACE | Card is sent to some location instead of another (Madolche Chateau) |
| 55 | EFFECT_CANNOT_DISCARD_HAND | Affected player cannot send cards from their hand to the graveyard. SetTarget receives the following parameters: -e: this effect itself -c: the card that would be discarded -re: the effect that would discard the cards -r: the reason for the discard |
| 56 | EFFECT_CANNOT_DISCARD_DECK | Affected player cannot send cards from their deck to the graveyard. SetTarget is not used in this effect |
| 57 | EFFECT_CANNOT_USE_AS_COST | The affected card cannot be used as Cost. Usually used as a single effect. Does not use SetTarget |
| 58 | EFFECT_CANNOT_PLACE_COUNTER | The affected player cannot place counters (See Gate Blocker). The SetTarget in this effect takes the following parameters: -e: this effect itself -c: the cards that cannot receive the counters (to be confirmed) -tp: the player that cannot place the counters -ctype: the type of the counter that cannot be placed -count: the ammount of counters that cannot be placed |
| 59 | EFFECT_CANNOT_TO_GRAVE_AS_COST | The affected card cannot be sent to the GY. |
| 60 | EFFECT_LEAVE_FIELD_REDIRECT | If the affected card would leave the field, sends it to another given location instead. The location must be set in SetValue |
| 61 | EFFECT_TO_HAND_REDIRECT | If the affected card would go to the hand, sends it to another given location instead. The location must be set in SetValue |
| 62 | EFFECT_TO_DECK_REDIRECT | If the affected card would go to the deck, sends it to another given location instead.  The location must be set in SetValue |
| 63 | EFFECT_TO_GRAVE_REDIRECT | If the affected card would go to the graveyard, sends it to another given location instead. The location must be set in SetValue |
| 64 | EFFECT_REMOVE_REDIRECT | If the affected card would be removed, sends it to another given location instead. The location must be set in SetValue. |
| 65 | EFFECT_CANNOT_TO_HAND | Affected card cannot be send to the hand. If it is used as a field effect, cards that return true for the SetTarget cannot be sent to the hand. SetTarget receives the following parameters: e: this effect itself c: the card that would be sent to the hand tp: the player that would send the card re: reason effect (defaults to core.reason_effect, to be confirmed) |
| 66 | EFFECT_CANNOT_TO_DECK | Affected card cannot be sent to the deck. If it is used as a field effect, cards that return true for the SetTarget cannot be sent to the hand. SetTarget receives the following parameters: e: this effect itself c: the card that would be sent to the Deck tp: the player that would send the card |
| 67 | EFFECT_CANNOT_REMOVE | Affected card cannot be banished. If it is used as a field effect, cards that return true for the SetTarget cannot be banished. SetTarget receives the following parameters: e: this effect itself c: the card that would be banished tp: the player that would banish re:the reason that would be applied to the banishing re: reason effect (defaults to core.reason_effect, to be confirmed) |
| 68 | EFFECT_CANNOT_TO_GRAVE | The affected card(s) cannot be sent to the Graveyard. If used as a field effect, only e and c are passed to SetTarget |
| 69 | EFFECT_CANNOT_TURN_SET | The affected card cannot be turned face-down ("Set"). If used as a field effect, only e and c are passed to SetTarget |
| 70 | EFFECT_CANNOT_BE_BATTLE_TARGET | The affected card cannot be targeted for an attack |
| 71 | EFFECT_CANNOT_BE_EFFECT_TARGET | Affected card cannot be targeted by card effects. When used as a single effect, SetTarget takes: e, re, rp |
| 72 | EFFECT_IGNORE_BATTLE_TARGET | Affected card cannot be targeted for an attack, but it doesn't prevent direct attack. |
| 73 | EFFECT_CANNOT_DIRECT_ATTACK | Affected card cannot attack directly |
| 74 | EFFECT_DIRECT_ATTACK | Affected card can make a direct attack. |
| 75 | EFFECT_DUAL_STATUS | Affected card is a Gemini Monster that has its effect |
| 76 | EFFECT_EQUIP_LIMIT | Equipment object restrictions |
| 77 | EFFECT_DUAL_SUMMONABLE | Affected card can be Normal Summon on the field as a Gemini Monster |
| 80 | EFFECT_REVERSE_DAMAGE | If the affected player would take damage, they gain that much LP instead. SetValue in this effect receives the following parameters: e: this effect itself re: reason effect r: reason rp: reason player rc: reason card |
| 81 | EFFECT_REVERSE_RECOVER | If the affected player would gain LP, they take that much damage instead. SetValue in this effect receives the following parameters: |
| e: this effect itself |
| r: reason |
| rp: reason player |
| 82 | EFFECT_CHANGE_DAMAGE | Modify the amount of damage the affected player would take |
| 83 | EFFECT_REFLECT_DAMAGE | If the affected player would take damage, their opponent takes damage instead. SetValue in this effect receives the following parameters: e: this effect itself amount: the amount of damage re: reason effect r: reason rp: reason player rc: reason card |
| 85 | EFFECT_CANNOT_ATTACK | Affected card cannot attack |
| 86 | EFFECT_CANNOT_ATTACK_ANNOUNCE | Affected card cannot declare attacks (but can finish conducting an attack responded to with this effect, Threatening Roar) |
| 87 | EFFECT_CANNOT_CHANGE_POS_E | Affected card's battle position cannot be changed by card effects (Raging Cloudian) |
| 90 | EFFECT_ACTIVATE_COST | Affected player must pay a cost to activate effects |
| 91 | EFFECT_SUMMON_COST | The affected player must pay a cost to Normal Summon. The parameters this effect's target receives are: e = this effect itself c = this card tp = the player that would summon |
| 92 | EFFECT_SPSUMMON_COST | The affected player must pay a cost to Special Summon. The parameters this effect's target receives are: e = this effect itself c = this card tp = the player that would summon sumtype = the type of the summon |
| 93 | EFFECT_FLIPSUMMON_COST | Affected player must pay a cost to Flip Summon. The parameters this effect's target receives are: e = this effect itself c = this card tp = the player that would summon |
| 94 | EFFECT_MSET_COST | The affected player must pay a cost to Set monsters. The parameters this effect's target receives are: e = this effect itself c = this card tp = the player that would set the monsters |
| 95 | EFFECT_SSET_COST | The affected player must pay a cost to Set Spell/Traps. The parameters this effect's target receives are: |
| e = this effect itself |
| c = this card |
| tp = the player that would Set the cards |
| 96 | EFFECT_ATTACK_COST | The affected player must pay a cost to attack. The parameters this effect's target receives are: |
| e = this effect itself |
| c = this card |
| tp = the player that would attack |
| 100 | EFFECT_UPDATE_ATTACK | Changes the ATK of a monster by a value (taken from the return in Effect.SetValue()) |
| 101 | EFFECT_SET_ATTACK | Sets the current ATK of a monster to a value evaluated in Effect.SetValue() |
| 102 | EFFECT_SET_ATTACK_FINAL | Set the attack of a monster, overriding other changes  (taken from the return in Effect.SetValue()) |
| 103 | EFFECT_SET_BASE_ATTACK | Set the original attack of a monster |
| 104 | EFFECT_UPDATE_DEFENSE | Change the defense of a monster by a value (written into Effect.SetValue()) |
| 105 | EFFECT_SET_DEFENSE | Set the defense of a monster |
| 106 | EFFECT_SET_DEFENSE_FINAL | Set the defense of a monster, overriding other changes (written into Effect.SetValue()) |
| 107 | EFFECT_SET_BASE_DEFENSE | Set the original defense of a monster |
| 108 | EFFECT_REVERSE_UPDATE | Any change to ATK and DEF is reversed (For the effects of 'Reverse Trap') |
| 109 | EFFECT_SWAP_AD | Swap the affected card's ATK and DEF |
| 110 | EFFECT_SWAP_BASE_AD | Swap the affected card's original ATK and DEF |
| 111 | EFFECT_SWAP_ATTACK_FINAL | Set the final attack (used to exchange offensive and defensive) |
| 112 | EFFECT_SWAP_DEFENSE_FINAL | Set the final defense (for exchange of offensive and defensive) |
| 113 | EFFECT_ADD_CODE | Treats a Card(s) as another Card by adding one additional Code (ID) to it (written into Effect.SetValue()) |
| 114 | EFFECT_CHANGE_CODE | Treats a Card(s) as one different Card by overwriting its Code(s) (ID(s)) it currently has (written into Effect.SetValue()) |
| 115 | EFFECT_ADD_TYPE | Treats a Card(s) as a additional type(s) (written into Effect.SetValue()) |
| 116 | EFFECT_REMOVE_TYPE | Treats a Card(s) as not a type(s) (written into Effect.SetValue()) |
| 117 | EFFECT_CHANGE_TYPE | Treats a Card(s) as another type overwriting its type (written into Effect.SetValue()) |
| 118 | EFFECT_REMOVE_CODE |
| 120 | EFFECT_ADD_RACE | Treats a Card(s) as a additional race(s) (written into Effect.SetValue()) |
| 121 | EFFECT_REMOVE_RACE | Treats a Card(s) as not a race(s) (written into Effect.SetValue()) |
| 122 | EFFECT_CHANGE_RACE | Treats a Card(s) as another type overwriting its type (written into Effect.SetValue()) |
| 125 | EFFECT_ADD_ATTRIBUTE | Treats a Card(s) as a additional element(s) (written into Effect.SetValue()) |
| 126 | EFFECT_REMOVE_ATTRIBUTE | Treats a Card(s) as not a element(s) (written into Effect.SetValue()) |
| 127 | EFFECT_CHANGE_ATTRIBUTE | Treats a Card(s) as another element overwriting its element (written into Effect.SetValue()) |
| 130 | EFFECT_UPDATE_LEVEL | Increase/decrease affected card's level by a value (written into Effect.SetValue()) |
| 131 | EFFECT_CHANGE_LEVEL | Set affected card's level to a value (written into Effect.SetValue()) |
| 132 | EFFECT_UPDATE_RANK | Increase/decrease affected card's rank by a value (written into Effect.SetValue()) |
| 133 | EFFECT_CHANGE_RANK | Set affected card's rank to a value (written into Effect.SetValue()) |
| 134 | EFFECT_UPDATE_LSCALE | Increase/decrease affected card's left pendulum scale (blue scale) by a value (written into Effect.SetValue()) |
| 135 | EFFECT_CHANGE_LSCALE | Set affected card's left pendulum scale (blue scale) to a value (written into Effect.SetValue()) |
| 136 | EFFECT_UPDATE_RSCALE | Increase/decrease affected card's right pendulum scale (red scale) by a value (written into Effect.SetValue()) |
| 137 | EFFECT_CHANGE_RSCALE | Set affected card's right pendulum scale (red scale) to a value (written into Effect.SetValue()) |
| 140 | EFFECT_SET_POSITION | Set affected card's battle position to a given value |
| 141 | EFFECT_SELF_DESTROY | Affected card destroys itself |
| 142 | EFFECT_SELF_TOGRAVE | Affected card sends itself to the graveyard, requires enabling GLOBALFLAG_SELF_TOGRAVE |
| 150 | EFFECT_DOUBLE_TRIBUTE | Treats a card as 2 tributes for a tribute summon |
| 151 | EFFECT_DECREASE_TRIBUTE | Decreases the ammount of tributes to perform a Tribute Summon |
| 152 | EFFECT_DECREASE_TRIBUTE_SET | Decreases the ammount of tributes to perform a Tribute Set |
| 153 | EFFECT_EXTRA_RELEASE | The affected card must be used when performing a tribute (Soul Exchange) |
| 154 | EFFECT_TRIBUTE_LIMIT | The affected card has restriction for the tribute summon |
| 155 | EFFECT_EXTRA_RELEASE_SUM | Allows, optionally, to tributed the affected card (Monarch's Stormforth, Vampire Sucker) |
| 156 | EFFECT_TRIPLE_TRIBUTE | Treats a card as 2 and 3 tributes for a tribute summon |
| 157 | EFFECT_ADD_EXTRA_TRIBUTE | The affected card can use as tribute other cards (than the default ones). Requires SetTargetRange and SetTarget |
| 158 | EFFECT_EXTRA_RELEASE_NONSUM | The affected card can be tributed (by a cost ?) even if it is controled by the opponent. SetValue in this effect receives the following parameters: e: this effect itself re: reason effect (to be confirmed: defaults to core.reason_effect) rp: reason player(to be confirmed: defaults to core.reason_player) |
| 160 | EFFECT_PUBLIC | Affected card becomes public knowledge |
| 0x10000 | EFFECT_COUNTER_PERMIT | Allow placement of counter type |
| 0x20000 | EFFECT_COUNTER_LIMIT | Allowed to place the number of counters |
| 0x30000 | EFFECT_RCOUNTER_REPLACE | Instead of removing the counter |
| 170 | EFFECT_LPCOST_CHANGE | Modify the amount of LP a given player must pay for a cost |
| 171 | EFFECT_LPCOST_REPLACE | If the affected player would pay LP for a cost, perform a given operation instead |
| 180 | EFFECT_SKIP_DP | Skip affected player's draw phase (used with SetTargetRange(tp value,1-tp value), 0 for not affected, 1 for affect) |
| 181 | EFFECT_SKIP_SP | Skip affected player's standby phase (used with SetTargetRange(tp value,1-tp value), 0 for not affected, 1 for affect) |
| 182 | EFFECT_SKIP_M1 | Skip affected player's main phase 1 (used with SetTargetRange(tp value,1-tp value), 0 for not affected, 1 for affect) |
| 183 | EFFECT_SKIP_BP | Skip affected player's battle phase (used with SetTargetRange(tp value,1-tp value), 0 for not affected, 1 for affect) |
| 184 | EFFECT_SKIP_M2 | Skip affected player's main phase 2 (used with SetTargetRange(tp value,1-tp value), 0 for not affected, 1 for affect) |
| 185 | EFFECT_CANNOT_BP | The affected player cannot enter the Battle Phase |
| 186 | EFFECT_CANNOT_M2 | The affected player cannot enter the Main Phase 2 |
| 187 | EFFECT_CANNOT_EP | The affected player cannot enter the End Phase |
| 188 | EFFECT_SKIP_TURN | The affected player's whole next turn is skipped |
| 189 | EFFECT_SKIP_EP | The affected player's End Phase is skipped |
| 190 | EFFECT_DEFENSE_ATTACK | Affected card can attack while in defense position. The stats it uses depends on Effect.Setvalue (if any), where it applies DEF if effect value is 1 and atk if it is 0 or doesn't exist. |
| 191 | EFFECT_MUST_ATTACK | Affected card must attack if able |
| 192 | EFFECT_FIRST_ATTACK | Affected card must attack before its controller's other monsters |
| 193 | EFFECT_ATTACK_ALL | Affected card can attack all valid attack targets once each. SetValue receives the following parameters: e: this effect itself c: the cards that can be attack target |
| 194 | EFFECT_EXTRA_ATTACK | Affected card can make a given number of additional attacks |
| 196 | EFFECT_ONLY_BE_ATTACKED | Only the affected card can be attacked |
| 197 | EFFECT_ATTACK_DISABLED | The affected card's attack has been negated (shows application of Duel.NegateAttack() ) |
| 198 | EFFECT_CHANGE_BATTLE_STAT | Changes the values used to calculate damage, during damage calculation only. Doesnt actually change the values, only what is calculated |
| 200 | EFFECT_NO_BATTLE_DAMAGE | No battle damage is dealt when the affected card battles |
| 201 | EFFECT_AVOID_BATTLE_DAMAGE | The controller of the affected card does not take battle damage when it battles |
| 202 | EFFECT_REFLECT_BATTLE_DAMAGE | If the controller of the affected card would take battle damage from a battle involving that card, the opponent takes the damage |
| 203 | EFFECT_PIERCE | The affected monster deals piercing battle damage |
| 204 | EFFECT_BATTLE_DESTROY_REDIRECT | If the affected card is destroyed by battle, send it to a given location |
| 205 | EFFECT_BATTLE_DAMAGE_TO_EFFECT | The affected card deals effect damage when it battles (Gravekeeper's Vassal) |
| 206 | EFFECT_BOTH_BATTLE_DAMAGE | Both players take the battle damage. See Double-Edged Sword |
| 207 | EFFECT_ALSO_BATTLE_DAMAGE | The opponent also takes the battle damage. See Lyrilusc - Recital Starling |
| 208 | EFFECT_CHANGE_BATTLE_DAMAGE |
| 220 | EFFECT_TOSS_COIN_REPLACE | If an effect requires a coin toss, replace it with a given result instead |
| 221 | EFFECT_TOSS_DICE_REPLACE | If an effect requires a dice roll, replace it with a given result instead |
| 222 | EFFECT_TOSS_COIN_CHOOSE |
| 223 | EFFECT_TOSS_DICE_CHOOSE |
| 230 | EFFECT_FUSION_MATERIAL | Can be used as Fusion material |
| 231 | EFFECT_CHAIN_MATERIAL | When Fusion Summoning, the affected player can banish materials from the hand, field, deck or graveyard instead (Chain Material) |
| 232 | EFFECT_SYNCHRO_MATERIAL | Can be used as Synchro material |
| 233 | EFFECT_XYZ_MATERIAL | Can be used as Xyz material |
| 234 | EFFECT_FUSION_SUBSTITUTE | When Fusion Summoning, the affected card can be used to substitute for any specifically named material |
| 235 | EFFECT_CANNOT_BE_FUSION_MATERIAL | Affected card cannot be used as Fusion material |
| 236 | EFFECT_CANNOT_BE_SYNCHRO_MATERIAL | Affected card cannot be used as Synchro material. SetValue takes the following parameters: |
| e: this effect |
| c: the card(s) for which this card cannot be used as material |
| 237 | EFFECT_SYNCHRO_MATERIAL_CUSTOM | Coexistence of material constraints |
| 238 | EFFECT_CANNOT_BE_XYZ_MATERIAL | Affected card cannot be used as Xyz material. SetValue takes the following parameters: e: this effect c: the card(s) for which this card cannot be used as material |
| 239 | EFFECT_CANNOT_BE_LINK_MATERIAL | Cannot be used as Link Material. SetValue takes the following parameters: e: this effect c: the card(s) for which this card cannot be used as material |
| 240 | EFFECT_SYNCHRO_LEVEL | Affected card can be treated as a given level if used for a Synchro Summon |
| 241 | EFFECT_RITUAL_LEVEL | Affected card can be treated as a given level if used for a Ritual Summon |
| 242 | EFFECT_XYZ_LEVEL | Affected card can be treated as a given level if used for an Xyz Summon |
| 243 | EFFECT_EXTRA_RITUAL_MATERIAL | Affected card can be used for a Ritual Summon in addition to what the Ritual Spell states (e.g. Sphere Kuriboh). If used as EFFECT_FLAG_SINGLE_RANGE, use SetValue , which takes the following parameters: e: this effect rc: the monster that would be summoned using this card. If used as EFFECT_TYPE_FIELD, SetValue is not considered. SetTarget should be used instead, which takes the following parameters: e: this effect c: the card(s) that can be used as extra ritual materials (the cards affected by this effect) |
| 244 | EFFECT_NONTUNER | Affected card can be treated as a non-Tuner despite being a Tuner (Phantom King Hydride). When used as a single effect, SetValue receives the following parameters: e: this effect sc: the monster that would use this card as material |
| 245 | EFFECT_OVERLAY_REMOVE_REPLACE | Replaces detaching Xyz materials from monsters by some other operation. SetCondition must be used to match the exact effects that can be replaced. SetOperation must return something. |
| 248 | EFFECT_CANNOT_BE_MATERIAL | The card cannot be used as material. Requires the summon type for which the material can't be used to be defined via SetValue. SetValue takes the following parameters: -sum_type -playerid |
| 250 | EFFECT_PRE_MONSTER | Can access the monster's value (Card.AddMonsterAttribute () only) |
| 251 | EFFECT_MATERIAL_CHECK | Applies a check to the materials used. The SetValue in this effect takes as parameter e and c |
| 260 | EFFECT_DISABLE_FIELD | Given card zones cannot be used. The zones affected must be defined via SetOperation |
| 261 | EFFECT_USE_EXTRA_MZONE | Card uses an additional Monster zone |
| 262 | EFFECT_USE_EXTRA_SZONE | Card uses an additional Spell/Trap zone |
| 263 | EFFECT_MAX_MZONE | The maximum number of monsters |
| 264 | EFFECT_MAX_SZONE | Maximum number of Spell/Trap zone |
| 265 | EFFECT_FORCE_MZONE | Forces a zone to be used (see Dai Dance).The target function of this effect receives the following parameters: e = this effect (EFFECT_FORCE_MZONE) c = the card that would be affected by it (the ones that cannot be Special Summoned) playerid = the player that would do the summon sumtype = the type of the summon toplayer = the player that would receive the monster sumef = the effect that would summon |
| 266 | EFFECT_BECOME_LINKED_ZONE | Makes a zone linked |
| 270 | EFFECT_HAND_LIMIT | Change the maximum number of cards the affected player can have in their hand during the End Phase. The new value should be provided via SetValue. |
| 271 | EFFECT_DRAW_COUNT | Change the number of cards the affected player draws for their Draw Phase |
| 280 | EFFECT_SPIRIT_DONOT_RETURN | Affected card does not return to the hand in the End Phase even if a Spirit Monster |
| 281 | EFFECT_SPIRIT_MAYNOT_RETURN | Affected card optionally may not return to the hand in the End Phase even if a Spirit Monster |
| 290 | EFFECT_CHANGE_ENVIRONMENT | The active Field Spell is treated as a given card if none exists (Maiden of the Aqua, Gravekeeper's Priestess) |
| 291 | EFFECT_NECRO_VALLEY | Cannot affect cards in the Graveyard (Necrovalley) |
| 292 | EFFECT_FORBIDDEN | Card cannot be used (Prohibition, Psi-Blocker) |
| 293 | EFFECT_NECRO_VALLEY_IM | Affected card is unaffected by the effects of Necrovalley |
| 294 | EFFECT_REVERSE_DECK | Flip affected player's deck upside-down, used with GLOBALFLAG_DECK_REVERSE_CHECK, set the player afected with SetTargetRange(,) |
| 295 | EFFECT_REMOVE_BRAINWASHING | Control of all monsters is returned to their owner |
| 296 | EFFECT_BP_TWICE | The affected player can conduct two Battle Phases (e.g. Weather Report) |
| 297 | EFFECT_UNIQUE_CHECK | There can only be one on the field (Card.SetUniqueOnField () only) |
| 300 | EFFECT_MATCH_KILL | When the affected card reduces its controller's opponent's LP to 0 by a direct attack, its controller wins the match. |
| 310 | EFFECT_SYNCHRO_CHECK | Genomix Fighter |
| 311 | EFFECT_QP_ACT_IN_NTPHAND | A Quick Play Spell affected can be activated from the hand during the turn of the opponent's turn |
| 312 | EFFECT_MUST_BE_SMATERIAL | Deprecated. Use EFFECT_MUST_BE_MATERIAL with REASON_SYNCHRO in the SetValue |
| 313 | EFFECT_TO_GRAVE_REDIRECT_CB | If the affected card would be sent to the graveyard, executes another operation instead (Crystal Beast monsters) |
| 314 | EFFECT_CHANGE_LEVEL_FINAL | Set affected card's level to a value, overriding other changes |
| 315 | EFFECT_CHANGE_RANK_FINAL | Set affected card's rank to a value, overriding other changes |
| 316 | EFFECT_MUST_BE_FMATERIAL | Deprecated. Use EFFECT_MUST_BE_MATERIAL with REASON_FUSION in the SetValue |
| 317 | EFFECT_MUST_BE_XMATERIAL | Deprecated. Use EFFECT_MUST_BE_MATERIAL with REASON_XYZ in the SetValue |
| 318 | EFFECT_MUST_BE_LMATERIAL | Deprecated. Use EFFECT_MUST_BE_MATERIAL with REASON_LINK in the SetValue |
| 320 | EFFECT_SPSUMMON_PROC_G | Pendulum Summon rules (e.g. Harmonic Oscilation) |
| 330 | EFFECT_SPSUMMON_COUNT_LIMIT | Limit for the number of Special Summons |
| 331 | EFFECT_LEFT_SPSUMMON_COUNT | The remaining number of Summoning (e.g Summon Breaker) |
| 332 | EFFECT_CANNOT_SELECT_BATTLE_TARGET | The affected cards cannot be chosen to be an attack target |
| 333 | EFFECT_CANNOT_SELECT_EFFECT_TARGET | The affected cards cannot activate their effects that target. SetValue takes the following parameters: e: this effect re: the effect that would be activated c: the cards that cannot activate the effect |
| 334 | EFFECT_ADD_SETCODE | Adds a setcode (archetype) to the affected card |
| 335 | EFFECT_NO_EFFECT_DAMAGE | The affected player does not take damage from card effects |
| 336 | EFFECT_UNSUMMONABLE_CARD | The affected card cannot be Normal Summoned |
| 337 | EFFECT_DISABLE_CHAIN_FIELD | Deprecated and removed effect. See core's "effect.h" |
| 338 | EFFECT_DISCARD_COST_CHANGE | Counter trap cards cost change (Guilding Ariadne) |
| 339 | EFFECT_HAND_SYNCHRO | Can Synchro Summon using monsters in the hand (e.g. Tatsunoko) |
| 343 | EFFECT_ONLY_ATTACK_MONSTER | Affected card can only attack monster. |
| 344 | EFFECT_MUST_ATTACK_MONSTER | Affected card must attack a monster, if abble. |
| 345 | EFFECT_PATRICIAN_OF_DARKNESS | The affected player chooses the targets of their opponent's attacks |
| 346 | EFFECT_EXTRA_ATTACK_MONSTER | Affected card can make a given number of additional attacks on monsters |
| 347 | EFFECT_UNION_STATUS |
| 348 | EFFECT_OLDUNION_STATUS |
| 349 | EFFECT_REMOVE_SETCODE |
| 350 | EFFECT_CHANGE_SETCODE  | The affected card's setcode is changed to the new value, replacing the SetCode(s) it currently has |
| 351 | EFFECT_ALWAYS_ATTACK | Deprecated and removed effect. See core's "effect.h" |
| 352 | EFFECT_EXTRA_FUSION_MATERIAL | Allows using affected cards as Fusion Materials |
| 354 | EFFECT_ADD_LINK_CODE | Deprecated and removed effect. See core's "effect.h". Add a code (ID/name) for the affected monster to have if used for a Link Summon |
| 355 | EFFECT_ADD_LINK_SETCODE | Deprecated and removed effect. See core's "effect.h". Add a setcode (archetype) for the affected monster to have if used for a Link Summon |
| 358 | EFFECT_EXTRA_MATERIAL | Deprecated and removed effect. See core's "effect.h". Allows the use of an extra material in a group of materials to summon a monster (e.g. "Micro Coder). This effect is not defined in the core. See the utility for its implementation |
| 361 | EFFECT_IRON_WALL |
| 400 | EFFECT_CANNOT_LOSE_DECK | Prevent losing via Deckout |
| 401 | EFFECT_CANNOT_LOSE_LP | Prevent losing while LP is 0 |
| 402 | EFFECT_CANNOT_LOSE_EFFECT | Prevent losing via card effects |
| 403 | EFFECT_BP_FIRST_TURN | Allows entering Battle Phase during the first turn |
| 404 | EFFECT_UNSTOPPABLE_ATTACK | Prevents the affected monster's attack from being negated |
| 405 | EFFECT_ALLOW_NEGATIVE | Allows the affected card to have negative levels |
| 406 | EFFECT_SELF_ATTACK | Allows players to attack themselves using monsters they control |
| 407 | EFFECT_BECOME_QUICK | The affected Spell cards can be played like Quick-Play spells |
| 408 | EFFECT_LEVEL_RANK | Gives Rank to an affected monster with a Level |
| 409 | EFFECT_RANK_LEVEL | Gives Level to an affected monster with a Rank |
| 410 | EFFECT_LEVEL_RANK_S | Gives Rank to an affected monster with a Level, Level and Rank are always synced. |
| 411 | EFFECT_RANK_LEVEL_S | Gives Level to an affected monster with a Rank, Level and Rank are always synced. |
| 420 | EFFECT_UPDATE_LINK | Increase/decrease affected card's Link Value by a value (written into Effect.SetValue()) |
| 421 | EFFECT_CHANGE_LINK | Set affected card's Link Value by a value (written into Effect.SetValue()) |
| 422 | EFFECT_CHANGE_LINK_FINAL | Set affected card's Link Value to a value, overriding other changes |
| 423 | EFFECT_ADD_LINKMARKER | Add Link Markers to the affected card |
| 424 | EFFECT_REMOVE_LINKMARKER | Remove Link Markers from the affected card |
| 425 | EFFECT_CHANGE_LINKMARKER | Set's the affected card's Link Markers to the value provided |
| 426 | EFFECT_FORCE_NORMAL_SUMMON_POSITION |
| 427 | EFFECT_FORCE_SPSUMMON_POSITION | This effect's SetTarget takes the following parameters: eff, pcard, playerid, sumtype, sumpos, toplayer, peffect |
| 428 | EFFECT_DARKNESS_HIDE | The affect players cannot see/confirm their face-down cards |
| 73941492+TYPE_FUSION | EFFECT_FUSION_MAT_RESTRICTION | 73941492+TYPE_FUSION. Used by the Fusion Summon procedure as an implementation of Harmonizing Magician's effect |
| 73941492+TYPE_SYNCHRO | EFFECT_SYNCHRO_MAT_RESTRICTION | 73941492+TYPE_SYNCHRO. Used by the Synchro Summon procedure as an implementation of Harmonizing Magician's effect |
| 73941492+TYPE_XYZ | EFFECT_XYZ_MAT_RESTRICTION | 73941492+TYPE_XYZ. Used by the XyzSummon procedure as an implementation of Harmonizing Magician's effect |


### Events
| Value | Name | Description |
| --- | --- | --- |
| 1000 | EVENT_STARTUP | This event is raised once, at the start of the duel |
| 1001 | EVENT_FLIP | This event is raised when a card is flipped face-up |
| 1002 | EVENT_FREE_CHAIN | An event that describes a timing at any valid response window or open game state |
| 1010 | EVENT_DESTROY | This event is raised when a card is destroyed |
| 1011 | EVENT_REMOVE | This event is raised when a card is banished |
| 1012 | EVENT_TO_HAND | This event is raised when a card is sent to the hand (includes draw, search and return) |
| 1013 | EVENT_TO_DECK | This event is raised when a card is sent to the deck |
| 1014 | EVENT_TO_GRAVE | This event is raised whenn a card is sent to the graveyard |
| 1015 | EVENT_LEAVE_FIELD | This event is raised when a card leaves the field |
| 1016 | EVENT_CHANGE_POS | This event is raised when a card changes battle position |
| 1017 | EVENT_RELEASE | This event is raised when a card is Tributed (includes tributing for a tribute summon, tributing by an effect and tributing by costs) |
| 1018 | EVENT_DISCARD | This event is raised when a card is discarded |
| 1019 | EVENT_LEAVE_FIELD_P | This event is raised when a card would leave the field (but before it actually leaves, so it still contains info on the field). Example of usage: in "Predaplanet", it is used to check if the card has Predacounters imediatelly before it leaves the field. |
| 1020 | EVENT_CHAIN_SOLVING | This event is raised when a Chain Link is resolving |
| 1021 | EVENT_CHAIN_ACTIVATING | This event is raised when a Chain Link is activating |
| 1022 | EVENT_CHAIN_SOLVED | This event is raised after a Chain Link resolves |
| 1024 | EVENT_CHAIN_NEGATED | This event is raised when a chain link has its activation negated (after EVENT_CHAIN_ACTIVATING) |
| 1025 | EVENT_CHAIN_DISABLED | This event is raised when the effect of a Chain Link is negated |
| 1026 | EVENT_CHAIN_END | This event is raised when a Chain has fully resolved |
| 1027 | EVENT_CHAINING | This event is raised when a chain is being built |
| 1028 | EVENT_BECOME_TARGET | This event is raised when a card is targeted for an effect |
| 1029 | EVENT_DESTROYED | This event is raised after a card is destroyed |
| 1030 | EVENT_MOVE | This event is raised when a card moves from one location or sequence to another |
| 1040 | EVENT_ADJUST | This event is raised when the game state changes (effectively working as some sort of EVENT_ANYCHANGE) |
| 1100 | EVENT_SUMMON_SUCCESS | This event is raised when a monster is successfully Normal Summoned (which is timing for cards like Trap Hole) |
| 1101 | EVENT_FLIP_SUMMON_SUCCESS | This event is raised when a monster is successfully Flip Summoned (which is timing for cards like Trap Hole) |
| 1102 | EVENT_SPSUMMON_SUCCESS | This event is raised when a monster is successfully Special Summoned  (which is timing for cards like Torrential Tribute) |
| 1103 | EVENT_SUMMON | This event is raised when a monster is being Normal Summoned (this is an attempt to perform a Normal Summon, aka "when a monster would be Summoned", for example, Bending Destiny's timing) |
| 1104 | EVENT_FLIP_SUMMON | This event is raised when a monster is being Flip Summoned (this is an attempt to perform a Flip Summon, for example, Solemn Warning's timing) |
| 1105 | EVENT_SPSUMMON | This event is raised when a monster is being Special Summoned (this is an attempt to perform a Special Summon, aka "when a monster would be Special Summoned", for example, Solemn Strike's timing) |
| 1106 | EVENT_MSET | This event is raised when a monster is Set |
| 1107 | EVENT_SSET | This event is raised when a Spell/Trap is set |
| 1108 | EVENT_BE_MATERIAL | This event is raised when a card is used as material (e.g. for a Synchro Summon) |
| 1109 | EVENT_BE_PRE_MATERIAL | Will be used as a fusion / ceremony of the same tune / excessive material |
| 1110 | EVENT_DRAW | This event is raised when a card is drawn |
| 1111 | EVENT_DAMAGE | This event is raised when a player takes damage, either by battle or by a card effect. |
| 1112 | EVENT_RECOVER | When LP is gained |
| 1113 | EVENT_PREDRAW | At the start of the Draw Phase |
| 1114 | EVENT_SUMMON_NEGATED | This event is raised when a Summon is negated, to be detected by Witch's Strike. |
| 1115 | EVENT_FLIP_SUMMON_NEGATED | This event is raised when a Flip Summon is negated |
| 1116 | EVENT_SPSUMMON_NEGATED | This event is raised when a Special Summon is negated |
| 1120 | EVENT_CONTROL_CHANGED | When control of a card changes |
| 1121 | EVENT_EQUIP | This event is raised when a card is equipped |
| 1130 | EVENT_ATTACK_ANNOUNCE | This event is raised when an attack is declared |
| 1131 | EVENT_BE_BATTLE_TARGET | This event is raised when a monster is targeted for an attack |
| 1132 | EVENT_BATTLE_START | The start of the damage step |
| 1133 | EVENT_BATTLE_CONFIRM | This event is raised when a monster battles another monster |
| 1134 | EVENT_PRE_DAMAGE_CALCULATE | Before the damage calculation |
| 1136 | EVENT_PRE_BATTLE_DAMAGE | Before battle damage applies |
| 1138 | EVENT_BATTLED | After battle |
| 1139 | EVENT_BATTLE_DESTROYING | This event is raised when a monster is destroyed by battle |
| 1140 | EVENT_BATTLE_DESTROYED | This event is raised after a monster is destroyed by battle |
| 1141 | EVENT_DAMAGE_STEP_END | At the end of the Damage Step |
| 1142 | EVENT_ATTACK_DISABLED | This event is raised when an attack is negated |
| 1143 | EVENT_BATTLE_DAMAGE | This event is raised when battle damage is taken |
| 1150 | EVENT_TOSS_DICE | This event is raised when dice are rolled |
| 1151 | EVENT_TOSS_COIN | This event is raised when coins are flipped |
| 1152 | EVENT_TOSS_COIN_NEGATE | This event is raised when coin tosses happen again, replacing previous result |
| 1153 | EVENT_TOSS_DICE_NEGATE | This event is raised when dice are re-rolled |
| 1200 | EVENT_LEVEL_UP | This event is raised when the level of monster increases (might also be raised for general level changes, but only for single effect. check the core's implementation for details) |
| 1201 | EVENT_PAY_LPCOST | This event is raised when LP is paid as a cost |
| 1202 | EVENT_DETACH_MATERIAL | This event is raised when Xyz materials are detached (only the card that detaches the materials is availble in the event group, not the detached cards) |
| 1203 | EVENT_RETURN_TO_GRAVE | Deprecated and removed event. See core's "effect.h". Card is being returned to the Graveyard |
| 1210 | EVENT_TURN_END | This event is raised when the turn ends |
| 0x1000 | EVENT_PHASE | This event is raised when a certain phase is reached (the required Phase value must be added to it, for example EVENT_PHASE+PHASE_END) |
| 0x2000 | EVENT_PHASE_START | This event is raised at the start of a certain phase (the required Phase value must be added to it) |
| 0x10000 | EVENT_ADD_COUNTER | This event is raised when a counter is placed on cards |
| 0x20000 | EVENT_REMOVE_COUNTER | This event is raised when a counter is removed from cards |
| 0xx10000000 | EVENT_CUSTOM | For custom events (Eg. Activate an effect of a card indicating EVENT_CUSTOM + <code of the card> in Duel.RaiseEvent) |

### Categories, hints and card hints
| Value | Name | Description |
| --- | --- | --- |
| 0x1 | CATEGORY_DESTROY | Describes that an effect destroys cards |
| 0x2 | CATEGORY_RELEASE | Describes that an effect tributes |
| 0x4 | CATEGORY_REMOVE | Describes that an effect banishes |
| 0x8 | CATEGORY_TOHAND | Describes that an effect adds a card to the hand (from any location) |
| 0x10 | CATEGORY_TODECK | Describes that an effect adds a card to the Deck (from any location) |
| 0x20 | CATEGORY_TOGRAVE | Describes that an effect sends a card to the Graveyard (from any location) |
| 0x40 | CATEGORY_DECKDES | Describes that an effect removes a card(s) from the Deck (to move them to the Graveyard or to banish them) |
| 0x80 | CATEGORY_HANDES | Describes that an effect removes a card(s) from the hand (to move them to the Graveyard or to banish them) |
| 0x100 | CATEGORY_SUMMON | Describes that an effect Normal Summons a monster(s) |
| 0x200 | CATEGORY_SPECIAL_SUMMON | Describes that an effect Special Summons a monster(s) |
| 0x400 | CATEGORY_TOKEN | Describes that an effect Special Summons a token(s) |
| 0x800 | CATEGORY_FLIP | Describes a FLIP effect |
| 0x1000 | CATEGORY_POSITION | Describes an effect that changes a card's battle position |
| 0x2000 | CATEGORY_CONTROL | Describes that an effect takes or switches control |
| 0x4000 | CATEGORY_DISABLE | Describes an effect that negates a card effect (not an effect's activation) |
| 0x8000 | CATEGORY_DISABLE_SUMMON | Describes an effect that negates the summon of a monster |
| 0x10000 | CATEGORY_DRAW | Describes that a card draws |
| 0x20000 | CATEGORY_SEARCH | Describes that a card searches |
| 0x40000 | CATEGORY_EQUIP | Describes that a card equips |
| 0x80000 | CATEGORY_DAMAGE | Describes that a card deals damage |
| 0x100000 | CATEGORY_RECOVER | Describes that a card recovers life points |
| 0x200000 | CATEGORY_ATKCHANGE | Describes that a card changes ATK |
| 0x400000 | CATEGORY_DEFCHANGE | Describes that a card changes DEF |
| 0x800000 | CATEGORY_COUNTER | Describes an effect that places Counters |
| 0x1000000 | CATEGORY_COIN | Describes that a card uses a coin |
| 0x2000000 | CATEGORY_DICE | Describes that a card uses a dice |
| 0x4000000 | CATEGORY_LEAVE_GRAVE | Describes an effect that causes a card to leave the Graveyard |
| 0x8000000 | CATEGORY_LVCHANGE | Describes an effect that changes a card's level |
| 0x10000000 | CATEGORY_NEGATE | Describes an effect that negates the activation of an effect |
| 0x20000000 | CATEGORY_ANNOUNCE | Describes an effect that requires declaring a card name |
| 0x40000000 | CATEGORY_FUSION_SUMMON | Describes an effect that Fusion Summons |
| 0x80000000 | CATEGORY_TOEXTRA | Describes an effect that sends/return a card to the Extra Deck |
| 1 | HINT_EVENT | used by the core |
| 2 | HINT_MESSAGE |
| 3 | HINT_SELECTMSG | The message that appears when the given player next selects a card |
| 4 | HINT_OPSELECTED | The message that appears on screen to tell a player which option their opponent selected |
| 5 | HINT_EFFECT |
| 6 | HINT_RACE | Called when selecting/declaring a monster type |
| 7 | HINT_ATTRIB | Called when selecting/declaring an attribute |
| 8 | HINT_CODE | Used with "Booster Draft Duel" |
| 9 | HINT_NUMBER | Called when a player has to pick/declare a number |
| 10 | HINT_CARD | Called when you need to display the picture of the card (Trickstar Lycoris) |
| 11 | HINT_ZONE | To be used when the player selects a zone (e.g. Dai Dance). |
| 200 | HINT_SKILL | Sets the code of a skill card. If it is called first, the skill is created face-up. |
| 201 | HINT_SKILL_COVER | Sets the cover and id for a skill card. Cover is  value & 0xffffffff, code is (value>>32) & 0xffffffff. If  it iscalled first, the skill is created face-down. |
| 202 | HINT_SKILL_FLIP | Changes the position of the skill face-down/face-up, updating the code as well. The code is value&0xffffffff. 0x100000000 is face-up and 0x200000000 is face-down. |
| 203 | HINT_SKILL_REMOVE |
| 1 | CHINT_TURN |
| 2 | CHINT_CARD |
| 3 | CHINT_RACE |
| 4 | CHINT_ATTRIBUTE |
| 5 | CHINT_NUMBER |
| 6 | CHINT_DESC_ADD |
| 7 | CHINT_DESC_REMOVE |
| 6 | PHINT_DESC_ADD |
| 7 | PHINT_DESC_REMOVE |


### OPCodes
See the definition of opcode [here](https://en.m.wikipedia.org/wiki/Opcode).
| Value | Name | Description |
| --- | --- | --- |
| 0x40000000 | OPCODE_ADD | Operation of addition, to be used in an AnnounceCard filter. |
| 0x40000001 | OPCODE_SUB | Operation of subtraction, to be used in an AnnounceCard filter. |
| 0x40000002 | OPCODE_MUL | Operation of multiplication, to be used in an AnnounceCard filter. |
| 0x40000003 | OPCODE_DIV | Operation of division, to be used in an AnnounceCard filter. |
| 0x40000004 | OPCODE_AND | Operation of logical AND, to be used in an AnnounceCard filter. |
| 0x40000005 | OPCODE_OR | Operation of logical OR, to be used in an AnnounceCard filter. |
| 0x40000006 | OPCODE_NEG | Operation of bitwise negation, to be used in an AnnounceCard filter. |
| 0x40000007 | OPCODE_NOT | Operation of changing sign (+/-), to be used in an AnnounceCard filter. |
| 0x40000008 | OPCODE_BAND |
| 0x40000009 | OPCODE_BOR |
| 0x40000010 | OPCODE_BNOT |
| 0x40000011 | OPCODE_BXOR |
| 0x40000012 | OPCODE_LSHIFT |
| 0x40000013 | OPCODE_RSHIFT |
| 0x40000014 | OPCODE_ALLOW_ALIASES |
| 0x40000015 | OPCODE_ALLOW_TOKENS |
| 0x40000100 | OPCODE_ISCODE | Operation of the function Card.IsCode, to be used in an AnnounceCard filter. |
| 0x40000101 | OPCODE_ISSETCARD | Operation of the function Card.IsSetCard, to be used in an AnnounceCard filter. |
| 0x40000102 | OPCODE_ISTYPE | Operation of the function Card.IsType, to be used in an AnnounceCard filter. |
| 0x40000103 | OPCODE_ISRACE | Operation of the function Card.IsRace, to be used in an AnnounceCard filter. |
| 0x40000104 | OPCODE_ISATTRIBUTE | Operation of the function Card.IsAttribute, to be used in an AnnounceCard filter. |
| 0x40000105 | OPCODE_GETCODE | Operation of the function Card.GetCode, to be used in an AnnounceCard filter. |
| 0x40000106 | OPCODE_GETSETCARD | Operation of the function Card.GetSetCard, to be used in an AnnounceCard filter. |
| 0x40000107 | OPCODE_GETTYPE | Operation of the function Card.GetType, to be used in an AnnounceCard filter. |
| 0x40000108 | OPCODE_GETRACE | Operation of the function Card.GetRace, to be used in an AnnounceCard filter. |
| 0x40000109 | OPCODE_GETATTRIBUTE | Operation of the function Card.GetAttribute, to be used in an AnnounceCard filter. |


### Hint messages
| Value | Name | Description |
| --- | --- | --- |
| 500 | HINTMSG_RELEASE | Shows the following hint message: "Select the card(s) to tribute" |
| 501 | HINTMSG_DISCARD | Shows the following hint message: "Select the card(s) to discard" |
| 502 | HINTMSG_DESTROY | Shows the following hint message: "Select the card(s) to destroy" |
| 503 | HINTMSG_REMOVE | Shows the following hint message: "Select the card(s) to banish" |
| 504 | HINTMSG_TOGRAVE | Shows the following hint message: "Select the card(s) to send to Graveyard" |
| 505 | HINTMSG_RTOHAND | Shows the following hint message: "Select the card(s) to return to hand" |
| 506 | HINTMSG_ATOHAND | Shows the following hint message: "Select the card(s) to add to your hand" |
| 507 | HINTMSG_TODECK | Shows the following hint message: "Select the card(s) to return to Deck" |
| 508 | HINTMSG_SUMMON | Shows the following hint message: "Select the card(s) to Normal Summon" |
| 509 | HINTMSG_SPSUMMON | Shows the following hint message: "Select the card(s) to Special Summon" |
| 510 | HINTMSG_SET | Shows the following hint message: "Select the card(s) to Set to the field" |
| 511 | HINTMSG_FMATERIAL | Shows the following hint message: "Select the card(s) to use as Fusion Material" |
| 512 | HINTMSG_SMATERIAL | Shows the following hint message: "Select the card(s) to use as Synchro Material" |
| 513 | HINTMSG_XMATERIAL | Shows the following hint message: "Select the card(s) to use as Xyz Material" |
| 514 | HINTMSG_FACEUP | Shows the following hint message: "Select a face-up card(s)" |
| 515 | HINTMSG_FACEDOWN | Shows the following hint message: "Select a face-down card(s)" |
| 516 | HINTMSG_ATTACK | Shows the following hint message: "Select a monster(s) in Attack Position" |
| 517 | HINTMSG_DEFENSE | Shows the following hint message: "Select a monster(s) in Defense Position" |
| 518 | HINTMSG_EQUIP | Shows the following hint message: "Select a card(s) to equip" |
| 519 | HINTMSG_REMOVEXYZ | Shows the following hint message: "Select the Xyz Material(s) to detach" |
| 520 | HINTMSG_CONTROL | Shows the following hint message: "Select the monster(s) to change control" |
| 521 | HINTMSG_DESREPLACE | Shows the following hint message: "Select the card(s) to replace" |
| 522 | HINTMSG_FACEUPATTACK | Shows the following hint message: "Select a face-up Attack Position monster(s)" |
| 523 | HINTMSG_FACEUPDEFENSE | Shows the following hint message: "Select a face-up Defense Position monster(s)" |
| 524 | HINTMSG_FACEDOWNATTACK | Shows the following hint message: "Select a face-down Attack Position monster(s)" |
| 525 | HINTMSG_FACEDOWNDEFENSE | Shows the following hint message: "Select a face-down Defense Position monster(s)" |
| 526 | HINTMSG_CONFIRM | Shows the following hint message: "Select the card(s) to reveal" |
| 527 | HINTMSG_TOFIELD | Shows the following hint message: "Select the card(s) to place on the field" |
| 528 | HINTMSG_POSCHANGE | Shows the following hint message: "Select a monster to change its battle position" |
| 529 | HINTMSG_SELF | Shows the following hint message: "Select your card" |
| 530 | HINTMSG_OPPO | Shows the following hint message: "Select an opponent's card" |
| 531 | HINTMSG_TRIBUTE | Shows the following hint message: "Select monsters for Tribute Summon" |
| 532 | HINTMSG_DEATTACHFROM | Shows the following hint message: "Select the monster(s) to detach Xyz Material(s) from" |
| 533 | HINTMSG_LMATERIAL | Shows the following hint message: "Select the card(s) to use as Link Material" |
| 549 | HINTMSG_ATTACKTARGET | Shows the following hint message: "Select an attack target" |
| 550 | HINTMSG_EFFECT | Shows the following hint message: "Select the effect you want to activate" |
| 551 | HINTMSG_TARGET | Shows the following hint message: "Select the target(s) of the effect" |
| 552 | HINTMSG_COIN | Shows the following hint message: "Select heads or tails" |
| 553 | HINTMSG_DICE | Shows the following hint message: "Select dice results" |
| 554 | HINTMSG_CARDTYPE | Shows the following hint message: "Declare 1 card type" |
| 555 | HINTMSG_OPTION | Shows the following hint message: "Select an option" |
| 556 | HINTMSG_RESOLVEEFFECT | Shows the following hint message: "Select effect to apply/resolve" |
| 560 | HINTMSG_SELECT | Shows the following hint message: "Select" |
| 561 | HINTMSG_POSITION | Shows the following hint message: "Select the battle position" |
| 562 | HINTMSG_ATTRIBUTE | Shows the following hint message: "Declare an Attribute" |
| 563 | HINTMSG_RACE | Shows the following hint message: "Declare a Type" |
| 564 | HINTMSG_CODE | Shows the following hint message: "Declare a card name" |
| 565 | HINTMSG_NUMBER | Shows the following hint message: "Declare a number" |
| 566 | HINTMSG_EFFACTIVATE | Shows the following hint message: "Select the effect to activate" |
| 567 | HINTMSG_LVRANK | Shows the following hint message: "Declare a Level/Rank" |
| 568 | HINTMSG_RESOLVECARD | Shows the following hint message: "Select a card to resolve" |
| 569 | HINTMSG_ZONE | Shows the following hint message: "Select the zone to place "card name"" |
| 570 | HINTMSG_DISABLEZONE | Shows the following hint message: "Select the zone(s) to become unusable" |
| 571 | HINTMSG_TOZONE | Shows the following hint message: "Select the zone to move the card to" |
| 572 | HINTMSG_COUNTER | Shows the following hint message: "Select the card(s) to place a counter on" |
| 575 | HINTMSG_NEGATE | Shows the following hint message: "Select the card(s) to negate its effects" |
| 576 | HINTMSG_ATKDEF  | Shows the following hint message: "Select the card(s) to change its ATK/DEF" |
| 577 | HINTMSG_APPLYTO | Shows the following hint message: "Select the card(s) to apply the effect to" |
| 578 | HINTMSG_ATTACH | Shows the following hint message: "Select the card(s) to attach as material" |

### Effect timings
| Value | Name | Description |
| --- | --- | --- |
| 0x1 | TIMING_DRAW_PHASE | During the Draw Phase |
| 0x2 | TIMING_STANDBY_PHASE | During the Standby Phase |
| 0x4 | TIMING_MAIN_END | When the Main Phase is about to end, while moving to the Battle/End phase |
| 0x8 | TIMING_BATTLE_START | When the Battle Phase has just started |
| 0x10 | TIMING_BATTLE_END | When the Battle Phase is about to end, while moving to the Main Phase 2/End Phase |
| 0x20 | TIMING_END_PHASE | During the End Phase of a turn |
| 0x40 | TIMING_SUMMON | When a monster is Summoned |
| 0x80 | TIMING_SPSUMMON | When a monster is Special Summoned |
| 0x100 | TIMING_FLIPSUMMON | When a monster is Flip Summoned |
| 0x200 | TIMING_MSET | When a monster is Set |
| 0x400 | TIMING_SSET | When a Spell/Trap is Set |
| 0x800 | TIMING_POS_CHANGE | When a position changes |
| 0x1000 | TIMING_ATTACK | When an attack is declared |
| 0x2000 | TIMING_DAMAGE_STEP | During the Damage Step |
| 0x4000 | TIMING_DAMAGE_CAL | When performing Damage Calculation |
| 0x8000 | TIMING_CHAIN_END | When a chain ends |
| 0x10000 | TIMING_DRAW | When someplayer draws (not only in the Draw Phase) |
| 0x20000 | TIMING_DAMAGE | When a player takes damage |
| 0x40000 | TIMING_RECOVER | When a player gains LP |
| 0x80000 | TIMING_DESTROY | When something is destroyed |
| 0x100000 | TIMING_REMOVE | This event is raised when a card is removed |
| 0x200000 | TIMING_TOHAND | When you add a hand (retrieve, recycle, etc.) |
| 0x400000 | TIMING_TODECK | This event is raised when a card is sent to the deck |
| 0x800000 | TIMING_TOGRAVE | This event is raised when a card is sent to the graveyard |
| 0x1000000 | TIMING_BATTLE_PHASE | During the Battle Phase |
| 0x2000000 | TIMING_EQUIP | This event is raised when a card is equipped to another |
| 0x4000000 | TIMING_BATTLE_STEP_END | When the steps in a battle have finished |
| 0x8000000 | TIMING_BATTLED |
| 0x1c0 | TIMINGS_CHECK_MONSTER | When a monster is placed on te field |
| 0x1e0 | TIMINGS_CHECK_MONSTER_E | When a monster is placed on the field and also during the End Phase |


### Global flgas
| Value | Name | Description |
| --- | --- | --- |
 0x1 | GLOBALFLAG_DECK_REVERSE_CHECK | This flags is required to use EFFECT_REVERSE_DECK |
| 0x2 | GLOBALFLAG_BRAINWASHING_CHECK | This flags is used with Removing Brainshwashing |
| 0x8 | GLOBALFLAG_DELAYED_QUICKEFFECT | N/A |
| 0x10 | GLOBALFLAG_DETACH_EVENT | This flag is required when using EVENT_DETACH_MATERIAL |
| 0x40 | GLOBALFLAG_SPSUMMON_COUNT | A flag related with a limit a player can attempt Special Summons. Used with El Shaddoll Winda |
| 0x80 | GLOBALFLAG_XMAT_COUNT_LIMIT | Allows EFFECT_TYPE_XMATERIAL to take SetCountLimit into account |
| 0x100 | GLOBALFLAG_SELF_TOGRAVE | Allows checking the Graveyard in the middle of a resolving chain. Flag required to use EFFECT_SELF_TOGRAVE |
| 0x200 | GLOBALFLAG_SPSUMMON_ONCE | Cards that can only be special Summoned once per turn. This flga is related to Card.SetSPSummonOnce () |


### SetCountLimit codes
| Value | Name | Description |
| --- | --- | --- |
| 0x1 | EFFECT_COUNT_CODE_OATH | A flag to be used with SetCountLimit. An effect that receives this can only be ACTIVATED a given number of times (activations that are negated do not count) |
| 0x2 | EFFECT_COUNT_CODE_DUEL | A flag to be used with SetCountLimit. The effect that receives this flag can only be used a given amount of times per duel. |
| 0x4 | EFFECT_COUNT_CODE_SINGLE | A flag to be used with SetCountLimit. Usually used with multiple effects of the same card, the value set is the maximum count among all those effects. Example: "Once per turn: You can activate 1 of these effects." |
| 0x8 | EFFECT_COUNT_CODE_CHAIN | A flag to be used with SetCountLimit. Can be used when the effect should only be activatable once per chain (per copy of the card) |


#### Duel mode flags
| Value | Name | Description |
| --- | --- | --- |
 0x1 | DUEL_TEST_MODE | A flag for duel modes. You can control the AI/Opponent |
| 0x2 | DUEL_ATTACK_FIRST_TURN | A flag for duel modes. You can attack on the first turn |
| 0x4 | DUEL_USE_TRAPS_IN_NEW_CHAIN | A flag for duel modes. Deprecated flag in Edopro's 8.0 core |
| 0x8 | DUEL_OBSOLETE_RULING | A flag for duel modes. Applies First turn draw and ignition priority |
| 0x10 | DUEL_PSEUDO_SHUFFLE | A flag for duel modes. The deck is not shuffled |
| 0x20 | DUEL_TRIGGER_WHEN_PRIVATE_KNOWLEDGE | - |
| 0x40 | DUEL_SIMPLE_AI | A flag for duel modes. The AI/Opponent will activate effects whenever prompted |
| 0x80 | DUEL_RELAY |
| 0x100 | DUEL_OBSOLETE_IGNITION |
| 0x200 | DUEL_1ST_TURN_DRAW |
| 0x400 | DUEL_1_FIELD | Use this constant name in the scripts (internally called DUEL_1_FACEUP_FIELD) |
| 0x800 | DUEL_PZONE |
| 0x1000 | DUEL_SEPARATE_PZONE |
| 0x2000 | DUEL_EMZONE |
| 0x4000 | DUEL_FSX_MMZONE |
| 0x8000 | DUEL_TRAP_MONSTERS_NOT_USE_ZONE |
| 0x10000 | DUEL_RETURN_TO_DECK_TRIGGERS |
| 0x20000 | DUEL_TRIGGER_ONLY_IN_LOCATION |
| 0x40000 | DUEL_SPSUMMON_ONCE_OLD_NEGATE |
| 0x80000 | DUEL_CANNOT_SUMMON_OATH_OLD |
| 0x100000 | DUEL_NO_STANDBY_PHASE |
| 0x200000 | DUEL_NO_MAIN_PHASE_2 |
| 0x400000 | DUEL_3_COLUMNS_FIELD |
| 0x800000 | DUEL_DRAW_UNTIL_5 |
| 0x1000000 | DUEL_NO_HAND_LIMIT |
| 0x2000000 | DUEL_UNLIMITED_SUMMONS |
| 0x4000000 | DUEL_INVERTED_QUICK_PRIORITY |
| 0x8000000 | DUEL_EQUIP_NOT_SENT_IF_MISSING_TARGET |
| 0x10000000 | DUEL_0_ATK_DESTROYED |
| 0x20000000 | DUEL_STORE_ATTACK_REPLAYS |
| 0x40000000 | DUEL_SINGLE_CHAIN_IN_DAMAGE_SUBSTEP |
| 0x80000000 | DUEL_CAN_REPOS_IF_NON_SUMPLAYER |
| 0x100000000 | DUEL_TCG_SEGOC_NONPUBLIC |
| 0x200000000 | DUEL_TCG_SEGOC_FIRSTTRIGGER |
| 0 | DUEL_MODE_SPEED | A composite flag for duel modes. (DUEL_3_COLUMNS_FIELD+DUEL_NO_MAIN_PHASE_2+DUEL_TRIGGER_ONLY_IN_LOCATION) |
| 0 | DUEL_MODE_RUSH | A composite flag for duel modes. (DUEL_3_COLUMNS_FIELD+DUEL_NO_MAIN_PHASE_2+DUEL_NO_STANDBY_PHASE+DUEL_1ST_TURN_DRAW+DUEL_INVERTED_QUICK_PRIORITY+DUEL_DRAW_UNTIL_5+DUEL_NO_HAND_LIMIT+DUEL_UNLIMITED_SUMMONS+DUEL_TRIGGER_ONLY_IN_LOCATION) |
| 0 | DUEL_MODE_GOAT | A composite flag for duel modes.  (DUEL_MODE_MR1 | DUEL_USE_TRAPS_IN_NEW_CHAIN | DUEL_6_STEP_BATLLE_STEP | DUEL_TRIGGER_WHEN_PRIVATE_KNOWLEDGE | DUEL_EQUIP_NOT_SENT_IF_MISSING_TARGET | DUEL_0_ATK_DESTROYED | DUEL_STORE_ATTACK_REPLAYS | DUEL_SINGLE_CHAIN_IN_DAMAGE_SUBSTEP | DUEL_CAN_REPOS_IF_NON_SUMPLAYER | DUEL_TCG_SEGOC_NONPUBLIC | DUEL_TCG_SEGOC_FIRSTTRIGGER) |
| 1 | DUEL_MODE_MR1 | A composite flag for duel modes. (DUEL_OBSOLETE_IGNITION+DUEL_1ST_TURN_DRAW+DUEL_1_FIELD+DUEL_SPSUMMON_ONCE_OLD_NEGATE+DUEL_RETURN_TO_DECK_TRIGGERS+DUEL_CANNOT_SUMMON_OATH_OLD) |
| 2 | DUEL_MODE_MR2 | A composite flag for duel modes. (DUEL_1ST_TURN_DRAW+DUEL_1_FIELD+DUEL_SPSUMMON_ONCE_OLD_NEGATE+DUEL_RETURN_TO_DECK_TRIGGERS+DUEL_CANNOT_SUMMON_OATH_OLD) |
| 3 | DUEL_MODE_MR3 | A composite flag for duel modes. (DUEL_PZONE+DUEL_SEPARATE_PZONE+DUEL_SPSUMMON_ONCE_OLD_NEGATE+DUEL_RETURN_TO_DECK_TRIGGERS+DUEL_CANNOT_SUMMON_OATH_OLD) |
| 4 | DUEL_MODE_MR4 | A composite flag for duel modes. (DUEL_PZONE+DUEL_EMZONE+DUEL_SPSUMMON_ONCE_OLD_NEGATE+DUEL_RETURN_TO_DECK_TRIGGERS+DUEL_CANNOT_SUMMON_OATH_OLD) |
| 5 | DUEL_MODE_MR5 | A composite flag for duel modes. (DUEL_PZONE+DUEL_EMZONE+DUEL_FSX_MMZONE+DUEL_TRAP_MONSTERS_NOT_USE_ZONE+DUEL_TRIGGER_ONLY_IN_LOCATION) |



#### Activities
| Value | Name | Description |
| --- | --- | --- |
| 1 | ACTIVITY_SUMMON | Refers to the action of attempting to perform Summons of any kind |
| 2 | ACTIVITY_NORMALSUMMON | Refers to the action of performing a Normal Summon |
| 3 | ACTIVITY_SPSUMMON | Refers to the action of performing Special Summons |
| 4 | ACTIVITY_FLIPSUMMON | Refers to the action of performing Flip Summons |
| 5 | ACTIVITY_ATTACK | Refers to the action of declarion attacks |
| 6 | ACTIVITY_BATTLE_PHASE | Refers to the act of conducting a battle phase. This activity is not available with custom counter |
| 7 | ACTIVITY_CHAIN | An activity only available with custom counter |


#### Win reasons
| Value | Name | Description |
| --- | --- | --- |
| 0x10 | WIN_REASON_EXODIA | The hexadecimal value for a duel win caused by "Exodia, the Forbidden One" |
| 0x11 | WIN_REASON_FINAL_COUNTDOWN | The hexadecimal value for a duel win caused by "Countdown" |
| 0x12 | WIN_REASON_VENNOMINAGA | The hexadecimal value for a duel win caused by "Vennominage, Deity of the Poisonous Snakes" |
| 0x13 | WIN_REASON_CREATORGOD | The hexadecimal value for a duel win caused by "Holactie the Creator of Light" |
| 0x14 | WIN_REASON_EXODIUS | The hexadecimal value for a duel win caused by "Exodius the Ultimate Forbidden Lord" |
| 0x15 | WIN_REASON_DESTINY_BOARD | The hexadecimal value for a duel win caused by "Destiny Board" |
| 0x16 | WIN_REASON_LAST_TURN | The hexadecimal value for a duel win caused by "Last Turn" |
| 0x17 | WIN_REASON_PUPPET_LEO | The hexadecimal value for a duel win caused by "Number 88: Gimmick Puppet of Leo" |
| 0x18 | WIN_REASON_DISASTER_LEO | The hexadecimal value for a duel win caused by "Number C88: Gimmick Puppet Disaster Leo" |
| 0x19 | WIN_REASON_JACKPOT7 | The hexadecimal value for a duel win caused by "Jackpot 7" |
| 0x1a | WIN_REASON_RELAY_SOUL | The hexadecimal value for a duel win caused by "Relay Soul" |
| 0x1b | WIN_REASON_GHOSTRICK_MISCHIEF | The hexadecimal value for a duel win caused by "Ghostrick Angel of Mischief" |
| 0x1c | WIN_REASON_PHANTASM_SPIRAL | The hexadecimal value for a duel win caused by "Phantasm Spiral Assault" |
| 0x1d | WIN_REASON_FA_WINNERS | The hexadecimal value for a duel win caused by "F.A. Winners" |
| 0x1e | WIN_REASON_FLYING_ELEPHANT | The hexadecimal value for a duel win caused by "Flying Elephant" |
| 0x1f | WIN_REASON_EXODIA_DEFENDER | The hexadecimal value for a duel win caused by "Exodia, the Legendary Defender" |
| 0x20 | WIN_REASON_MATCH_WINNER | Not used by cards. |
| 0x21 | WIN_REASON_TRUE_EXODIA | The hexadecimal value for a duel win caused by "True Exodia" |
| 0x22 | WIN_REASON_FINAL_DRAW | The hexadecimal value for a duel win caused by "Final Draw" |
| 0x30 | WIN_REASON_CREATOR_MIRACLE | The hexadecimal value for a duel win caused by "Creator of Miracles" |
| 0x51 | WIN_REASON_EVIL_1 | Not used by cards. |
| 0x52 | WIN_REASON_NUMBER_Ci1000 | The hexadecimal value for a duel win caused by "Number iC1000: Numeronius Numeronia" |
| 0x53 | WIN_REASON_ZERO_GATE | The hexadecimal value for a duel win caused by "Zero Gate of the Void" |
| 0x54 | WIN_REASON_DEUCE | The hexadecimal value for a duel win caused by "Number iC1000: Numeronius Numeronia" |
| 0x56 | WIN_REASON_DECK_MASTER | The hexadecimal value for a duel win caused by the rules of Deck Masters |
| 0x57 | WIN_REASON_DRAW_OF_FATE | The hexadecimal value for a duel win caused by "Draw of Fate" |
| 0x58 | WIN_REASON_MUSICAL_SUMO | The hexadecimal value for a duel win caused by "Musical Sumo Dice Games" |


#### Other constants
| Value | Name | Description |
| --- | --- | --- |
 0x7 | ANNOUNCE_CARD | Declaration card |
| 0x8 | ANNOUNCE_CARD_FILTER | Declaration card with filters |
| 1 | REGISTER_FLAG_DETACH_XMAT | Effect that activates with cost of detaching own Xyz material, for Tachyon Unit (Card.RegisterEffect) |
| 2 | REGISTER_FLAG_CARDIAN | Cardian's effects to Special Summon a Cardian, for anime Cardians (Card.RegisterEffect) |
| 4 | REGISTER_FLAG_THUNDRA | Thunders Dragon monster's effects that activates by discarding themselves, for Thunder Dragon Thunderstormech (Card.RegisterEffect) |
| 8 | REGISTER_FLAG_ALLURE_LVUP | Allure Queen's effect to Special Summon the next level, for Allure Palace (Card.RegisterEffect) |
| 16 | REGISTER_FLAG_TELLAR | An effect registered with this flag will be available to be applied by Tellarknight Constellar Caduceus |
| 0x100 | FUSPROC_NOTFUSION | Flag used for the various filters in the fusion procedure. |
| 0x200 | FUSPROC_CONTACTFUS | Flag used for the various filters in the fusion procedure. |
| 0x400 | FUSPROC_LISTEDMATS | Flag used for the various filters in the fusion procedure. |
| 0x800 | FUSPROC_NOLIMIT |
| 0x1000 | FUSPROC_CANCELABLE | Flag used in the fusion procedure. Allows the selection of fusion materials to be canceled |
| 0x1 | RITPROC_EQUAL | Flag used for the type of Ritual Summon procedure |
| 0x2 | RITPROC_GREATER | Flag used for the type of Ritual Summon procedure |
| 0x1<<32 | MATERIAL_FUSION | Value= 0x1<<32 |
| 0x2<<32 | MATERIAL_SYNCHRO | Value= 0x2<<32 |
| 0x4<<32 | MATERIAL_XYZ | Value= 0x4<<32 |
| 0x8<<32 | MATERIAL_LINK | Value= 0x8<<32 |
| 0 | EFFECT_CLIENT_MODE_NORMAL |
| 1 | EFFECT_CLIENT_MODE_RESOLVE |
| 2 | EFFECT_CLIENT_MODE_RESET |
| 0x80000000 | DOUBLE_DAMAGE | Double piercing damage, used as the value of EFFECT_PIERCE |
| 0x80000001 | HALF_DAMAGE | Half piercing damage, used as the value of EFFECT_PIERCE |
| 60 | SELECT_HEADS | Display "Heads". Used as description when an effect required the player to select heads/tails |
| 61 | SELECT_TAILS | Display "Tails". Used as description when an effect required the player to select heads/tails |
