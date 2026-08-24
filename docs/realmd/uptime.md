# uptime Table

Uptime history of the realm(s): start time, player peak, revision.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`realmid`](#f-realmid) | int(11) unsigned | PRI | NO |  |  |
| [`starttime`](#f-starttime) | bigint(20) unsigned | PRI | NO | 0 |  |
| [`startstring`](#f-startstring) | varchar(64) |  | NO | '' |  |
| [`uptime`](#f-uptime) | bigint(20) unsigned |  | NO | 0 |  |
| [`onlineplayers`](#f-onlineplayers) | smallint(5) unsigned |  | NO | 0 |  |
| [`maxplayers`](#f-maxplayers) | smallint(5) unsigned |  | NO | 0 |  |
| [`revision`](#f-revision) | varchar(255) |  | NO | 'VMangos' |  |

---

## Field Breakdown

- <a id="f-realmid"></a>**`realmid`** - Part of the primary key. Realm reporting uptime.
- <a id="f-starttime"></a>**`starttime`** - Part of the primary key. Process start time (numeric + text form).
- <a id="f-startstring"></a>**`startstring`** - Process start time (numeric + text form).
- <a id="f-uptime"></a>**`uptime`** - Seconds running at last update.
- <a id="f-onlineplayers"></a>**`onlineplayers`** - Players online at the last periodic update.
- <a id="f-maxplayers"></a>**`maxplayers`** - Peak concurrent players this session.
- <a id="f-revision"></a>**`revision`** - Core git revision the binary was built from.
