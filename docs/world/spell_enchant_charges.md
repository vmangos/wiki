# spell_enchant_charges Table

Defines the number of charges for item enchantments.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO |  |  |
| [`charges`](#f-charges) | int(10) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Enchantment spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-charges"></a>**`charges`** - Number of charges.
