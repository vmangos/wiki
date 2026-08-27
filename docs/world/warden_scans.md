# warden_scans Table

Defines Warden scans - anti-cheat checks for client memory modifications.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | smallint(5) unsigned | PRI | NO |  | auto_increment |
| [`type`](#f-type) | int(11) |  | YES | 0 |  |
| [`str`](#f-str) | text |  | YES |  |  |
| [`data`](#f-data) | text |  | YES |  |  |
| [`address`](#f-address) | int(11) |  | YES | 0 |  |
| [`length`](#f-length) | int(11) |  | YES | 0 |  |
| [`result`](#f-result) | tinytext |  | NO |  |  |
| [`flags`](#f-flags) | mediumint(8) unsigned |  | NO |  |  |
| [`penalty`](#f-penalty) | tinyint(4) |  | NO | -1 |  |
| [`build_min`](#f-build_min) | smallint(5) unsigned |  | NO | 5875 |  |
| [`build_max`](#f-build_max) | smallint(5) unsigned |  | NO | 5875 |  |
| [`comment`](#f-comment) | tinytext |  | NO |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Auto-increment primary key.
- <a id="f-type"></a>**`type`** - Windows scan type (`WindowsScanType`, `WardenScan.hpp`):

  | Value | Scan |
  | :---: | :--- |
  | 0 | READ_MEMORY - compare client memory bytes |
  | 1 | FIND_MODULE_BY_NAME - detect loaded cheat modules |
  | 2 | FIND_MEM_IMAGE_CODE_BY_HASH - hash memory-image code |
  | 3 | FIND_CODE_BY_HASH - hash function code |
  | 4 | HASH_CLIENT_FILE - verify game file integrity |
  | 5 | GET_LUA_VARIABLE - read Lua UI state |
  | 6 | API_CHECK - verify imported APIs |
  | 7 | FIND_DRIVER_BY_NAME - detect kernel drivers |
  | 8 | CHECK_TIMING_VALUES - timing/teleport consistency |

- <a id="f-str"></a>**`str`** - Name/string payload for module/driver/Lua lookups.
- <a id="f-data"></a>**`data`** - Expected bytes or hash payload (hex).
- <a id="f-length"></a><a id="f-address"></a>**`address`** / **`length`** - Client memory probe location and size (READ_MEMORY).
- <a id="f-result"></a>**`result`** - Expected comparison result.
- <a id="f-flags"></a>**`flags`** - `ScanFlags` bitmask (`WardenScan.hpp`):

  | Bit | Meaning |
  | ---: | :--- |
  | 0x01 | FromDatabase - row removed on `.reload` |
  | 0x02 | Windows client only |
  | 0x04 | macOS client only |
  | 0x08 | run once at initial login |
  | 0x20 | Maiev default-module scan |
  | 0x40 | requires MODULE_INITIALIZE first (File/Lua/Timing) |

- <a id="f-penalty"></a>**`penalty`** - `WardenActions` value applied on failure (`Anticheat.h`): `0` log, `1` kick,
  `2` ban. `-1` (255 as uint8) falls back to the global
  `Warden.DefaultPenalty` config (`mangosd.conf`, `Warden.DefaultPenalty`).
- <a id="f-build_max"></a><a id="f-build_min"></a>**`build_min` / `build_max`** - Client build range this scan applies to.
- <a id="f-comment"></a>**`comment`** - Description.
