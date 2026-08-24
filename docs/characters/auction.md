# auction Table

Active auctions on the world auction houses. Rows are removed when an auction expires or is cancelled.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(11) unsigned | PRI | NO | 0 |  |
| [`house_id`](#f-house_id) | int(11) unsigned |  | NO | 0 |  |
| [`item_guid`](#f-item_guid) | int(11) unsigned | UNI | NO | 0 |  |
| [`item_id`](#f-item_id) | int(11) unsigned |  | NO | 0 |  |
| [`seller_guid`](#f-seller_guid) | int(11) unsigned |  | NO | 0 |  |
| [`buyout_price`](#f-buyout_price) | int(11) |  | NO | 0 |  |
| [`expire_time`](#f-expire_time) | bigint(40) |  | NO | 0 |  |
| [`buyer_guid`](#f-buyer_guid) | int(11) unsigned |  | NO | 0 |  |
| [`last_bid`](#f-last_bid) | int(11) |  | NO | 0 |  |
| [`start_bid`](#f-start_bid) | int(11) |  | NO | 0 |  |
| [`deposit`](#f-deposit) | int(11) |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Auction identifier.
- <a id="f-house_id"></a>**`house_id`** - Auction house (faction/neutrality) the auction runs on.
- <a id="f-item_guid"></a>**`item_guid`** - The physical item (from [`item_instance`](item_instance.md).guid).
- <a id="f-item_id"></a>**`item_id`** - Template entry of the auctioned item.
- <a id="f-seller_guid"></a>**`seller_guid`** - Seller character guid (from [`characters`](characters.md).guid).
- <a id="f-buyout_price"></a>**`buyout_price`** - Instant-buy price (copper).
- <a id="f-expire_time"></a>**`expire_time`** - Unix timestamp when the auction ends.
- <a id="f-buyer_guid"></a>**`buyer_guid`** - Buyer character guid (from [`characters`](characters.md).guid); empty until the first bid.
- <a id="f-last_bid"></a>**`last_bid`** - Current highest bid (copper).
- <a id="f-start_bid"></a>**`start_bid`** - Original listing bid (copper).
- <a id="f-deposit"></a>**`deposit`** - Deposit charged at listing; lost if the sale fails.
