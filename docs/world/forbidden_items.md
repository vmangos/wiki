# forbidden_items Table

Items that are forbidden from being used or obtained in certain patches.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`patch`](#f-patch) | tinyint(3) unsigned |  | NO | 0 |  |
| [`after_or_before`](#f-after_or_before) | tinyint(3) unsigned | PRI | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Item ID. (see [`item_template`](item_template.md).entry)
- <a id="f-patch"></a>**`patch`** - Patch version.
- <a id="f-after_or_before"></a>**`after_or_before`** - `0` = item removed at `patch`; forbidden from that patch onward. `1` = item added at `patch`; forbidden until that patch.
