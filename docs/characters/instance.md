# instance Table

Dungeon/raid save instances with reset times.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(11) unsigned | PRI | NO | 0 |  |
| [`map`](#f-map) | int(11) unsigned | MUL | NO | 0 |  |
| [`reset_time`](#f-reset_time) | bigint(40) | MUL | NO | 0 |  |
| [`data`](#f-data) | longtext |  | YES |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Instance save id (referenced by character/group binds).
- <a id="f-map"></a>**`map`** - Map id of the dungeon/raid.
- <a id="f-reset_time"></a>**`reset_time`** - Scheduled reset timestamp (from [`instance_reset`](instance_reset.md) schedule).
- <a id="f-data"></a>**`data`** - Encounter progress blob written by the instance script (`SET_INST_DATA`).
