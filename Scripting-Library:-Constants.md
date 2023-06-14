- For a list of the constants used to represent archetypes in scripts see [archetype_setcode_constants](https://github.com/ProjectIgnis/CardScripts/blob/master/archetype_setcode_constants.lua) file

- For a list of the commonly used card names that have a constant as well as constant for some counters and tokens, see the [card_counter_constants](https://github.com/ProjectIgnis/CardScripts/blob/master/card_counter_constants.lua) file

- This is the [main constant](https://github.com/ProjectIgnis/CardScripts/blob/master/constant.lua) file


### Locations, positions, sequences, card types, attributes and monster type
| Value | Name | Description |
| --- | --- | --- |
| val | name | desc |
| 0x1 | LOCATION_DECK | The Deck. If it is used as Location Redirect, the card is placed on the top. (decimal value= 1) |
| 0x2 | LOCATION_HAND | The hand  (decimal value= 2) |
| 0x4 | LOCATION_MZONE | The Monster Zone  (decimal value= 4) |
| 0x8 | LOCATION_SZONE | The Spell/Trap Zones. It includes the Field Spell Zone and the Pendulum Zones (<=MR3). (decimal value= 8) |
| 0x10 | LOCATION_GRAVE | The graveyard/GY (decimal value= 16) |
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
| 0x400 | LOCATION_STZONE | The Spell/Trap Zone (without the Field Zone). Symbolic location. Can be used in functions expecting a location and also in SetRange (except with trigger effects) |
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
| 0x1 | TYPE_MONSTER | A Monster card  (decimal value= 1) |
| 0x2 | TYPE_SPELL | A Spell card  (decimal value= 2) |
| 0x4 | TYPE_TRAP | A Trap card (decimal value= 4) |
| 0x10 | TYPE_NORMAL | A Normal monster (decimal value= 16) |
| 0x20 | TYPE_EFFECT | A card with effect (decimal value= 32) |
| 0x40 | TYPE_FUSION | A Fusion (monster) (decimal value= 64) |
| 0x80 | TYPE_RITUAL | A Ritual card (decimal value= 128) |
| 0x100 | TYPE_TRAPMONSTER | A Trap monster, e.g. Embodiment of Apophis. NOTE: This is not used in adding to the default card types.  (decimal value= 256) |
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
| 0x2000000 | TYPE_SPSUMMON | An Special Summon-only monster. Used for Nomi/Semi-Nomi Main Deck monsters (decimal value= 33554432) |
| 0x4000000 | TYPE_LINK | A Link (decimal value= 67108864) |
| 0x8000000 | TYPE_SKILL | A Skill Card. (decimal value= 134217728) |
| 0x10000000 | TYPE_ACTION | An Action card. (decimal value= 268435456) |
| 0x4011 | TYPES_TOKEN | Constant used to simplify cards that summon tokens. Sum of the following values: Monster + Normal + Token (decimal value= 16401) |
| 0x4802040 | TYPE_EXTRA | Extra Deck cards: TYPE_FUSION+TYPE_SYNCHRO+TYPE_XYZ+TYPE_LINK. The sum of (0x40+0x2000+0x4000000+0x800000) (decimal value= 75505728) |
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


### effect types and effect flags
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


