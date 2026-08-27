# scripted_event_id Table

Maps scripted event IDs to script names.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | mediumint(8) | PRI | NO |  |  |
| [`script_name`](#f-script_name) | char(64) |  | NO |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Event ID.
- <a id="f-script_name"></a>**`script_name`** - C++ script name.
