# character_battleground_data Table

Per-character battleground state that must survive a restart (marked for BG, random BG info).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`instance_id`](#f-instance_id) | int(11) unsigned |  | NO | 0 |  |
| [`team`](#f-team) | int(11) unsigned |  | NO | 0 |  |
| [`join_x`](#f-join_x) | float |  | NO | 0 |  |
| [`join_y`](#f-join_y) | float |  | NO | 0 |  |
| [`join_z`](#f-join_z) | float |  | NO | 0 |  |
| [`join_o`](#f-join_o) | float |  | NO | 0 |  |
| [`join_map`](#f-join_map) | int(11) |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-instance_id"></a>**`instance_id`** - Battleground instance the player is queued/deserter-bound to.
- <a id="f-team"></a>**`team`** - Team id the player joined as (Alliance/Horde).
- <a id="f-join_x"></a>**`join_x`** - Position saved on join so the player returns here after the BG.
- <a id="f-join_y"></a>**`join_y`** - Join position Y coordinate.
- <a id="f-join_z"></a>**`join_z`** - Join position Z coordinate.
- <a id="f-join_o"></a>**`join_o`** - Join orientation.
- <a id="f-join_map"></a>**`join_map`** - Map id of the join position (from [`map_template`](../world/map_template.md).entry).
