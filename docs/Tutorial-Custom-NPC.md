# Tutorial: Adding a Custom NPC

End-to-end example: a talkative guard NPC for Stormwind that greets players, responds when
greeted with /bow, and drops a custom item. Everything is database-only.

---

## 1. Template

```sql
INSERT INTO creature_template
(entry, name, subname, display_id1, level_min, level_max, faction, npc_flags,
 gossip_menu_id, ai_name, movement_type, rank, script_name)
VALUES
(90001, 'Stormwind Town Crier', 'Herald of Goldshire', 4975, 60, 60, 12,
 1, 90001, 'EventAI', 0, 0, '');
```

- `faction = 12` - stormwind-friendly.
- `npc_flags = 1` - gossip enabled.
- `ai_name = 'EventAI'` - table-driven AI (see [AI System](AI-System.md)).

Check the exact column names in [`creature_template`](world/creature_template.md) - the table
carries many more (stats, resistances…), defaults are fine for a friendly NPC.

## 2. Spawn

```sql
INSERT INTO creature (guid, id, map, position_x, position_y, position_z, orientation,
                      spawntimesecsmin, spawntimesecsmax, movement_type)
VALUES (5000000, 90001, 0, -9464.13, 61.94, 56.34, 2.42, 300, 300, 0);
```

Pick an unused `guid`; `map 0` = Eastern Kingdoms. Movement types are explained in the
[Movement System](Movement-System.md).

## 3. Greeting Text

```sql
-- menu id 90001 shows text 90001
INSERT INTO broadcast_text (entry, male_text) VALUES (90001, 'Hail, traveler! Need directions?');
INSERT INTO npc_text (ID, BroadcastTextID0) VALUES (90001, 90001);
INSERT INTO gossip_menu (entry, text_id) VALUES (90001, 90001);
```

Flow details: [Gossip System](Gossip-System.md).

## 4. Bow Response (EventAI)

```sql
-- event: on receive emote → action scripts 900010 and 900011
INSERT INTO creature_ai_events (id, creature_id, event_type, event_chance, event_param1,
                                action1_script, action2_script, comment)
VALUES (9000101, 90001, 22 /*RECEIVE_EMOTE*/, 100, 17 /*TEXTEMOTE_BOW = /bow*/,
        900010, 900011, 'Crier bows back');

INSERT INTO creature_ai_scripts (id, command, datalong, dataint, comments)
VALUES (900010, 0 /*TALK*/, 1 /*CHAT_TYPE_YELL*/, 90002, 'Crier yells a greeting'),
       (900011, 1 /*EMOTE*/, 2 /*EMOTE_ONESHOT_BOW*/, 1, 'bow emote');
```

The TALK command reads texts from [`broadcast_text`](world/broadcast_text.md) - add entry
`90002` there. Full command reference: [DB Script Tables](DB-Script-Tables.md).

## 5. Optional Loot

```sql
UPDATE creature_template SET loot_id = 90001 WHERE entry = 90001;
INSERT INTO creature_loot_template (entry, item, ChanceOrQuestChance)
VALUES (90001, 900001, 25);   -- 25% drop of item 900001
```

Loot mechanics: [Loot System](Loot-System.md).

## 6. Localization (optional)

Add rows to [`locales_creature`](world/locales_creature.md) and
[`locales_broadcast_text`](world/locales_broadcast_text.md) with `_locN` columns filled
(see [Localization](Localization.md)).

## 7. Verify

```
.npc info 90001          -- template loaded?
.go creature 5000000     -- teleport to spawn
.reload creature_template -- after template edits
```

Watch the server log for `LOG_DBERROR` lines mentioning your entries.
