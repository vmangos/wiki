# creature_linking_template Table

Template-level creature linking - all spawns of a given entry link to a master entry on a specific map.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`map`](#f-map) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`master_entry`](#f-master_entry) | mediumint(8) unsigned |  | NO | 0 |  |
| [`flag`](#f-flag) | mediumint(8) unsigned |  | NO | 0 |  |
| [`search_range`](#f-search_range) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Creature template entry of the follower ([`creature_template`](creature_template.md).entry).
- <a id="f-map"></a>**`map`** - Primary Key. Map ID where this link applies.
- <a id="f-master_entry"></a>**`master_entry`** - Template ID of the master creature.
- <a id="f-flag"></a>**`flag`** - Link behavior flags.
- <a id="f-search_range"></a>**`search_range`** - Radius within which to find the master.
