# pet_name_generation Table

Generates random names for summoned pets (e.g. warlock minions). Hunter pets instead get their creature-family name and can be renamed by the player.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | mediumint(8) unsigned | PRI | NO |  | auto_increment |
| [`word`](#f-word) | tinytext |  | NO |  |  |
| [`entry`](#f-entry) | mediumint(8) unsigned |  | NO | 0 |  |
| [`half`](#f-half) | tinyint(4) |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key, auto-increment.
- <a id="f-word"></a>**`word`** - Syllable or word fragment.
- <a id="f-entry"></a>**`entry`** - Creature entry (pet family) - if 0, applies to all. (see [`creature_template`](creature_template.md).entry (if set))
- <a id="f-half"></a>**`half`** - `0` = first half, `1` = second half.
