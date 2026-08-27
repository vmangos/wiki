# fishing_loot_template Table

Loot tables for fishing - defines items catchable in specific zones.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`item`](#f-item) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`ChanceOrQuestChance`](#f-ChanceOrQuestChance) | float |  | NO | 100 |  |
| [`groupid`](#f-groupid) | tinyint(3) unsigned |  | NO | 0 |  |
| [`mincountOrRef`](#f-mincountOrRef) | mediumint(9) |  | NO | 1 |  |
| [`maxcount`](#f-maxcount) | tinyint(3) unsigned |  | NO | 1 |  |
| [`condition_id`](#f-condition_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned |  | NO | 10 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Zone ID or fishing area.
- <a id="f-item"></a>**`item`** - Primary Key. Item ID. (see [`item_template`](item_template.md).entry)
- <a id="f-ChanceOrQuestChance"></a>**`ChanceOrQuestChance`** - Drop probability.
- <a id="f-groupid"></a>**`groupid`** - Loot group.
- <a id="f-mincountOrRef"></a>**`mincountOrRef`** - Minimum stack size; a negative value `-n` pulls from [`reference_loot_template`](reference_loot_template.md).entry n.
- <a id="f-maxcount"></a>**`maxcount`** - Maximum stack count.
- <a id="f-condition_id"></a>**`condition_id`** - Condition. (see [`conditions`](conditions.md).condition_entry)
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
