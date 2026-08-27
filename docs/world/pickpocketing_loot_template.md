# pickpocketing_loot_template Table

Loot tables for pickpocketing - items that can be stolen from creatures.

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

- <a id="f-entry"></a>**`entry`** - Primary Key. Loot list id referenced by the owner system (see Loot System page). (see [`creature_template`](creature_template.md).pickpocket_loot_id)
- <a id="f-item"></a>**`item`** - Primary Key. [`item_template`](item_template.md).entry granted when this loot line rolls.
- <a id="f-ChanceOrQuestChance"></a>**`ChanceOrQuestChance`** - Positive = plain % chance · negative = quest drop (% magnitude) · 100 always.
- <a id="f-groupid"></a>**`groupid`** - Equal-chance group id; rows sharing a group share the drop budget. 0 = independent roll.
- <a id="f-mincountOrRef"></a>**`mincountOrRef`** - Minimum stack size; a negative value `-n` pulls from [`reference_loot_template`](reference_loot_template.md).entry n.
- <a id="f-maxcount"></a>**`maxcount`** - Max stack size (or max pulls for references).
- <a id="f-condition_id"></a>**`condition_id`** - Optional [`conditions`](conditions.md) row gating this loot line.
- <a id="f-patch_min"></a>**`patch_min`** - Progression visibility window.
- <a id="f-patch_max"></a>**`patch_max`** - Progression visibility window.
