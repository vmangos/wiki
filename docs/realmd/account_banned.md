# account_banned Table

Account ban records with reason and expiration.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`banid`](#f-banid) | bigint(20) | UNI | NO |  | auto_increment |
| [`id`](#f-id) | bigint(20) | PRI | NO | 0 |  |
| [`bandate`](#f-bandate) | bigint(40) | PRI | NO | 0 |  |
| [`unbandate`](#f-unbandate) | bigint(40) |  | NO | 0 |  |
| [`bannedby`](#f-bannedby) | varchar(50) |  | NO |  |  |
| [`banreason`](#f-banreason) | varchar(255) |  | NO |  |  |
| [`active`](#f-active) | tinyint(4) |  | NO | 1 |  |
| [`realm`](#f-realm) | tinyint(4) |  | NO | 1 |  |
| [`gmlevel`](#f-gmlevel) | tinyint(4) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-banid"></a>**`banid`** - Unique. Ban record id.
- <a id="f-id"></a>**`id`** - Part of the primary key. Account id from [`account`](account.md).id.
- <a id="f-bandate"></a>**`bandate`** - Part of the primary key. Start unix timestamp of the ban.
- <a id="f-unbandate"></a>**`unbandate`** - End unix timestamp of the ban (equal to `bandate` for permanent bans).
- <a id="f-bannedby"></a>**`bannedby`** - Name of the staff member or console that issued the ban.
- <a id="f-banreason"></a>**`banreason`** - Reason text shown to staff.
- <a id="f-active"></a>**`active`** - 1 while ban is in effect; expired bans are deactivated at startup.
- <a id="f-realm"></a>**`realm`** - Id of the realm that issued the ban.
- <a id="f-gmlevel"></a>**`gmlevel`** - Minimum GM level required to view the ban reason via `.baninfo`.
