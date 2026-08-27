# account Table

Account credentials and per-account settings (username, password hash/verifier, expansion, locale).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(11) unsigned | PRI | NO |  | auto_increment |
| [`username`](#f-username) | varchar(32) | UNI | NO |  |  |
| [`gmlevel`](#f-gmlevel) | tinyint(3) unsigned | MUL | NO | 0 |  |
| [`sessionkey`](#f-sessionkey) | longtext |  | YES |  |  |
| [`v`](#f-v) | longtext |  | YES |  |  |
| [`s`](#f-s) | longtext |  | YES |  |  |
| [`token_key`](#f-token_key) | varchar(100) |  | NO | '' |  |
| [`email`](#f-email) | text |  | YES |  |  |
| [`joindate`](#f-joindate) | timestamp |  | NO | current_timestamp() |  |
| [`last_ip`](#f-last_ip) | varchar(30) |  | NO | '0.0.0.0' |  |
| [`locked`](#f-locked) | tinyint(3) unsigned |  | NO | 0 |  |
| [`lock_country`](#f-lock_country) | varchar(2) |  | NO | '00' |  |
| [`last_login`](#f-last_login) | timestamp |  | NO | '0000-00-00 00:00:00' |  |
| [`online`](#f-online) | tinyint(4) |  | NO | 0 |  |
| [`expansion`](#f-expansion) | tinyint(3) unsigned |  | NO | 0 |  |
| [`mutetime`](#f-mutetime) | bigint(40) |  | NO | 0 |  |
| [`locale`](#f-locale) | tinyint(3) unsigned |  | NO | 0 |  |
| [`os`](#f-os) | varchar(4) |  | NO | '' |  |
| [`platform`](#f-platform) | varchar(4) |  | NO | '' |  |
| [`current_realm`](#f-current_realm) | tinyint(3) unsigned |  | NO | 0 |  |
| [`flags`](#f-flags) | int(10) unsigned |  | NO | 0 |  |
| [`security`](#f-security) | varchar(255) |  | YES |  |  |
| [`email_verif`](#f-email_verif) | tinyint(1) |  | NO | 0 |  |
| [`geolock_pin`](#f-geolock_pin) | int(11) |  | YES | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Account id (referenced as [`account`](account.md) in characters DB).
- <a id="f-username"></a>**`username`** - Unique. Login name (uppercase-normalized for lookups).
- <a id="f-gmlevel"></a>**`gmlevel`** - Legacy per-account GM level snapshot; live level comes from [`account_access`](account_access.md).gmlevel.
- <a id="f-sessionkey"></a>**`sessionkey`** - SRP6 session key written by realmd at each successful login; reused for
  reconnect and world-server authentication until replaced by the next login.
- <a id="f-v"></a>**`v`** - SRP6 verifier, never a plain password.
- <a id="f-s"></a>**`s`** - SRP6 salt used with `v` for the secure login handshake.
- <a id="f-token_key"></a>**`token_key`** - Authenticator token key when 2FA is enabled. (2FA secrets are stored in `security`).
- <a id="f-email"></a>**`email`** - Account e-mail (password recovery / identification).
- <a id="f-joindate"></a>**`joindate`** - Registration date.
- <a id="f-last_ip"></a>**`last_ip`** - IP of the most recent login.
- <a id="f-locked"></a>**`locked`** - Lock/authenticator bitmask (`LockFlag`): 1 = IP lock to `last_ip`, 2 = fixed PIN required, 4 = TOTP authenticator, 8 = always enforce authenticator, 16 = GeoIP country lock, 32 = GeoIP city lock.
- <a id="f-lock_country"></a>**`lock_country`** - Country code of the client's last-login IP (populated by external tooling); never written or read by core.
- <a id="f-last_login"></a>**`last_login`** - Timestamp of previous successful login.
- <a id="f-online"></a>**`online`** - 1 while logged into any realm served by auth server.
- <a id="f-expansion"></a>**`expansion`** - Expansion level (`.account set addon`): 0 classic, 1 TBC, 2 WotLK. Set via command only.
- <a id="f-mutetime"></a>**`mutetime`** - Unix timestamp until chat mutes expire (0 none).
- <a id="f-locale"></a>**`locale`** - Client locale id selected at login (drives localized DBC data).
- <a id="f-os"></a>**`os`** - OS identifier reported by client (Win/Mac).
- <a id="f-platform"></a>**`platform`** - Detailed platform string reported by client.
- <a id="f-current_realm"></a>**`current_realm`** - Last realm played (id).
- <a id="f-flags"></a>**`flags`** - Server-side account flag bits: `0x1` = muted from public chat channels
  (set by the anticheat for `SEC_PLAYER`s; read back at world login and enforced when sending messages to public channels).
- <a id="f-security"></a>**`security`** - Authenticator secret used to verify the fixed PIN or TOTP code entered at login.
- <a id="f-email_verif"></a>**`email_verif`** - E-mail verification state; with `ReqEmailVerification` enabled unverified accounts cannot log in.
- <a id="f-geolock_pin"></a>**`geolock_pin`** - PIN that must be entered at next login (set after suspicious logins); cleared once entered correctly.
