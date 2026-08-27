# Auction House Bot

The Auction House Bot (AHBot, `src/game/AuctionHouse/AuctionHouseBotMgr.cpp`) lets the server
place items on the auction houses: keep markets stocked on low-population realms or seed specific
items for testing.

---

## Enabling

1. Set `AHBot.Enable = 1` in `mangosd.conf`.
2. Configure which faction houses it sells on via `AHBot.ah.fid`.
3. Control volume with `AHBot.itemcount`.

---

## Item Supply

Two sources feed the bot:

- **Table**: [`auctionhousebot`](world/auctionhousebot.md)

  | Column | Meaning |
  | :--- | :--- |
  | `item` | [`item_template`](world/item_template.md).entry to sell |
  | `stack` | Stack size to auction |
  | `bid` | Starting bid price (copper) |
  | `buyout` | Buyout price (copper) |

- **Command**: `.ahbot update <item> …` adds items at runtime; `.ahbot reload` re-reads
  table and config (Administrator level - see [GM Commands](GM-Commands.md)).

---

## How It Works

- The manager creates normal [`auction`](characters/auction.md) rows owned by a hidden seller,
  so players interact with them exactly like player auctions.
- Prices are fixed by configuration/table rather than market simulation in this implementation.
- Expired AHBot auctions follow normal expiry rules (return/delete).

---

## Related Pages

- [auctionhousebot](world/auctionhousebot.md)
- [auction](characters/auction.md)
- `mangosd.conf`
