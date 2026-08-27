# character_inventory Table

Every item a character carries: bag/slot mapping from [`item_instance`](item_instance.md).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | MUL | NO | 0 |  |
| [`bag`](#f-bag) | int(11) unsigned |  | NO | 0 |  |
| [`slot`](#f-slot) | tinyint(3) unsigned |  | NO | 0 |  |
| [`item_guid`](#f-item_guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`item_id`](#f-item_id) | int(11) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Character owning the item ([`characters`](characters.md).guid).
- <a id="f-bag"></a>**`bag`** - Container item guid; `0` whenever the item sits directly on the player
  (equipment 0-18, bags 19-22, backpack 23-38, bank main slots 39-62, bank bag slots 63-68, keyring 81+).
- <a id="f-slot"></a>**`slot`** - Slot inside the container or equipment slot on the paperdoll.
- <a id="f-item_guid"></a>**`item_guid`** - Primary Key. Item Global Unique Identifier
- <a id="f-item_id"></a>**`item_id`** - Item Identifier
