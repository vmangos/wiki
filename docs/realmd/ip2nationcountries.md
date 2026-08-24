# ip2nationcountries Table

Country metadata for [`ip2nation`](ip2nation.md).

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

---

## Field Breakdown

- <a id="f-code"></a>**`code`** - Primary Key. Country code key.
- <a id="f-iso_code_2"></a>**`iso_code_2`** - ISO country codes.
- <a id="f-iso_code_3"></a>**`iso_code_3`** - ISO country codes.
- <a id="f-iso_country"></a>**`iso_country`** - Full ISO country name.
- <a id="f-country"></a>**`country`** - Display name.
- <a id="f-lat"></a>**`lat`** - Approximate country centroid coordinates.
- <a id="f-lon"></a>**`lon`** - Approximate country centroid coordinates.
