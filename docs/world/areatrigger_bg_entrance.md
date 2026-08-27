# areatrigger_bg_entrance Table

Defines battleground entrance portals that players can use to join the queue.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`name`](#f-name) | text |  | YES |  |  |
| [`team`](#f-team) | mediumint(8) unsigned |  | NO | 0 |  |
| [`bg_template`](#f-bg_template) | mediumint(8) unsigned |  | NO | 0 |  |
| [`exit_map`](#f-exit_map) | smallint(5) unsigned |  | NO | 0 |  |
| [`exit_position_x`](#f-exit_position_x) | float |  | NO | 0 |  |
| [`exit_position_y`](#f-exit_position_y) | float |  | NO | 0 |  |
| [`exit_position_z`](#f-exit_position_z) | float |  | NO | 0 |  |
| [`exit_orientation`](#f-exit_orientation) | float |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Areatrigger ID from [`areatrigger_template`](areatrigger_template.md).entry.
- <a id="f-name"></a>**`name`** - Name of the battleground. Not used by the core - purely descriptive.
- <a id="f-team"></a>**`team`** - Faction allowed to use this entrance:
  - `469` - Alliance
  - `67` - Horde
- <a id="f-bg_template"></a>**`bg_template`** - Battleground ID from [`battleground_template`](battleground_template.md).id:
- <a id="f-exit_map"></a>**`exit_map`** - Map ID (from [`map_template`](map_template.md).entry) where players are teleported upon leaving the battleground.
- <a id="f-exit_position_x"></a>**`exit_position_x`** - Where players appear when exiting the battleground through this entrance.
- <a id="f-exit_position_y"></a>**`exit_position_y`** - Exit teleport Y coordinate.
- <a id="f-exit_position_z"></a>**`exit_position_z`** - Exit teleport Z coordinate.
- <a id="f-exit_orientation"></a>**`exit_orientation`** - Facing direction on exit.
