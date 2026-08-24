# character_action Table

Player action bar button assignments (spells/items placed on slots).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`button`](#f-button) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`action`](#f-action) | int(11) unsigned |  | NO | 0 |  |
| [`type`](#f-type) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Part of the primary key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-button"></a>**`button`** - Part of the primary key. Action bar button index (0-119 across bars/pages).
- <a id="f-action"></a>**`action`** - Content id placed on the button: spell id or item id depending on `type`.
- <a id="f-type"></a>**`type`** - Button content type (`ActionButtonType`, `Player.h`): `0x00` spell,
  `0x40` macro, `0x80` item. Defines how the client interprets `action`.
