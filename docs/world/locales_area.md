# locales_area Table

Localized area/zone names. Read by the core (`ObjectMgr::LoadAreaLocales`) so it can hand clients the name matching their login locale.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`Entry`](#f-Entry) | mediumint(8) | PRI | NO | 0 |  |
| [`NameLoc1`](#f-NameLoc1) | varchar(100) |  | NO | '' |  |
| [`NameLoc2`](#f-NameLoc2) | varchar(100) |  | NO | '' |  |
| [`NameLoc3`](#f-NameLoc3) | varchar(100) |  | NO | '' |  |
| [`NameLoc4`](#f-NameLoc4) | varchar(100) |  | NO | '' |  |
| [`NameLoc5`](#f-NameLoc5) | varchar(100) |  | NO | '' |  |
| [`NameLoc6`](#f-NameLoc6) | varchar(100) |  | NO | '' |  |
| [`NameLoc7`](#f-NameLoc7) | varchar(100) |  | NO | '' |  |
| [`NameLoc8`](#f-NameLoc8) | varchar(100) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-Entry"></a>**`Entry`** - Primary Key. Area ID (from `AreaTable.dbc`).
- <a id="f-NameLoc1"></a>**`NameLoc1`** - Korean (`koKR`) name.
- <a id="f-NameLoc2"></a>**`NameLoc2`** - French (`frFR`) name.
- <a id="f-NameLoc3"></a>**`NameLoc3`** - German (`deDE`) name.
- <a id="f-NameLoc4"></a>**`NameLoc4`** - Chinese simplified (`zhCN`) name.
- <a id="f-NameLoc5"></a>**`NameLoc5`** - Chinese traditional (`zhTW`) name.
- <a id="f-NameLoc6"></a>**`NameLoc6`** - Spanish (`esES`) name.
- <a id="f-NameLoc7"></a>**`NameLoc7`** - Spanish Latin American (`esMX`) name (no official vanilla client existed for this locale; slot kept by the core's `LocaleConstant` enum).
- <a id="f-NameLoc8"></a>**`NameLoc8`** - Russian (`ruRU`) name (no official vanilla client existed; used today via fan-made clients).
