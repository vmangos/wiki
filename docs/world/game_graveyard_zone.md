# game_graveyard_zone Table

Maps graveyards to zones and factions.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`ghost_zone`](#f-ghost_zone) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`faction`](#f-faction) | smallint(5) unsigned |  | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(2) unsigned |  | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(2) unsigned | PRI | NO | 10 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Graveyard ID.
- <a id="f-ghost_zone"></a>**`ghost_zone`** - Primary Key. Zone ID where ghost appears. (see `AreaTable.dbc`)
- <a id="f-faction"></a>**`faction`** - Team filter: `0` any, `469` Alliance, `67` Horde (root team ids, not a [`faction`](faction.md) reference).
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
