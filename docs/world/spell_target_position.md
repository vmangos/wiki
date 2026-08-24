# spell_target_position Table

Defines target position for spells that teleport or summon to a fixed location.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`target_map`](#f-target_map) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`target_position_x`](#f-target_position_x) | float |  | NO | 0 |  |
| [`target_position_y`](#f-target_position_y) | float |  | NO | 0 |  |
| [`target_position_z`](#f-target_position_z) | float |  | NO | 0 |  |
| [`target_orientation`](#f-target_orientation) | float |  | NO | 0 |  |
| [`build_min`](#f-build_min) | smallint(4) unsigned |  | NO | 0 |  |
| [`build_max`](#f-build_max) | smallint(4) unsigned |  | NO | 5875 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-target_map"></a>**`target_map`** - Primary Key. Destination map.
- <a id="f-target_position_x"></a><a id="f-target_position_y"></a><a id="f-target_position_z"></a>**`target_position_x/y/z`** - Destination coordinates.
- <a id="f-target_orientation"></a>**`target_orientation`** - Facing direction.
- <a id="f-build_max"></a><a id="f-build_min"></a>**`build_min` / `build_max`** - Client build range.
