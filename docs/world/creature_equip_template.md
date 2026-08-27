# creature_equip_template Table

Defines equipment sets for creatures - up to three items (main hand, off hand, ranged).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`probability`](#f-probability) | mediumint(8) unsigned |  | NO | 1 |  |
| [`item1`](#f-item1) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`item2`](#f-item2) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`item3`](#f-item3) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned |  | NO | 10 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** (mediumint(8) unsigned) - Primary Key. Equipment set ID, referenced by [`creature_template`](creature_template.md).equipment_id.
- <a id="f-probability"></a>**`probability`** - Weight for random selection among multiple sets.
- <a id="f-item1"></a>**`item1`** - Main hand item (from [`item_template`](item_template.md).entry).
- <a id="f-item2"></a>**`item2`** - Off hand / shield item.
- <a id="f-item3"></a>**`item3`** - Ranged / two-handed item.
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
