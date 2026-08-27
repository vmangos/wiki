# battlemaster_entry Table

Defines which creatures are battlemasters and which battleground they represent.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`bg_template`](#f-bg_template) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Creature ID from [`creature_template`](creature_template.md).entry.
- <a id="f-bg_template"></a>**`bg_template`** - Battleground ID from [`battleground_template`](battleground_template.md).id:
  - `1` - Alterac Valley
  - `2` - Warsong Gulch
  - `3` - Arathi Basin
