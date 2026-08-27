# account_data Table

Stores account-wide client UI data (per type/keybind blobs), kept separately from per-character settings.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`account`](#f-account) | int(11) unsigned | PRI | NO | 0 |  |
| [`type`](#f-type) | int(11) unsigned | PRI | NO | 0 |  |
| [`time`](#f-time) | bigint(11) unsigned |  | NO | 0 |  |
| [`data`](#f-data) | longblob |  | NO |  |  |

---

## Field Breakdown

- <a id="f-account"></a>**`account`** - Primary Key. Account id ([`account`](../realmd/account.md).id) the data belongs to.
- <a id="f-type"></a>**`type`** - Primary Key. Global data type index: `0` = config (incl. camera), `2` = key bindings,
  `4` = macros (`GLOBAL_CACHE_MASK`). Per-character types live in [`character_account_data`](character_account_data.md).
- <a id="f-time"></a>**`time`** - Unix timestamp of last modification.
- <a id="f-data"></a>**`data`** - Raw client UI configuration text for this type (stored after zlib decompression).

*Account-wide counterpart: [`character_account_data`](character_account_data.md).*
