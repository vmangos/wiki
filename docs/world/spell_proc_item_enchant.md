# spell_proc_item_enchant Table

Defines proc rates for item enchantments (PPM).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO |  |  |
| [`ppmRate`](#f-ppmRate) | float |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Enchantment spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-ppmRate"></a>**`ppmRate`** - Procs per minute rate.
