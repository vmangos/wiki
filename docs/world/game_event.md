# game_event Table

Defines world events - their start/end times, occurrence intervals, and holidays.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO |  |  |
| [`start_time`](#f-start_time) | timestamp |  | NO | '0000-00-00 00:00:00' |  |
| [`end_time`](#f-end_time) | timestamp |  | NO | '0000-00-00 00:00:00' |  |
| [`occurence`](#f-occurence) | bigint(20) unsigned |  | NO | 5184000 |  |
| [`length`](#f-length) | bigint(20) unsigned |  | NO | 2592000 |  |
| [`holiday`](#f-holiday) | mediumint(8) unsigned |  | NO | 0 |  |
| [`description`](#f-description) | varchar(255) |  | YES |  |  |
| [`hardcoded`](#f-hardcoded) | tinyint(3) |  | NO | 0 |  |
| [`disabled`](#f-disabled) | tinyint(3) |  | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned |  | NO | 10 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Unique event ID.
- <a id="f-start_time"></a>**`start_time`** - Event start timestamp.
- <a id="f-end_time"></a>**`end_time`** - Event end timestamp.
- <a id="f-occurence"></a>**`occurence`** - Interval between event repeats (in minutes).
- <a id="f-length"></a>**`length`** - Duration of the event (in minutes).
- <a id="f-holiday"></a>**`holiday`** - Holiday ID (from `Holidays.dbc`).
- <a id="f-description"></a>**`description`** - Human-readable name.
- <a id="f-hardcoded"></a>**`hardcoded`** - `1` if event logic is hardcoded in core.
- <a id="f-disabled"></a>**`disabled`** - `1` disables the event.
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
