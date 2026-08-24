# ip_banned Table

Banned IP addresses/networks.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`ip`](#f-ip) | varchar(32) | PRI | NO | '0.0.0.0' |  |
| [`bandate`](#f-bandate) | int(11) |  | NO |  |  |
| [`unbandate`](#f-unbandate) | int(11) |  | NO |  |  |
| [`bannedby`](#f-bannedby) | varchar(50) |  | NO | '[Console]' |  |
| [`banreason`](#f-banreason) | varchar(50) |  | NO | 'no reason' |  |

---

## Field Breakdown

- <a id="f-ip"></a>**`ip`** - Primary Key. Banned IP address or pattern.
- <a id="f-bandate"></a>**`bandate`** - Start/end unix timestamps.
- <a id="f-unbandate"></a>**`unbandate`** - Start/end unix timestamps.
- <a id="f-bannedby"></a>**`bannedby`** - Staff account or console that issued the ban.
- <a id="f-banreason"></a>**`banreason`** - Reason text for the ban.
