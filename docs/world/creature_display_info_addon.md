# creature_display_info_addon Table

Addon data for creature display info - bounding radius, combat reach, movement speeds, and gender.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`display_id`](#f-display_id) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`build`](#f-build) | smallint(4) unsigned | PRI | NO | 0 |  |
| [`bounding_radius`](#f-bounding_radius) | float |  | NO | 0 |  |
| [`combat_reach`](#f-combat_reach) | float |  | NO | 0 |  |
| [`speed_walk`](#f-speed_walk) | float |  | NO | 1 |  |
| [`speed_run`](#f-speed_run) | float |  | NO | 1.14286 |  |
| [`gender`](#f-gender) | tinyint(3) unsigned |  | NO | 2 |  |
| [`display_id_other_gender`](#f-display_id_other_gender) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-display_id"></a>**`display_id`** (mediumint(8) unsigned) - Primary Key. From `CreatureDisplayInfo.dbc`.
- <a id="f-build"></a>**`build`** (smallint(4) unsigned) - Primary Key. Client build version.
- <a id="f-bounding_radius"></a>**`bounding_radius`** - Collision radius.
- <a id="f-combat_reach"></a>**`combat_reach`** - Melee attack reach.
- <a id="f-speed_walk"></a>**`speed_walk`** - Base walk speed (yards/sec).
- <a id="f-speed_run"></a>**`speed_run`** - Base run speed (yards/sec).
- <a id="f-gender"></a>**`gender`** - `0` male, `1` female, `2` none.
- <a id="f-display_id_other_gender"></a>**`display_id_other_gender`** - Corresponding display ID for the opposite gender.
