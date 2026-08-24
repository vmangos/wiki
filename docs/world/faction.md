# faction Table

Defines reputation factions, their base standings per race/class, and other properties.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | smallint(3) unsigned | PRI | NO | 0 |  |
| [`build`](#f-build) | smallint(4) unsigned | PRI | NO | 5875 |  |
| [`reputation_list_id`](#f-reputation_list_id) | mediumint(9) |  | NO | 0 |  |
| [`base_rep_race_mask1`](#f-base_rep_race_mask1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`base_rep_race_mask2`](#f-base_rep_race_mask2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`base_rep_race_mask3`](#f-base_rep_race_mask3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`base_rep_race_mask4`](#f-base_rep_race_mask4) | mediumint(8) unsigned |  | NO | 0 |  |
| [`base_rep_class_mask1`](#f-base_rep_class_mask1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`base_rep_class_mask2`](#f-base_rep_class_mask2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`base_rep_class_mask3`](#f-base_rep_class_mask3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`base_rep_class_mask4`](#f-base_rep_class_mask4) | mediumint(8) unsigned |  | NO | 0 |  |
| [`base_rep_value1`](#f-base_rep_value1) | mediumint(9) |  | NO | 0 |  |
| [`base_rep_value2`](#f-base_rep_value2) | mediumint(9) |  | NO | 0 |  |
| [`base_rep_value3`](#f-base_rep_value3) | mediumint(9) |  | NO | 0 |  |
| [`base_rep_value4`](#f-base_rep_value4) | mediumint(9) |  | NO | 0 |  |
| [`reputation_flags1`](#f-reputation_flags1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`reputation_flags2`](#f-reputation_flags2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`reputation_flags3`](#f-reputation_flags3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`reputation_flags4`](#f-reputation_flags4) | mediumint(8) unsigned |  | NO | 0 |  |
| [`team`](#f-team) | mediumint(8) unsigned |  | NO | 0 |  |
| [`name`](#f-name) | varchar(256) |  | NO | '' |  |
| [`description`](#f-description) | varchar(512) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Part of the primary key. Faction (reputation group) id.
- <a id="f-build"></a>**`build`** - Part of the primary key. Client build this row targets.
- <a id="f-reputation_list_id"></a>**`reputation_list_id`** - Index players see in the rep pane (-1 not listed).
- <a id="f-base_rep_race_mask1"></a>**`base_rep_race_mask1`** - Race mask that receives the paired base_rep_value at creation.
- <a id="f-base_rep_race_mask2"></a>**`base_rep_race_mask2`** - Race mask that receives the paired base_rep_value at creation.
- <a id="f-base_rep_race_mask3"></a>**`base_rep_race_mask3`** - Race mask that receives the paired base_rep_value at creation.
- <a id="f-base_rep_race_mask4"></a>**`base_rep_race_mask4`** - Race mask that receives the paired base_rep_value at creation.
- <a id="f-base_rep_class_mask1"></a>**`base_rep_class_mask1`** - Class mask variant of the same pairing.
- <a id="f-base_rep_class_mask2"></a>**`base_rep_class_mask2`** - Class mask variant of the same pairing.
- <a id="f-base_rep_class_mask3"></a>**`base_rep_class_mask3`** - Class mask variant of the same pairing.
- <a id="f-base_rep_class_mask4"></a>**`base_rep_class_mask4`** - Class mask variant of the same pairing.
- <a id="f-base_rep_value1"></a>**`base_rep_value1`** - Starting reputation for the corresponding mask row.
- <a id="f-base_rep_value2"></a>**`base_rep_value2`** - Starting reputation for the corresponding mask row.
- <a id="f-base_rep_value3"></a>**`base_rep_value3`** - Starting reputation for the corresponding mask row.
- <a id="f-base_rep_value4"></a>**`base_rep_value4`** - Starting reputation for the corresponding mask row.
- <a id="f-reputation_flags1"></a>**`reputation_flags1`** - Per-rank flags (visible/forgotten-at-war behaviour bits).
- <a id="f-reputation_flags2"></a>**`reputation_flags2`** - Per-rank flags (visible/forgotten-at-war behaviour bits).
- <a id="f-reputation_flags3"></a>**`reputation_flags3`** - Per-rank flags (visible/forgotten-at-war behaviour bits).
- <a id="f-reputation_flags4"></a>**`reputation_flags4`** - Per-rank flags (visible/forgotten-at-war behaviour bits).
- <a id="f-team"></a>**`team`** - Parent faction chain link for spillover/aggregation.
- <a id="f-name"></a>**`name`** - Display strings.
- <a id="f-description"></a>**`description`** - Display strings.

*Referenced by: [`item_template`](item_template.md).RequiredReputationFaction and other reputation-requiring columns.*
