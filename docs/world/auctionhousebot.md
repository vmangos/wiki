# auctionhousebot Table

Defines items that will be sold by the Auction House Bot (simulated economy).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`item`](#f-item) | int(11) unsigned |  | NO |  |  |
| [`stack`](#f-stack) | tinyint(3) unsigned |  | NO | 1 |  |
| [`bid`](#f-bid) | int(11) unsigned |  | NO | 1 |  |
| [`buyout`](#f-buyout) | int(11) unsigned |  | NO | 1 |  |

---

## Field Breakdown

- <a id="f-item"></a>**`item`** - Item ID (from [`item_template`](item_template.md).entry).
- <a id="f-stack"></a>**`stack`** - Stack size per auction listing.
- <a id="f-bid"></a>**`bid`** - Starting bid price (in copper).
- <a id="f-buyout"></a>**`buyout`** - Buyout price (in copper).
