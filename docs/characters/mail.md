# mail Table

Mailbox messages: sender, receiver, subject, body, attachments state, expiry.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(11) unsigned | PRI | NO |  | auto_increment |
| [`message_type`](#f-message_type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stationery`](#f-stationery) | tinyint(3) |  | NO | 41 |  |
| [`mail_template_id`](#f-mail_template_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`sender_guid`](#f-sender_guid) | int(11) unsigned |  | NO | 0 |  |
| [`receiver_guid`](#f-receiver_guid) | int(11) unsigned | MUL | NO | 0 |  |
| [`subject`](#f-subject) | longtext |  | YES |  |  |
| [`item_text_id`](#f-item_text_id) | int(11) unsigned |  | NO | 0 |  |
| [`has_items`](#f-has_items) | tinyint(3) unsigned |  | NO | 0 |  |
| [`expire_time`](#f-expire_time) | bigint(40) |  | NO | 0 |  |
| [`deliver_time`](#f-deliver_time) | bigint(40) |  | NO | 0 |  |
| [`money`](#f-money) | int(11) unsigned |  | NO | 0 |  |
| [`cod`](#f-cod) | int(11) unsigned |  | NO | 0 |  |
| [`checked`](#f-checked) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Mail id.
- <a id="f-message_type"></a>**`message_type`** - 0 normal player mail · 2 auction · 3 creature · 4 gameobject · 5 item (drives client icon/query behaviour).
- <a id="f-stationery"></a>**`stationery`** - Stationery template id (41 default, 61 GM, 62 auction…).
- <a id="f-mail_template_id"></a>**`mail_template_id`** - Optional mail template id.
- <a id="f-sender_guid"></a>**`sender_guid`** - Player guid for normal mail; creature/gameobject/item entry or auction
  **house** id for non-player mail types (interpret together with `message_type`).
- <a id="f-receiver_guid"></a>**`receiver_guid`** - Recipient character guid (from [`characters`](characters.md).guid).
- <a id="f-subject"></a>**`subject`** - Subject line.
- <a id="f-item_text_id"></a>**`item_text_id`** - Reference for item-text style bodies.
- <a id="f-has_items"></a>**`has_items`** - 1 when [`mail_items`](mail_items.md) rows are attached.
- <a id="f-expire_time"></a>**`expire_time`** - When the mail is returned/deleted.
- <a id="f-deliver_time"></a>**`deliver_time`** - When it becomes visible to the receiver (AH delay/AH time).
- <a id="f-money"></a>**`money`** - Attached money (copper).
- <a id="f-cod"></a>**`cod`** - Cash-on-demand amount required before taking attached items.
- <a id="f-checked"></a>**`checked`** - Status bitmask: 0x01 read · 0x02 returned · 0x04 copied · 0x08 this mail *is* a COD payment (sent to the original sender) · 0x10 has body.
