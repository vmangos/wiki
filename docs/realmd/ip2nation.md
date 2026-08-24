# ip2nation Table

Mapping of IP ranges to country codes for GeoIP lookups.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`ip`](#f-ip) | int(11) unsigned | MUL | NO | 0 |  |
| [`country`](#f-country) | char(2) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-ip"></a>**`ip`** - Leading IP block key.
- <a id="f-country"></a>**`country`** - Two-letter country code.
