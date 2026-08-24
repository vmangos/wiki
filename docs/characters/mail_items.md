# mail_items Table

Items attached to mails (moved out of [`mail`](mail.md) for performance).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`mail_id`](#f-mail_id) | int(11) unsigned | PRI | NO | 0 |  |
| [`item_guid`](#f-item_guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`item_id`](#f-item_id) | int(11) unsigned |  | NO | 0 |  |
| [`receiver_guid`](#f-receiver_guid) | int(11) unsigned | MUL | NO | 0 |  |

---

## Field Breakdown

- <a id="f-mail_id"></a>**`mail_id`** - Primary Key. Parent mail.
- <a id="f-item_guid"></a>**`item_guid`** - Primary Key. Attached physical item.
- <a id="f-item_id"></a>**`item_id`** - Attached physical item.
- <a id="f-receiver_guid"></a>**`receiver_guid`** - Recipient snapshot for integrity checks.
