# player_xp_for_level Table

Defines experience points required to reach each level.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`lvl`](#f-lvl) | int(3) unsigned | PRI | NO |  |  |
| [`xp_for_next_level`](#f-xp_for_next_level) | int(10) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-lvl"></a>**`lvl`** - Primary Key. Current level.
- <a id="f-xp_for_next_level"></a>**`xp_for_next_level`** - XP required to reach the next level.
