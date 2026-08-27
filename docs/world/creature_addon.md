# creature_addon Table

Provides per-spawn overrides for creature visual state, equipment, mount, emotes, and auras.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO | 0 |  |
| [`patch`](#f-patch) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`display_id`](#f-display_id) | smallint(5) unsigned |  | NO | 0 |  |
| [`mount_display_id`](#f-mount_display_id) | smallint(6) |  | NO | -1 |  |
| [`equipment_id`](#f-equipment_id) | int(11) |  | NO | -1 |  |
| [`stand_state`](#f-stand_state) | tinyint(3) unsigned |  | NO | 0 |  |
| [`sheath_state`](#f-sheath_state) | tinyint(3) unsigned |  | NO | 1 |  |
| [`emote_state`](#f-emote_state) | smallint(5) unsigned |  | NO | 0 |  |
| [`auras`](#f-auras) | text |  | YES |  |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. References [`creature`](creature.md).guid.
- <a id="f-patch"></a>**`patch`** - Primary Key. Patch version - loads the highest ≤ current.
- <a id="f-display_id"></a>**`display_id`** - Override display model (from `CreatureDisplayInfo.dbc`). `0` means no override.
- <a id="f-mount_display_id"></a>**`mount_display_id`** - Override mount display. `-1` means no override (0 = no mount).; references `CreatureDisplayInfo.dbc`
- <a id="f-equipment_id"></a>**`equipment_id`** - Override equipment set. `-1` means no override (0 = no equipment). (see [`creature_equip_template`](creature_equip_template.md).entry)
- <a id="f-stand_state"></a>**`stand_state`** - Stand/sit/lie state:
  - `0` - Stand
  - `1` - Sit
  - `2` - Sit on chair
  - `3` - Sleep
  - `4` - Sit low chair
  - `5` - Sit medium chair
  - `6` - Sit high chair
  - `7` - Dead
  - `8` - Kneel
  - `9` - Custom state (used by scripts)
- <a id="f-sheath_state"></a>**`sheath_state`** - Weapon sheath:
  - `0` - Unarmed
  - `1` - Melee (default)
  - `2` - Ranged
- <a id="f-emote_state"></a>**`emote_state`** - Idle emote state (from `Emotes.dbc`). Common values:
  - `10` - Dance
  - `12` - Sleep
  - `13` - Sit
  - `26` - Stand
  - `233` - Work (mining)
  - `234` - Work (chop wood)
  - `375` - Ready 2H
  - `379` - Fishing
- <a id="f-auras"></a>**`auras`** - Space-separated list of spell IDs (from [`spell_template`](spell_template.md).entry) for permanent auras. Do not use temporary buffs here.
