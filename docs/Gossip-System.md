# Gossip System

How NPC menus ("gossips") work in VMaNGOS: which tables are involved, how menus chain together,
and where conditions and scripts hook in.

---

## Requirements

A creature only shows gossip if:

1. [`creature_template`](world/creature_template.md).npc_flags contains `UNIT_NPC_FLAG_GOSSIP` (`0x1`) - or the interacting
   player has a reason to talk to it (quest giver, vendor, trainer…), and
2. a matching menu exists (see flow below), otherwise the core falls back to default
   vendor/quest/trainer windows.

NPC flag values are defined in `src/game/Objects/UnitDefines.h` (`enum NPCFlags`).

---

## The Menu Flow

```
player interacts with creature
        │
        ▼
creature_template.gossip_menu_id ──► gossip_menu.entry  ──► npc_text (menu greeting text)
        │                                          │
        │                                          ▼
        └───────────────────────────► gossip_menu_option.menu_id
                                                 │  (filtered by condition_id,
                                                 │   npc_option_npcflag)
                                                 ▼
                                   action_menu_id      → open another menu (chain)
                                   action_script_id    → run gossip_scripts
                                   action_poi_id       → show map point of interest
```

1. **[`gossip_menu`](world/gossip_menu.md)** maps a *menu id* (from [`creature_template`](world/creature_template.md).gossip_menu_id)
   to one or more **text ids** from [`npc_text`](world/npc_text.md). Multiple rows = condition-dependent greetings:
   the core picks the text of the fitting row with the highest `condition_id`. Each row can carry its own
   `condition_id` and an optional `script_id` (a [gossip_scripts](world/gossip_scripts.md) run when the text is shown).
2. **[`gossip_menu_option`](world/gossip_menu_option.md)** holds the selectable options for a
   `menu_id`. Each option defines:
   - `option_icon` / text (`option_text` or localized `option_broadcast_text` from
     [`broadcast_text`](world/broadcast_text.md)),
   - `option_id` - what kind of action the client offers (vendor, trainer, taxi…),
   - `npc_option_npcflag` - option only shows when the NPC has this npc flag
     (e.g. vendor options need `0x4`),
   - one of the three actions: open another menu (`action_menu_id`), run a script
     (`action_script_id`), or show a point of interest (`action_poi_id`),
   - an optional input box (`box_text`, `box_money`, `box_coded`) used e.g. for petition names,
   - a `condition_id` gate per option.

---

## Conditions

Both [`gossip_menu`](world/gossip_menu.md) rows and [`gossip_menu_option`](world/gossip_menu_option.md) rows
support [`conditions`](world/conditions.md). Failed conditions hide the row entirely - use this for
faction-specific greetings, phase-dependent options, or quest-state-gated choices
(`CONDITION_QUESTTAKEN`, …).

---

## Scripts

`action_script_id` points into [`gossip_scripts`](world/gossip_scripts.md), which uses the
[generic script command set](DB-Script-Tables.md): make the NPC talk (`TALK`), cast spells,
teleport the player, start quests, terminate the gossip (`TERMINATE_SCRIPT`) and more.

---

## Localization

Option and box texts can be localized via
[`locales_gossip_menu_option`](world/locales_gossip_menu_option.md); menu greetings via the `locales_*`
machinery of [`npc_text`](world/npc_text.md).

---

## Related Pages

- [gossip_menu](world/gossip_menu.md) · [gossip_menu_option](world/gossip_menu_option.md)
- [npc_text](world/npc_text.md) · [broadcast_text](world/broadcast_text.md)
- [gossip_scripts](world/gossip_scripts.md) · [conditions](world/conditions.md)
