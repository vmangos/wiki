# npc_vendor Table

Defines items sold by specific NPC vendors (per-spawn or per-entry).

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

- <a id="f-entry"></a>**`entry`** - Primary Key. NPC entry ID ([`creature_template`](creature_template.md).entry).
- <a id="f-slot"></a>**`slot`** - Vendor slot position.
- <a id="f-item"></a>**`item`** - Primary Key. Item ID ([`item_template`](item_template.md).entry).
- <a id="f-maxcount"></a>**`maxcount`** - Maximum stock count (0 = unlimited).
- <a id="f-incrtime"></a>**`incrtime`** - Restock interval (seconds).
- <a id="f-itemflags"></a>**`itemflags`** - Flags: `0x01` random restock (item restocked at random intervals), `0x02` dynamic restock (restock rate scales with the online player population).
- <a id="f-condition_id"></a>**`condition_id`** - Condition required to see/buy the item. (see [`conditions`](conditions.md).condition_entry)
