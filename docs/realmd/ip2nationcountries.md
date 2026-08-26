# ip2nationcountries Table

Country metadata for [`ip2nation`](ip2nation.md). Not read or written by core.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`code`](#f-code) | varchar(4) | PRI | NO | '' |  |
| [`iso_code_2`](#f-iso_code_2) | varchar(2) |  | NO | '' |  |
| [`iso_code_3`](#f-iso_code_3) | varchar(3) |  | YES | '' |  |
| [`iso_country`](#f-iso_country) | varchar(255) |  | NO | '' |  |
| [`country`](#f-country) | varchar(255) |  | NO | '' |  |
| [`lat`](#f-lat) | float |  | NO | 0 |  |
| [`lon`](#f-lon) | float |  | NO | 0 |  |
