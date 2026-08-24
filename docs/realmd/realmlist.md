# realmlist Table

Registered realms served by this auth server (name, address, type, security level).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(11) unsigned | PRI | NO |  | auto_increment |
| [`name`](#f-name) | varchar(32) | UNI | NO | '' |  |
| [`address`](#f-address) | varchar(32) |  | NO | '127.0.0.1' |  |
| [`localAddress`](#f-localAddress) | varchar(255) |  | NO | '127.0.0.1' |  |
| [`localSubnetMask`](#f-localSubnetMask) | varchar(255) |  | NO | '255.255.255.0' |  |
| [`port`](#f-port) | int(11) |  | NO | 8085 |  |
| [`icon`](#f-icon) | tinyint(3) unsigned |  | NO | 0 |  |
| [`realmflags`](#f-realmflags) | tinyint(3) unsigned |  | NO | 2 |  |
| [`timezone`](#f-timezone) | tinyint(3) unsigned |  | NO | 0 |  |
| [`allowedSecurityLevel`](#f-allowedSecurityLevel) | tinyint(3) unsigned |  | NO | 0 |  |
| [`population`](#f-population) | float unsigned |  | NO | 0 |  |
| [`gamebuild_min`](#f-gamebuild_min) | int(11) unsigned |  | NO | 0 |  |
| [`gamebuild_max`](#f-gamebuild_max) | int(11) unsigned |  | NO | 0 |  |
| [`flag`](#f-flag) | tinyint(3) unsigned |  | NO | 2 |  |
| [`realmbuilds`](#f-realmbuilds) | varchar(64) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Realm id clients select.
- <a id="f-name"></a>**`name`** - Unique. Displayed realm name.
- <a id="f-address"></a>**`address`** - Public address clients connect to (host or IP).
- <a id="f-localAddress"></a>**`localAddress`** - Address handed to clients inside the local network.
- <a id="f-localSubnetMask"></a>**`localSubnetMask`** - Subnet mask deciding which clients count as local (dotted format).
- <a id="f-port"></a>**`port`** - World server port (default 8085).
- <a id="f-icon"></a>**`icon`** - Realm type: 0 normal, 1 PvP, 4 normal variant (`REALM_TYPE_NORMAL2`), 6 RP, 8 RPPvP. The custom FFA-PvP mode (16) is stored as 1 in this column.
- <a id="f-realmflags"></a>**`realmflags`** - Bitmask: 1 invalid (realm hidden from clients), 2 offline, 4 specify build (show version next to name), 32 new players, 64 recommended, 128 full (defined but not set by this core). Only 2, 4, 32 and 64 may be set in DB; realmd shows realms as offline dynamically when the client build is unsupported or the realm is locked.
- <a id="f-timezone"></a>**`timezone`** - Realm timezone grouping for the realm list sort.
- <a id="f-allowedSecurityLevel"></a>**`allowedSecurityLevel`** - Minimum account security required to enter this realm (realms above the account level show as locked).
- <a id="f-population"></a>**`population`** - Population level float shown as low/medium/high. Updated by mangosd.
- <a id="f-gamebuild_min"></a>**`gamebuild_min`** - Accepted client build range. Not read by this core; kept for compatibility.
- <a id="f-gamebuild_max"></a>**`gamebuild_max`** - Accepted client build range. Not read by this core; kept for compatibility.
- <a id="f-flag"></a>**`flag`** - Additional display flag byte. Not read by this core; kept for compatibility.
- <a id="f-realmbuilds"></a>**`realmbuilds`** - Explicit comma-separated accepted build list overriding min/max. Written by mangosd at startup.
