# Conditions Examples

Examples for the [conditions](world/conditions.md) system. Every condition source type in
`enum ConditionSource` (`src/game/Conditions.h`) is listed with a practical example.

---

## Source Types

| Source | Checked for | Typical table |
| :--- | :--- | :--- |
| `CONDITION_FROM_LOOT` (0) | loot rolls | any `*_loot_template.condition_id` |
| `CONDITION_FROM_REFERING_LOOT` (1) | reference loot expansion | [`reference_loot_template`](world/reference_loot_template.md) |
| `CONDITION_FROM_GOSSIP_MENU` (2) | menu text rows | [`gossip_menu`](world/gossip_menu.md) |
| `CONDITION_FROM_GOSSIP_OPTION` (3) | menu options | [`gossip_menu_option`](world/gossip_menu_option.md) |
| `CONDITION_FROM_EVENTAI` (4) | EventAI events | [`creature_ai_events`](world/creature_ai_events.md) |
| `CONDITION_FROM_HARDCODED` (5) | internal checks | - |
| `CONDITION_FROM_VENDOR` (6) | vendor listings | [`npc_vendor`](world/npc_vendor.md) |
| `CONDITION_FROM_SPELL_AREA` (7) | aura application by area | [`spell_area`](world/spell_area.md) |
| `CONDITION_FROM_MAP_EVENT` (8) | scripted map events | commands 61-69 |
| `CONDITION_FROM_DBSCRIPTS` (9) | generic script steps | `condition_id` column |
| `CONDITION_FROM_AREATRIGGER` (10) | areatrigger teleports | [`areatrigger_teleport`](world/areatrigger_teleport.md) |
| `CONDITION_FROM_QUEST` (11) | quest availability | [`quest_template`](world/quest_template.md) |

---

## Example: Faction-Only Greeting

Only Horde players see this greeting text:

```sql
INSERT INTO conditions (condition_entry, type, value1) VALUES
(900001, 6 /*TEAM*/, 67 /*Horde*/);

UPDATE gossip_menu SET condition_id = 900001 WHERE entry = 5000;
```

## Example: Vendor Item Only With Reputation

```sql
INSERT INTO conditions (condition_entry, type, value1, value2) VALUES
(900002, 5 /*REP_RANK_MIN*/, 60 /*faction*/, 7 /*exalted*/);

UPDATE npc_vendor SET condition_id = 900002 WHERE entry = 12345 AND item = 19019;
```

## Example: Loot Requires an Aura

Classic Argent Dawn pattern - only drop while the commission aura is active:

```sql
INSERT INTO conditions (condition_entry, type, value1) VALUES
(900003, 1 /*AURA*/, 17670 /*Argent Dawn Commission*/);

UPDATE creature_loot_template SET condition_id = 900003
WHERE entry = 10816 AND item = 12843;
```

(The core also has a dedicated shortcut for exactly this: `CONDITION_AD_COMMISSION_AURA` (10).)

## Example: Quest-Gated Gossip Option

```sql
-- show option only while quest 90002 is taken but not done
INSERT INTO conditions (condition_entry, type, value1, value2) VALUES
(900004, 9 /*QUESTTAKEN*/, 90002, 1 /*incomplete*/);

UPDATE gossip_menu_option SET condition_id = 900004
WHERE menu_id = 5000 AND id = 2;
```

Combine states by making an `AND` condition:

```sql
INSERT INTO conditions (condition_entry, type, value1) VALUES
(900005, -1 /*AND*/, 900004);
```

## Example: Area-Restricted Aura via spell_area

`spell_area` has no `condition_id` column - its requirements are expressed through its own
columns (`quest_start`, `aura_spell`, `racemask`, `gender`, …). Apply an aura only while the
player is inside a zone:

```sql
INSERT INTO spell_area (spell, area, autocast) VALUES
(40075, 1 /*Dun Morogh*/, 1);
```

The aura is removed automatically when the player leaves the area. To gate other sources by
level instead, use a LEVEL condition with an operator:

```sql
INSERT INTO conditions (condition_entry, type, value1, value2) VALUES
(900006, 15 /*LEVEL*/, 20, 1 /*equal or higher than*/);
```

## Example: Patch-Gated Teleport

```sql
-- areatrigger only usable while content patch <= 3 (pre-1.5 timeline)
INSERT INTO conditions (condition_entry, type, value1, value2) VALUES
(900007, 24 /*WOW_PATCH*/, 3, 2 /*<=*/);
```

Then reference it from [`areatrigger_teleport`](world/areatrigger_teleport.md)'s
`required_condition` column.

---

## Combining & Reversing

- `-1 AND`, `-2 OR` combine up to four child conditions.
- Prefer `flags = 0x01` (**reverse result**) over deprecated `CONDITION_NOT`.
- `flags = 0x02` swaps source/target before evaluation.

---

## Related Pages

- [conditions](world/conditions.md)
- [Gossip System](Gossip-System.md)
