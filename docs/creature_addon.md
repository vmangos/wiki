# The creature_addon table

Allows you to override some creature data per spawn.

## Structure

### 1. guid - int(10) unsigned, primary key

The guid of the spawn from the `creature` table.

### 2. patch - tinyint(3) unsigned, primary key

Minimum content patch to load this row. Patch values go from 0 for 1.2 to 10 for 1.12.

### 3. display_id - smallint(5) unsigned

Creature display id from CreatureDisplayInfo.dbc in client. It defines what model will be used by the creature. This value overrides the display id from the `creature_template` if its set.

### 4. mount_display_id - mediumint(8) unsigned

Creature display id from CreatureDisplayInfo.dbc in client. It defines what mount will be used by the creature. This value overrides the mount display id from the `creature_template` if its set. Value -1 is used as default to mean "don't override", since 0 means no mount.

### 5. equipment_id - mediumint(8) unsigned

Creature equipment id from the `creature_equip_template` table. It defines what weapons the creature will be holding. It is purely visual, and the stats of the weapons do not affect the creature. This value overrides the equipment id from the `creature_template` if its set. Value -1 is used as default to mean "don't override", since 0 means no equipment.

### 6. stand_state - tinyint(3) unsigned

Defines if the creature is standing, sitting on laying down out of combat.

```
UNIT_STAND_STATE_STAND             = 0,
UNIT_STAND_STATE_SIT               = 1,
UNIT_STAND_STATE_SIT_CHAIR         = 2,
UNIT_STAND_STATE_SLEEP             = 3,
UNIT_STAND_STATE_SIT_LOW_CHAIR     = 4,
UNIT_STAND_STATE_SIT_MEDIUM_CHAIR  = 5,
UNIT_STAND_STATE_SIT_HIGH_CHAIR    = 6,
UNIT_STAND_STATE_DEAD              = 7,
UNIT_STAND_STATE_KNEEL             = 8
```

### 7. sheath_state - tinyint(3) unsigned

Defines if the creature is holding its weapon out of combat, or is it hidden away. Value 1 is used as default, since the vast majority of creatures hold their melee weapons in their hands even when out of combat.

```
SHEATH_STATE_UNARMED  = 0,
SHEATH_STATE_MELEE    = 1,
SHEATH_STATE_RANGED   = 2
```

### 8. emote_state - smallint(5) unsigned

Defines what emote state will be used as the idle animation when out of combat. A blizzlike example of this functionality would be the workers in Elwynn Forest that chop wood.

```
EMOTE_STATE_DANCE                  = 10,
EMOTE_STATE_SLEEP                  = 12,
EMOTE_STATE_SIT                    = 13,
EMOTE_STATE_STAND                  = 26,
EMOTE_STATE_READYUNARMED           = 27,
EMOTE_STATE_WORK_SHEATHED          = 28,
EMOTE_STATE_POINT                  = 29,
EMOTE_STATE_NONE                   = 30,
EMOTE_STATE_STUN                   = 64,
EMOTE_STATE_DEAD                   = 65,
EMOTE_STATE_KNEEL                  = 68,
EMOTE_STATE_USESTANDING            = 69,
EMOTE_STATE_STUN_NOSHEATHE         = 93,
EMOTE_STATE_USESTANDING_NOSHEATHE  = 133,
EMOTE_STATE_WORK                   = 173,
EMOTE_STATE_SPELLPRECAST           = 193,
EMOTE_STATE_READYRIFLE             = 214,
EMOTE_STATE_WORK_MINING            = 233,
EMOTE_STATE_WORK_CHOPWOOD          = 234,
EMOTE_STATE_APPLAUD                = 253,
EMOTE_STATE_AT_EASE                = 313,
EMOTE_STATE_READY1H                = 333,
EMOTE_STATE_SPELLKNEELSTART        = 353,
EMOTE_STATE_SUBMERGED              = 373,
EMOTE_STATE_READY2H                = 375,
EMOTE_STATE_READYBOW               = 376,
EMOTE_STATE_TALK                   = 378,
EMOTE_STATE_FISHING                = 379,
EMOTE_STATE_WHIRLWIND              = 382,
EMOTE_STATE_DROWNED                = 383,
EMOTE_STATE_HOLD_BOW               = 384,
EMOTE_STATE_HOLD_RIFLE             = 385,
EMOTE_STATE_HOLD_THROWN            = 386,
EMOTE_STATE_ROAR                   = 391,
EMOTE_STATE_LAUGH                  = 392,
EMOTE_STATE_CANNIBALIZE            = 398,
EMOTE_STATE_DANCESPECIAL           = 400,
EMOTE_STATE_EXCLAIM                = 412,
EMOTE_STATE_SIT_CHAIR_MED          = 415,
EMOTE_STATE_SPELLEFFECT_HOLD       = 422,
EMOTE_STATE_EAT_NO_SHEATHE         = 423,
```

### 9. auras - text

A list of spell ids from the `spell_template` table separated by spaces. These are permanent auras that should always be present on the creature. Do not assign temporary casted buffs like Frost Armor here, only permanent auras.
