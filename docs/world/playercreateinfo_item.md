# playercreateinfo_item Table

Defines starting items for each race/class combination.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`race`](#f-race) | tinyint(3) unsigned | MUL | NO | 0 |  |
| [`class`](#f-class) | tinyint(3) unsigned |  | NO | 0 |  |
| [`itemid`](#f-itemid) | mediumint(8) unsigned |  | NO | 0 |  |
| [`amount`](#f-amount) | tinyint(3) unsigned |  | NO | 1 |  |

---

## Field Breakdown

- <a id="f-race"></a>**`race`** - Race ID.
- <a id="f-class"></a>**`class`** - Class ID.
- <a id="f-itemid"></a>**`itemid`** - Item ID ([`item_template`](item_template.md).entry).
- <a id="f-amount"></a>**`amount`** - Quantity.
