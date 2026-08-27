# character_account_data Table

Per-character client UI data blobs (window layouts, action settings), stored by data type.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`type`](#f-type) | int(11) unsigned | PRI | NO | 0 |  |
| [`time`](#f-time) | bigint(11) unsigned |  | NO | 0 |  |
| [`data`](#f-data) | longblob |  | NO |  |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character guid these settings belong to ([`characters`](characters.md).guid).
- <a id="f-type"></a>**`type`** - Primary Key. Per-character data type index (`1` = config, `3` = bindings, `5` = macros,
  `6` = layout, `7` = chat; `PER_CHARACTER_CACHE_MASK`). Global types 0/2/4 live in [`account_data`](account_data.md).
- <a id="f-time"></a>**`time`** - Unix timestamp of last modification.
- <a id="f-data"></a>**`data`** - Client UI configuration blob.

*Per-character variant: [`account_data`](account_data.md).*
