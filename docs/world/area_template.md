# area_template Table

Contains information about all areas and zones of the world, including flags, recommended level, faction ownership, and liquid type.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`map_id`](#f-map_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`zone_id`](#f-zone_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`explore_flag`](#f-explore_flag) | mediumint(8) unsigned |  | NO | 0 |  |
| [`flags`](#f-flags) | mediumint(8) unsigned |  | NO | 0 |  |
| [`area_level`](#f-area_level) | mediumint(8) |  | NO | 0 |  |
| [`name`](#f-name) | varchar(100) |  | NO | '' |  |
| [`team`](#f-team) | tinyint(3) unsigned |  | NO | 0 |  |
| [`liquid_type`](#f-liquid_type) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Unique area ID. (see `AreaTable.dbc`)
- <a id="f-map_id"></a>**`map_id`** - Map ID (from [`map_template`](map_template.md).entry).
- <a id="f-zone_id"></a>**`zone_id`** - Parent zone ID (references `entry` in same table). Defines the zone to which this sub-area belongs. (see [`area_template`](area_template.md).entry (self-reference))
- <a id="f-explore_flag"></a>**`explore_flag`** - Exploration-related flags (internal).
- <a id="f-flags"></a>**`flags`** - Bitmask of area properties:
  - `0x01` - Snow (Dun Morogh, Naxxramas, etc.)
  - `0x02` - Unknown
  - `0x04` - Development map only
  - `0x08` - Slave capital
  - `0x10` - Unknown
  - `0x20` - Slave capital (2)
  - `0x40` - Duel allowed
  - `0x80` - Arena
  - `0x100` - Main capital city
  - `0x200` - City (one specific zone)
- <a id="f-area_level"></a>**`area_level`** - Recommended level for the area.
- <a id="f-name"></a>**`name`** - Area name.
- <a id="f-team"></a>**`team`** - Faction ownership:
  - `2` - Alliance
  - `4` - Horde
- <a id="f-liquid_type"></a>**`liquid_type`** - Liquid type (from `LiquidType.dbc`):
  - `1` - Water
  - `2` - Ocean
  - `3` - Magma
  - `4` - Slime
  - `5` - Naxxramas slime
