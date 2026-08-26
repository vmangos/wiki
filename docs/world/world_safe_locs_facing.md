# world_safe_locs_facing Table

Defines orientation for world safe locations (graveyards, respawn points).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(10) unsigned | PRI | NO |  |  |
| [`orientation`](#f-orientation) | float |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Safe-location id from `WorldSafeLocs.dbc` (same id space as the graveyard ids in [`game_graveyard_zone`](game_graveyard_zone.md)).
- <a id="f-orientation"></a>**`orientation`** - Facing direction (radians).
