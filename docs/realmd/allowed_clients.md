# allowed_clients Table

Whitelist of client builds/platforms permitted to log on through realmd. The table must contain at least one row;
realmd exits at startup with "No valid client builds specified." otherwise. Builds greater than or equal to the
first (lowest) listed build number are accepted.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`major_version`](#f-major_version) | tinyint(3) unsigned |  | NO |  |  |
| [`minor_version`](#f-minor_version) | tinyint(3) unsigned |  | NO |  |  |
| [`bugfix_version`](#f-bugfix_version) | tinyint(3) unsigned |  | NO |  |  |
| [`hotfix_version`](#f-hotfix_version) | char(1) |  | NO |  |  |
| [`build`](#f-build) | mediumint(8) unsigned |  | NO |  |  |
| [`os`](#f-os) | char(50) |  | NO |  |  |
| [`platform`](#f-platform) | char(50) |  | NO |  |  |
| [`integrity_hash`](#f-integrity_hash) | varchar(40) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-major_version"></a>**`major_version`** - Exact client version components accepted.
- <a id="f-minor_version"></a>**`minor_version`** - Exact client version components accepted.
- <a id="f-bugfix_version"></a>**`bugfix_version`** - Exact client version components accepted.
- <a id="f-hotfix_version"></a>**`hotfix_version`** - Exact client version components accepted.
- <a id="f-build"></a>**`build`** - Client build number (e.g. 5875 for 1.12.1).
- <a id="f-os"></a>**`os`** - Operating platform filter, exact string match against the client-reported value (`Win`/`OSX`).
- <a id="f-platform"></a>**`platform`** - Architecture/platform string filter, exact match against the client-reported value (`x86`/`PPC`).
- <a id="f-integrity_hash"></a>**`integrity_hash`** - Optional client integrity hash requirement.
