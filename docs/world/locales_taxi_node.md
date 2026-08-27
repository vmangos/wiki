# locales_taxi_node Table

Localized taxi node names.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | int(10) unsigned | PRI | NO |  |  |
| [`name_loc1`](#f-name_loc1) | varchar(256) |  | NO | '' |  |
| [`name_loc2`](#f-name_loc2) | varchar(256) |  | NO | '' |  |
| [`name_loc3`](#f-name_loc3) | varchar(256) |  | NO | '' |  |
| [`name_loc4`](#f-name_loc4) | varchar(256) |  | NO | '' |  |
| [`name_loc5`](#f-name_loc5) | varchar(256) |  | NO | '' |  |
| [`name_loc6`](#f-name_loc6) | varchar(256) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Taxi node id. (see [`taxi_nodes`](taxi_nodes.md).id)
- <a id="f-name_loc1"></a>**`name_loc1`** - Locale 1 text (koKR/frFR/deDE/zhCN/zhTW/esES); empty falls back to the base table.
- <a id="f-name_loc2"></a>**`name_loc2`** - Locale 2 text (koKR/frFR/deDE/zhCN/zhTW/esES); empty falls back to the base table.
- <a id="f-name_loc3"></a>**`name_loc3`** - Locale 3 text (koKR/frFR/deDE/zhCN/zhTW/esES); empty falls back to the base table.
- <a id="f-name_loc4"></a>**`name_loc4`** - Locale 4 text (koKR/frFR/deDE/zhCN/zhTW/esES); empty falls back to the base table.
- <a id="f-name_loc5"></a>**`name_loc5`** - Locale 5 text (koKR/frFR/deDE/zhCN/zhTW/esES); empty falls back to the base table.
- <a id="f-name_loc6"></a>**`name_loc6`** - Locale 6 text (koKR/frFR/deDE/zhCN/zhTW/esES); empty falls back to the base table.
