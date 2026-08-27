# gossip_menu Table

Defines gossip menus - links NPCs to text and script logic.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(6) unsigned | PRI | NO | 0 |  |
| [`text_id`](#f-text_id) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`script_id`](#f-script_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`condition_id`](#f-condition_id) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Menu ID (referenced by [`creature_template`](creature_template.md).gossip_menu_id).
- <a id="f-text_id"></a>**`text_id`** - Primary Key. Text ID ([`npc_text`](npc_text.md).ID).
- <a id="f-script_id"></a>**`script_id`** - Script ID for gossip action. (see Script system.)
- <a id="f-condition_id"></a>**`condition_id`** - Condition required for this menu to appear. (see [`conditions`](conditions.md).condition_entry)
