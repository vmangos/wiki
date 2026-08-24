# character_spell Table

Spells learned by the character.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`spell`](#f-spell) | int(11) unsigned | PRI | NO | 0 |  |
| [`active`](#f-active) | tinyint(3) unsigned |  | NO | 1 |  |
| [`disabled`](#f-disabled) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Part of the primary key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-spell"></a>**`spell`** - Part of the primary key. Learned spell id.
- <a id="f-active"></a>**`active`** - 1 if spell is in an action-bar usable state (toggled spells like auras).
- <a id="f-disabled"></a>**`disabled`** - 1 = temporarily disabled by core (cannot be cast).
