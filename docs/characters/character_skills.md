# character_skills Table

Learned skills and their current/max values (professions, weapon skills).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO |  |  |
| [`skill`](#f-skill) | mediumint(9) unsigned | PRI | NO |  |  |
| [`value`](#f-value) | mediumint(9) unsigned |  | NO |  |  |
| [`max`](#f-max) | mediumint(9) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-skill"></a>**`skill`** - Primary Key. Skill line id (weapon skills, professions, secondary skills).
- <a id="f-value"></a>**`value`** - Current skill value.
- <a id="f-max"></a>**`max`** - Current cap (grows with level/profession tier).
