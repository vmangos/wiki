# locales_creature Table

Localized names and subtitles for creatures.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`name_loc1`](#f-name_loc1) | varchar(100) |  | NO | '' |  |
| [`name_loc2`](#f-name_loc2) | varchar(100) |  | NO | '' |  |
| [`name_loc3`](#f-name_loc3) | varchar(100) |  | NO | '' |  |
| [`name_loc4`](#f-name_loc4) | varchar(100) |  | NO | '' |  |
| [`name_loc5`](#f-name_loc5) | varchar(100) |  | NO | '' |  |
| [`name_loc6`](#f-name_loc6) | varchar(100) |  | NO | '' |  |
| [`name_loc7`](#f-name_loc7) | varchar(100) |  | NO | '' |  |
| [`name_loc8`](#f-name_loc8) | varchar(100) |  | NO | '' |  |
| [`subname_loc1`](#f-subname_loc1) | varchar(100) |  | YES |  |  |
| [`subname_loc2`](#f-subname_loc2) | varchar(100) |  | YES |  |  |
| [`subname_loc3`](#f-subname_loc3) | varchar(100) |  | YES |  |  |
| [`subname_loc4`](#f-subname_loc4) | varchar(100) |  | YES |  |  |
| [`subname_loc5`](#f-subname_loc5) | varchar(100) |  | YES |  |  |
| [`subname_loc6`](#f-subname_loc6) | varchar(100) |  | YES |  |  |
| [`subname_loc7`](#f-subname_loc7) | varchar(100) |  | YES |  |  |
| [`subname_loc8`](#f-subname_loc8) | varchar(100) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Creature template entry ([`creature_template`](creature_template.md).entry).
- <a id="f-name_loc1"></a>**`name_loc1`** - Locale 1 text (koKR/frFR/deDE/zhCN/zhTW/esES/esMX/ruRU); empty falls back to the base table.
- <a id="f-name_loc2"></a>**`name_loc2`** - Locale 2 text (koKR/frFR/deDE/zhCN/zhTW/esES/esMX/ruRU); empty falls back to the base table.
- <a id="f-name_loc3"></a>**`name_loc3`** - Locale 3 text (koKR/frFR/deDE/zhCN/zhTW/esES/esMX/ruRU); empty falls back to the base table.
- <a id="f-name_loc4"></a>**`name_loc4`** - Locale 4 text (koKR/frFR/deDE/zhCN/zhTW/esES/esMX/ruRU); empty falls back to the base table.
- <a id="f-name_loc5"></a>**`name_loc5`** - Locale 5 text (koKR/frFR/deDE/zhCN/zhTW/esES/esMX/ruRU); empty falls back to the base table.
- <a id="f-name_loc6"></a>**`name_loc6`** - Locale 6 text (koKR/frFR/deDE/zhCN/zhTW/esES/esMX/ruRU); empty falls back to the base table.
- <a id="f-name_loc7"></a>**`name_loc7`** - Locale 7 text (koKR/frFR/deDE/zhCN/zhTW/esES/esMX/ruRU); empty falls back to the base table.
- <a id="f-name_loc8"></a>**`name_loc8`** - Locale 8 text (koKR/frFR/deDE/zhCN/zhTW/esES/esMX/ruRU); empty falls back to the base table.
- <a id="f-subname_loc1"></a>**`subname_loc1`** - Locale 1 text; empty falls back to the base column.
- <a id="f-subname_loc2"></a>**`subname_loc2`** - Locale 2 text; empty falls back to the base column.
- <a id="f-subname_loc3"></a>**`subname_loc3`** - Locale 3 text; empty falls back to the base column.
- <a id="f-subname_loc4"></a>**`subname_loc4`** - Locale 4 text; empty falls back to the base column.
- <a id="f-subname_loc5"></a>**`subname_loc5`** - Locale 5 text; empty falls back to the base column.
- <a id="f-subname_loc6"></a>**`subname_loc6`** - Locale 6 text; empty falls back to the base column.
- <a id="f-subname_loc7"></a>**`subname_loc7`** - Locale 7 text; empty falls back to the base column.
- <a id="f-subname_loc8"></a>**`subname_loc8`** - Locale 8 text; empty falls back to the base column.
