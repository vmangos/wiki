# system_fingerprint_usage Table

Records system fingerprint usage during logon - part of anti-cheat/multi-boxing detection.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(10) unsigned | PRI | NO |  | auto_increment |
| [`fingerprint`](#f-fingerprint) | int(10) unsigned | MUL | NO |  |  |
| [`account`](#f-account) | int(10) unsigned | MUL | NO |  |  |
| [`ip`](#f-ip) | varchar(16) | MUL | NO |  |  |
| [`realm`](#f-realm) | int(10) unsigned |  | NO |  |  |
| [`time`](#f-time) | timestamp |  | NO | current_timestamp() |  |
| [`architecture`](#f-architecture) | varchar(16) |  | YES |  |  |
| [`cputype`](#f-cputype) | varchar(64) |  | YES |  |  |
| [`activecpus`](#f-activecpus) | int(10) unsigned |  | YES |  |  |
| [`totalcpus`](#f-totalcpus) | int(10) unsigned |  | YES |  |  |
| [`pagesize`](#f-pagesize) | int(10) unsigned |  | YES |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Row id.
- <a id="f-fingerprint"></a>**`fingerprint`** - System fingerprint hash; the core does not currently implement fingerprinting and always stores `0`.
- <a id="f-account"></a>**`account`** - Account using the fingerprint ([`account`](../realmd/account.md).id).
- <a id="f-ip"></a>**`ip`** - Source IP.
- <a id="f-realm"></a>**`realm`** - Realm id.
- <a id="f-time"></a>**`time`** - Row insert timestamp (each observation is one row).
- <a id="f-architecture"></a>**`architecture`** - Machine characteristics collected with the fingerprint.
- <a id="f-cputype"></a>**`cputype`** - Machine characteristics collected with the fingerprint.
- <a id="f-activecpus"></a>**`activecpus`** - Machine characteristics collected with the fingerprint.
- <a id="f-totalcpus"></a>**`totalcpus`** - Machine characteristics collected with the fingerprint.
- <a id="f-pagesize"></a>**`pagesize`** - Machine characteristics collected with the fingerprint.
