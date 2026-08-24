# pet_spell_cooldown Table

Pet spell cooldowns persisting across logout.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`spell`](#f-spell) | int(11) unsigned | PRI | NO | 0 |  |
| [`time`](#f-time) | bigint(20) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Part of the primary key. Global Unique Identifier, Low part
- <a id="f-spell"></a>**`spell`** - Part of the primary key. Spell Identifier
- <a id="f-time"></a>**`time`** - Cooldown expiry timestamp (unix time).
