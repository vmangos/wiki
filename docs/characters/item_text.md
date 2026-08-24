# item_text Table

Text written on letter-stationery items (old book items) - deprecated content.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(11) unsigned | PRI | NO | 0 |  |
| [`text`](#f-text) | longtext |  | YES |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Text id referenced by [`item_instance`](item_instance.md).text.
- <a id="f-text"></a>**`text`** - Page body for readable in-game books.
