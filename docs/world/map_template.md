# map_template Table

Defines map properties - parent map, type, player limit, reset delay, and script binding.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO |  |  |
| [`patch`](#f-patch) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`parent`](#f-parent) | int(10) unsigned |  | NO | 0 |  |
| [`map_type`](#f-map_type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`linked_zone`](#f-linked_zone) | int(10) unsigned |  | NO | 0 |  |
| [`player_limit`](#f-player_limit) | tinyint(3) unsigned |  | NO | 0 |  |
| [`reset_delay`](#f-reset_delay) | int(10) unsigned |  | NO | 0 |  |
| [`ghost_entrance_map`](#f-ghost_entrance_map) | smallint(5) |  | NO | -1 |  |
| [`ghost_entrance_x`](#f-ghost_entrance_x) | float |  | NO | 0 |  |
| [`ghost_entrance_y`](#f-ghost_entrance_y) | float |  | NO | 0 |  |
| [`map_name`](#f-map_name) | varchar(128) |  | NO | '' |  |
| [`script_name`](#f-script_name) | varchar(128) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Map ID.
- <a id="f-patch"></a>**`patch`** - Primary Key. Client patch.
- <a id="f-parent"></a>**`parent`** - Parent map ID.
- <a id="f-map_type"></a>**`map_type`** - `0` normal, `1` instance, `2` raid, `3` battleground.
- <a id="f-linked_zone"></a>**`linked_zone`** - Zone ID associated with this map.
- <a id="f-player_limit"></a>**`player_limit`** - Max players.
- <a id="f-reset_delay"></a>**`reset_delay`** - Instance reset delay in **days** (multiplied by the `Rate.InstanceResetTime` config; minimum forced to 1).
- <a id="f-ghost_entrance_map"></a>**`ghost_entrance_map`** - Map where ghost appears.
- <a id="f-ghost_entrance_x"></a><a id="f-ghost_entrance_y"></a>**`ghost_entrance_x/y`** - Ghost entrance coords.
- <a id="f-map_name"></a>**`map_name`** - Map name.
- <a id="f-script_name"></a>**`script_name`** - C++ script binding.
