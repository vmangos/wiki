# playercreateinfo_spell Table

Defines starting spells for each race/class combination.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`race`](#f-race) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`class`](#f-class) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`spell`](#f-spell) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`build_min`](#f-build_min) | smallint(4) unsigned |  | NO | 0 |  |
| [`build_max`](#f-build_max) | smallint(4) unsigned |  | NO | 5875 |  |
| [`note`](#f-note) | varchar(255) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-race"></a>**`race`** - Primary Key. Race ID.
- <a id="f-class"></a>**`class`** - Primary Key. Class ID.
- <a id="f-spell"></a>**`spell`** - Primary Key. Spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-build_max"></a><a id="f-build_min"></a>**`build_min` / `build_max`** - Client build range.
- <a id="f-note"></a>**`note`** - Comment.
