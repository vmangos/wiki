# transports Table

Defines transport vehicles (e.g., ships, zeppelins) with their path period and name.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`build`](#f-build) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`name`](#f-name) | text |  | YES |  |  |
| [`period`](#f-period) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Transport entry ID.
- <a id="f-build"></a>**`build`** - Primary Key. Client build.
- <a id="f-name"></a>**`name`** - Transport name.
- <a id="f-period"></a>**`period`** - Round-trip duration override (milliseconds). The core computes a period from the
  client taxi path; a non-zero value here replaces it. `0` keeps the computed value.
