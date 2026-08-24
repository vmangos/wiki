# group_member Table

Members of each party/raid group.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`group_id`](#f-group_id) | int(11) unsigned | PRI | NO |  |  |
| [`member_guid`](#f-member_guid) | int(11) unsigned | PRI | NO |  |  |
| [`assistant`](#f-assistant) | tinyint(1) unsigned |  | NO |  |  |
| [`subgroup`](#f-subgroup) | smallint(6) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-group_id"></a>**`group_id`** - Primary Key. Group header row.
- <a id="f-member_guid"></a>**`member_guid`** - Primary Key. Member character guid ([`characters`](characters.md).guid).
- <a id="f-assistant"></a>**`assistant`** - Raid assistant flag (can mark/invite).
- <a id="f-subgroup"></a>**`subgroup`** - Raid subgroup index 0-7 (displayed as subgroup 1-8 in the client).
