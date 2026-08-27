# saved_variables Table

Single-row table of global flags saved between restarts (honour maintenance bookkeeping, character-cleaner phase markers).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`key`](#f-key) | tinyint(1) unsigned | PRI | NO | 0 |  |
| [`cleaning_flags`](#f-cleaning_flags) | int(11) unsigned |  | NO | 0 |  |
| [`honor_last_maintenance_day`](#f-honor_last_maintenance_day) | int(11) unsigned |  | NO | 0 |  |
| [`honor_next_maintenance_day`](#f-honor_next_maintenance_day) | int(11) unsigned |  | NO | 0 |  |
| [`honor_maintenance_marker`](#f-honor_maintenance_marker) | tinyint(1) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-key"></a>**`key`** - Primary Key (always `0`); each variable is its own column of this one-row table.
- <a id="f-cleaning_flags"></a>**`cleaning_flags`** - Cleanup-phase markers used during maintenance.
- <a id="f-honor_last_maintenance_day"></a>**`honor_last_maintenance_day`** - Honour day tick bookkeeping.
- <a id="f-honor_next_maintenance_day"></a>**`honor_next_maintenance_day`** - Honour day tick bookkeeping.
- <a id="f-honor_maintenance_marker"></a>**`honor_maintenance_marker`** - Honour day tick bookkeeping.
