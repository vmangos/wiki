# npc_vendor_template Table

Reusable vendor templates - assign to NPCs via [`creature_template`](creature_template.md).vendor_id.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`slot`](#f-slot) | smallint(5) unsigned |  | NO | 0 |  |
| [`item`](#f-item) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`maxcount`](#f-maxcount) | tinyint(3) unsigned |  | NO | 0 |  |
| [`incrtime`](#f-incrtime) | int(10) unsigned |  | NO | 0 |  |
| [`itemflags`](#f-itemflags) | int(10) unsigned |  | NO | 0 |  |
| [`condition_id`](#f-condition_id) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Vendor template ID. (see [`creature_template`](creature_template.md).vendor_id)
- <a id="f-slot"></a>**`slot`** - Vendor slot position.
- <a id="f-item"></a>**`item`** - Primary Key. Item ID. (see [`item_template`](item_template.md).entry)
- <a id="f-maxcount"></a>**`maxcount`** - Stock limit.
- <a id="f-incrtime"></a>**`incrtime`** - Restock time.
- <a id="f-itemflags"></a>**`itemflags`** - Flags: `0x01` random restock (item restocked at random intervals), `0x02` dynamic restock (restock rate scales with the online player population).
- <a id="f-condition_id"></a>**`condition_id`** - Condition. (see [`conditions`](conditions.md).condition_entry)
