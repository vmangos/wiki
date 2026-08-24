# skill_fishing_base_level Table

Defines base fishing skill required per zone/area.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`skill`](#f-skill) | smallint(6) |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Zone/area ID. (see `AreaTable.dbc`)
- <a id="f-skill"></a>**`skill`** - Minimum fishing skill required.
