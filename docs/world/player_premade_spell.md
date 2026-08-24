# player_premade_spell Table

Defines spells granted to premade characters.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | int(10) unsigned | PRI | NO |  |  |
| [`spell`](#f-spell) | smallint(5) unsigned | PRI | NO |  |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Premade template ID. (see [`player_premade_item_template`](player_premade_item_template.md).entry)
- <a id="f-spell"></a>**`spell`** - Primary Key. Spell ID. (see [`spell_template`](spell_template.md).entry)
