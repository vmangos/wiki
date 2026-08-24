# character_gifts Table

Items wrapped as gifts waiting to be opened (gift target stored until unwrapped).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(20) unsigned | MUL | NO | 0 |  |
| [`item_guid`](#f-item_guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`item_id`](#f-item_id) | int(20) unsigned |  | NO | 0 |  |
| [`flags`](#f-flags) | int(20) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Character who received the wrapped gift ([`characters`](characters.md).guid).
- <a id="f-item_guid"></a>**`item_guid`** - Primary Key. [`item_instance`](item_instance.md).guid of the gift package.
- <a id="f-item_id"></a>**`item_id`** - Template entry of the package item.
- <a id="f-flags"></a>**`flags`** - Internal gift state flags.
