# Auction House

How the auction house system works server-side
(`src/game/AuctionHouse/AuctionHouseMgr.cpp`, handlers in `src/game/Handlers/AuctionHouseHandler.cpp`).

---

## Tables

| Table | Purpose |
| :--- | :--- |
| [`auction`](characters/auction.md) ([characters DB](Characters-Database.md)) | One row per live auction: item, seller/buyer, prices, deposit, expiry. |
| [`item_instance`](characters/item_instance.md) | The physical item while it is escrowed by the AH. |
| [`logs_trade`](logs/logs_trade.md) | Money flow entries with types `AuctionBid` / `AuctionBuyout` when trade logging is on. |

By default there are three houses - Alliance, Horde and Neutral (Booty Bay/Gadgetzan/Everlook/Winterspring)
- distinguished by [`auction`](characters/auction.md).`house_id`; house metadata comes from
`AuctionHouse.dbc`. Config can change this grouping: `AllowTwoSide.Interaction.Auction` merges
everything into a single house, and with `Progression.UnlinkedAuctionHouses` (enabled by default)
every DBC entry gets its own house on pre-1.9 timelines.

---

## Economics

Both rates come from `AuctionHouse.dbc` per house and are configurable multipliers:

- **Deposit** (charged at listing, lost if the sale fails):
  `SellPrice x stack x (listing_time / 2h) x depositPercent x Rate.Auction.Deposit`,
  never below `Auction.Deposit.Min`.
- **Cut** (taken from the seller when the sale succeeds):
  `cutPercent x final_bid x Rate.Auction.Cut`.

Related settings in `mangosd.conf`: `Rate.Auction.Time`, `Rate.Auction.Deposit`,
`Rate.Auction.Cut`, `Auction.Deposit.Min`.

---

## Lifecycle

1. **List** - item moves into AH escrow; an [`auction`](characters/auction.md) row is created and the deposit charged.
2. **Bid / Buyout** - bids above the current one refund the previous bidder; a buyout ends the auction immediately.
3. **End**
   - *Sold*: the seller receives a mail with `bid + deposit - cut`; the buyer gets the item by mail (`message_type = 2`, auction).
   - *Expired without bid*: the item is returned to the seller by mail.
4. Expired/sold auctions are removed from the table; everything travels as regular
   [mail](Mail-System.md), so delivery follows the normal mail rules.

---

## Administration

- `.auction` command family lists live auctions per house (`alliance` / `horde` / `goblin`) -
  see [GM Commands](GM-Commands.md).
- To stock markets automatically, use the [Auction House Bot](Auction-House-Bot.md):
  [`auctionhousebot`](world/auctionhousebot.md) rows become normal auctions owned by a hidden seller.

---

## Related Pages

- [auction](characters/auction.md)
- [Auction House Bot](Auction-House-Bot.md)
- [Mail System](Mail-System.md)
