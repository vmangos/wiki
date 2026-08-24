# pet_spell Table

Spells known by persistent pets.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`spell`](#f-spell) | int(11) unsigned | PRI | NO | 0 |  |
| [`active`](#f-active) | int(11) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Part of the primary key. Global Unique Identifier
- <a id="f-spell"></a>**`spell`** - Part of the primary key. Spell Identifier
- <a id="f-active"></a>**`active`** - `ActiveStates` toggle (`UnitDefines.h`): `0x01` passive, `0x81` disabled/castable (off), `0xC1` auto-cast + castable.
