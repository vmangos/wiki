# logs_trade Table

Money flow log entries above the configured threshold (loot, quest rewards, trades, mail, GM changes).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`time`](#f-time) | timestamp |  | NO | current_timestamp() |  |
| [`type`](#f-type) | enum('AuctionBid','AuctionBuyout','BuyItem','SellItem','GM','Mail','QuestMaxLevel','Quest','Loot','Trade','') |  | NO | '' |  |
| [`sender`](#f-sender) | int(11) unsigned | MUL | NO | 0 |  |
| [`senderType`](#f-senderType) | int(11) unsigned |  | NO | 0 |  |
| [`senderEntry`](#f-senderEntry) | int(11) unsigned |  | NO | 0 |  |
| [`receiver`](#f-receiver) | int(11) unsigned | MUL | NO | 0 |  |
| [`amount`](#f-amount) | int(11) |  | NO | 0 |  |
| [`data`](#f-data) | int(11) |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-time"></a>**`time`** - Trade timestamp.
- <a id="f-type"></a>**`type`** - Trade event kind (item/money flow direction codes).
- <a id="f-sender"></a>**`sender`** - Sending object identity (player guid or creature/item entry depending on type).
- <a id="f-senderType"></a>**`senderType`** - Sending object identity (player guid or creature/item entry depending on type).
- <a id="f-senderEntry"></a>**`senderEntry`** - Sending object identity (player guid or creature/item entry depending on type).
- <a id="f-receiver"></a>**`receiver`** - Receiving player/object.
- <a id="f-amount"></a>**`amount`** - Money amount traded.
- <a id="f-data"></a>**`data`** - Item id/count payload blob for item lines.
