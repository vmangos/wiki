# character_forgotten_skills Table

Skills explicitly unlearned from a character (weapon skill resets); remembered so they are not re-granted automatically.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO |  |  |
| [`skill`](#f-skill) | mediumint(9) unsigned | PRI | NO |  |  |
| [`value`](#f-value) | mediumint(9) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-skill"></a>**`skill`** - Primary Key. Skill line id that was unlearned (e.g. via GM reset).
- <a id="f-value"></a>**`value`** - Former skill value, kept so it can be restored.
