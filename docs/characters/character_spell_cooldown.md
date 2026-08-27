# character_spell_cooldown Table

Spell cooldowns persisting across logout.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`spell`](#f-spell) | int(11) unsigned | PRI | NO | 0 |  |
| [`spell_expire_time`](#f-spell_expire_time) | bigint(20) unsigned |  | NO | 0 |  |
| [`category`](#f-category) | int(11) unsigned |  | NO | 0 |  |
| [`category_expire_time`](#f-category_expire_time) | bigint(20) unsigned |  | NO | 0 |  |
| [`item_id`](#f-item_id) | int(11) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-spell"></a>**`spell`** - Primary Key. Spell on cooldown.
- <a id="f-spell_expire_time"></a>**`spell_expire_time`** - Unix timestamp when the spell cooldown ends.
- <a id="f-category"></a>**`category`** - Cooldown category id (shared-category cooldowns).
- <a id="f-category_expire_time"></a>**`category_expire_time`** - Category cooldown expiry timestamp.
- <a id="f-item_id"></a>**`item_id`** - Item causing the cooldown (item cooldowns), else 0.
