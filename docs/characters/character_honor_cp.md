# character_honor_cp Table

Honour contribution points accumulated during the current honour day (used by the weekly honour calculation).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | MUL | NO | 0 |  |
| [`victim_type`](#f-victim_type) | tinyint(3) unsigned |  | NO | 4 |  |
| [`victim_id`](#f-victim_id) | int(11) unsigned |  | NO | 0 |  |
| [`cp`](#f-cp) | float |  | NO | 0 |  |
| [`date`](#f-date) | int(11) unsigned |  | NO | 0 |  |
| [`type`](#f-type) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Character earning the honour ([`characters`](characters.md).guid); indexed, not unique - one row per honour event.
- <a id="f-victim_type"></a>**`victim_type`** - Object type id of the honour source unit (0 when the source is the character itself).
- <a id="f-victim_id"></a>**`victim_id`** - Victim identifier (guid low or creature entry).
- <a id="f-cp"></a>**`cp`** - Contribution points awarded for this entry.
- <a id="f-date"></a>**`date`** - Honour day (date key) this row counts towards.
- <a id="f-type"></a>**`type`** - Honor type (`HonorType`): 1 honourable, 2 dishonourable, 3 bonus, 4 quest, 5 other.
