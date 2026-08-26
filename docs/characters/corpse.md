# corpse Table

Corpses left in the world after deaths (position, bones/state).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`player_guid`](#f-player_guid) | int(11) unsigned | MUL | NO | 0 |  |
| [`position_x`](#f-position_x) | float |  | NO | 0 |  |
| [`position_y`](#f-position_y) | float |  | NO | 0 |  |
| [`position_z`](#f-position_z) | float |  | NO | 0 |  |
| [`orientation`](#f-orientation) | float |  | NO | 0 |  |
| [`map`](#f-map) | int(11) unsigned |  | NO | 0 |  |
| [`time`](#f-time) | bigint(20) unsigned | MUL | NO | 0 |  |
| [`corpse_type`](#f-corpse_type) | tinyint(3) unsigned | MUL | NO | 0 |  |
| [`instance`](#f-instance) | int(11) unsigned | MUL | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Global Unique Identifier
- <a id="f-player_guid"></a>**`player_guid`** - Dead character ([`characters`](characters.md).guid).
- <a id="f-position_x"></a>**`position_x`** - Where the corpse lies.
- <a id="f-position_y"></a>**`position_y`** - Corpse Y coordinate.
- <a id="f-position_z"></a>**`position_z`** - Corpse Z coordinate.
- <a id="f-orientation"></a>**`orientation`** - Where the corpse lies.
- <a id="f-map"></a>**`map`** - Where the corpse lies.
- <a id="f-time"></a>**`time`** - Death time.
- <a id="f-corpse_type"></a>**`corpse_type`** - 0 = bones, 1 = resurrectable PvE corpse, 2 = resurrectable PvP corpse.
  Only values 1-2 are ever written; bones exist only as transient world objects (never persisted).
- <a id="f-instance"></a>**`instance`** - Instance id ([`instance`](instance.md).id) when death happened inside an instance.

---

### corpse_type Values

| Value | Meaning |
| :---: | :--- |
| 0 | Bones - enum value exists but bones are never saved to the DB |
| 1 | Resurrectable PvE corpse |
| 2 | Resurrectable PvP corpse |

> Resurrectable corpses expire after 3 days (`time` + 3 days).
