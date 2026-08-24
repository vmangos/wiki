# autobroadcast Table

Defines messages sent periodically to all online players.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`string_id`](#f-string_id) | int(11) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-string_id"></a>**`string_id`** - Text ID from [`mangos_string`](mangos_string.md).entry. The actual message content is stored there.
