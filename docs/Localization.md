# Localization

VMaNGOS supports 8 client locales. Base tables hold the English (locale 0) text; the
`locales_*` tables override it per locale for every localisable string type.

---

## Locale Indices

`_locN` suffixes map to the game's locales:

| Column | Locale | Language |
| :---: | :--- | :--- |
| `_loc1` | koKR | Korean |
| `_loc2` | frFR | French |
| `_loc3` | deDE | German |
| `_loc4` | zhCN | Chinese (Simplified) |
| `_loc5` | zhTW | Chinese (Taiwan) |
| `_loc6` | esES | Spanish |
| `_loc7` | esMX | Spanish (Mexico) |
| `_loc8` | ruRU | Russian |

Empty columns fall back to locale 0 (the base table text).

---

## Localisable Tables

| Table | Localises |
| :--- | :--- |
| [`locales_creature`](world/locales_creature.md) | creature names/subnames |
| [`locales_gameobject`](world/locales_gameobject.md) | object names |
| [`locales_item`](world/locales_item.md) | item names/descriptions |
| [`locales_quest`](world/locales_quest.md) | quest title, details, objectives, reward texts |
| [`npc_text`](world/npc_text.md) | gossip greetings, resolved through broadcast text ids (no dedicated table) |
| [`locales_gossip_menu_option`](world/locales_gossip_menu_option.md) | gossip option/box texts |
| [`locales_broadcast_text`](world/locales_broadcast_text.md) | script/broadcast say-texts |
| [`locales_page_text`](world/locales_page_text.md) | book pages |
| [`locales_spell`](world/locales_spell.md) | spell names/tooltips served to scripts |
| [`locales_faction`](world/locales_faction.md) | faction titles/descriptions |
| [`locales_area`](world/locales_area.md) | zone/area names |
| [`locales_areatrigger`](world/locales_areatrigger.md) | areatrigger messages |
| [`locales_points_of_interest`](world/locales_points_of_interest.md) | POI icon labels |
| [`locales_taxi_node`](world/locales_taxi_node.md) | flight node names |

---

## How It Works

1. Client sends its locale at login; the server selects the matching `_locN` column.
2. If that column is empty, the base (English) value from the main table is sent.
3. Texts referenced by **broadcast_text** ids in scripts (`TALK`, quest mails…) resolve through
   [`locales_broadcast_text`](world/locales_broadcast_text.md) automatically - DB-scripted NPCs speak localized lines without
   extra work.

> Keep base-table texts authoritative: only fill `_locN` columns you actually translate,
> otherwise leave them empty instead of duplicating English.

---

## Related Pages

- [Gossip System](Gossip-System.md)
- [DB Script Tables](DB-Script-Tables.md) - TALK command and broadcast_text usage
