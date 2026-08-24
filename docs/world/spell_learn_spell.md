# spell_learn_spell Table

Defines spells that are learned automatically when another spell is learned (e.g., passive rank-ups).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`SpellID`](#f-SpellID) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`Active`](#f-Active) | tinyint(3) unsigned |  | NO | 1 |  |
| [`build_min`](#f-build_min) | smallint(4) unsigned |  | NO | 0 |  |
| [`build_max`](#f-build_max) | smallint(4) unsigned |  | NO | 5875 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Source spell ID.; references [`spell_template`](spell_template.md).entry
- <a id="f-SpellID"></a>**`SpellID`** - Primary Key. Spell learned automatically.; references [`spell_template`](spell_template.md).entry
- <a id="f-Active"></a>**`Active`** - `1` active, `0` inactive.
- <a id="f-build_max"></a><a id="f-build_min"></a>**`build_min` / `build_max`** - Client build range.
