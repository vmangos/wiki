# sound_entries Table

Maps sound IDs to sound file names.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | smallint(6) | PRI | NO | 0 |  |
| [`name`](#f-name) | varchar(128) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Sound ID.
- <a id="f-name"></a>**`name`** - Sound file name.

*Referenced by: [`broadcast_text`](broadcast_text.md).sound_id and [`script_texts`](script_texts.md).sound.*
