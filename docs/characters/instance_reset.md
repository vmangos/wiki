# instance_reset Table

Global reset schedule per map (one row per resettable map).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`map`](#f-map) | int(11) unsigned | PRI | NO | 0 |  |
| [`reset_time`](#f-reset_time) | bigint(40) |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-map"></a>**`map`** - Primary Key. Dungeon/raid map id.
- <a id="f-reset_time"></a>**`reset_time`** - Next scheduled global reset for this map.
