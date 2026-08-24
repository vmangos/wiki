# spell_cone Table

Defines cone angles for spells with cone area of effect.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO |  |  |
| [`cone_degrees`](#f-cone_degrees) | smallint(6) |  | NO |  |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-cone_degrees"></a>**`cone_degrees`** - Cone angle in degrees.
