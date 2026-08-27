# logs_transactions Table

Money/mail transaction audit trail.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`time`](#f-time) | timestamp |  | NO | current_timestamp() |  |
| [`type`](#f-type) | enum('Bid','Buyout','PlaceAuction','Trade','Mail','MailCOD') |  | YES |  |  |
| [`guid1`](#f-guid1) | int(11) unsigned | MUL | NO | 0 |  |
| [`money1`](#f-money1) | int(11) unsigned |  | NO | 0 |  |
| [`spell1`](#f-spell1) | int(11) unsigned |  | NO | 0 |  |
| [`items1`](#f-items1) | varchar(255) |  | NO | '' |  |
| [`guid2`](#f-guid2) | int(11) unsigned | MUL | NO | 0 |  |
| [`money2`](#f-money2) | int(11) unsigned |  | NO | 0 |  |
| [`spell2`](#f-spell2) | int(11) unsigned |  | NO | 0 |  |
| [`items2`](#f-items2) | varchar(255) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-time"></a>**`time`** - Transaction timestamp.
- <a id="f-type"></a>**`type`** - Transaction category.
- <a id="f-guid1"></a>**`guid1`** - First side: character, money delta, spell, items payload.
- <a id="f-money1"></a>**`money1`** - First side: character, money delta, spell, items payload.
- <a id="f-spell1"></a>**`spell1`** - First side: character, money delta, spell, items payload.
- <a id="f-items1"></a>**`items1`** - First side: character, money delta, spell, items payload.
- <a id="f-guid2"></a>**`guid2`** - Second side mirrored fields.
- <a id="f-money2"></a>**`money2`** - Second side mirrored fields.
- <a id="f-spell2"></a>**`spell2`** - Second side mirrored fields.
- <a id="f-items2"></a>**`items2`** - Second side mirrored fields.
