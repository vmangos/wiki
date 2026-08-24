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
- <a id="f-type"></a>**`type`** - Primary Key. Data slot 0-7 (per-type client config blob: key bindings, camera settings, layout…).
- <a id="f-time"></a>**`time`** - Unix timestamp of last modification.
- <a id="f-data"></a>**`data`** - Compressed/encoded client UI blob for this type.

*Account-wide counterpart: [`character_account_data`](character_account_data.md).*
