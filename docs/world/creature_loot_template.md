# creature_loot_template Table

Loot tables for creatures - defines items, drop chances, groups, and patch ranges.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`item`](#f-item) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`ChanceOrQuestChance`](#f-ChanceOrQuestChance) | float |  | NO | 100 |  |
| [`groupid`](#f-groupid) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`mincountOrRef`](#f-mincountOrRef) | mediumint(9) |  | NO | 1 |  |
| [`maxcount`](#f-maxcount) | tinyint(3) unsigned |  | NO | 1 |  |
| [`condition_id`](#f-condition_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned | PRI | NO | 10 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Creature loot ID = [`creature_template`](creature_template.md).loot_id
  (a creature with `loot_id` = 0 has no body loot).
- <a id="f-item"></a>**`item`** - Primary Key. Item ID from [`item_template`](item_template.md).entry.
- <a id="f-ChanceOrQuestChance"></a>**`ChanceOrQuestChance`** - Drop percentage (0-100). Negative values indicate quest item chance.
- <a id="f-groupid"></a>**`groupid`** - Primary Key. Loot group (items in same group are mutually exclusive).
- <a id="f-mincountOrRef"></a>**`mincountOrRef`** - Minimum stack size; a negative value `-n` pulls from [`reference_loot_template`](reference_loot_template.md).entry n.
- <a id="f-maxcount"></a>**`maxcount`** - Maximum stack count.
- <a id="f-condition_id"></a>**`condition_id`** - Condition that must be met for the drop. (see [`conditions`](conditions.md).condition_entry)
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
