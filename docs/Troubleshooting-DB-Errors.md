# Troubleshooting Startup DB Errors

The world server validates the database at startup and prints `LOG_DBERROR` messages for bad
rows. This page maps the most common messages to causes and fixes.

---

## Loot

| Message | Meaning | Fix |
| :--- | :--- | :--- |
| `Table 'X' entry %d item %d: maxcount value (%u) to large...` | `maxcount > 255` | lower maxcount |
| `...has condition_id %u that does not exist in 'conditions', ignoring` | dangling condition reference | create the [condition](world/conditions.md) or set 0 |
| `mincountOrRef %i < 0 and has condition ... requires a player and is not supported` | reference rows can't use player-dependent conditions | move condition to child rows / drop it |
| `Table '%s' loot id #%u used but it doesn't have records.` | a creature/GO/item references an empty loot table | add rows to that entry |
| `>> Loaded 0 loot definitions. DB table '%s' is empty.` | store empty; benign for optional stores like junk/fail pools | fill if referenced |

Unused-loot warnings (`ReportUnusedIds`) list entries nobody references: delete them or wire
them up.

## Creatures & Templates

| Message | Fix |
| :--- | :--- |
| `Creature (GUID: %u) does not exist but has a record in 'creature_addon'` | remove orphan addon row |
| `Creature (Entry: %u) is using display_id%d (%u), but creature_display_info_addon data is missing` | add addon row for the display or change display id |
| `Creature id %u listed in 'creature_charm_spells' does not exist.` | fix entry |
| `Creature id %u listed in 'petcreateinfo_spell' not exist.` | fix entry |

## Broadcast Text & Sounds

| Message | Fix |
| :--- | :--- |
| `BroadcastText (Id: %u) ... has ChatType %u but this chat type does not exist.` | fix ChatType (say/yell/emote…) |
| `BroadcastText (Id: %u) ... has EmoteId2/3 ...` | invalid emote ids → correct or zero them |
| `BroadcastText (Id: %u) ... SoundId %u but sound does not exist.` | point at [`sound_entries`](world/sound_entries.md) id or clear |
| `BroadcastText (Id: %u) in table 'locales_broadcast_text' does not exist. Skipped!` | locale row without base row - delete it |
| `Entry %i in table '%s' has Emote %u but emote does not exist.` | quest/greeting emote ids |

## Quests, Skills, Fishing

| Message | Fix |
| :--- | :--- |
| `AreaId %u defined in 'skill_fishing_base_level' does not exist` | wrong area id |
| quest referenced by `*_questrelation` doesn't exist | add the quest or remove the relation |

---

## General Workflow

1. **Reproduce**: restart mangosd and capture full log (`grep LOG_DBERROR`).
2. **Fix data, not code**: these errors are almost always data bugs.
3. **Reload where possible**: many stores support `.reload <store>` commands
   ([GM Commands](GM-Commands.md)); otherwise restart.
4. Re-check with a fresh log until clean.

> A clean startup log is the baseline for content work: new errors then stand out immediately.

---

## Related Pages

- [Loot System](Loot-System.md)
- [Conditions Examples](Conditions-Examples.md)
