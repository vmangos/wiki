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

- <a id="f-guid"></a>**`guid`** - Part of the primary key. Character guid these settings belong to ([`characters`](characters.md).guid).
- <a id="f-type"></a>**`type`** - Part of the primary key. Data slot 0-7 (same slots as [`account_data`](account_data.md), but per character).
- <a id="f-time"></a>**`time`** - Unix timestamp of last modification.
- <a id="f-data"></a>**`data`** - Client UI configuration blob.

*Per-character variant: [`account_data`](account_data.md).*
