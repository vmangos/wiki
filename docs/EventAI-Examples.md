# EventAI Examples

Practical examples for [`creature_ai_events`](world/creature_ai_events.md) +
[`creature_ai_scripts`](world/creature_ai_scripts.md). Command parameters follow the
[DB Script Tables](DB-Script-Tables.md) reference; event ids come from
[Event Types](world/creature_ai_events.md#event-types).

> Convention: event `id = creature_entry * 100 + n`. Always set
> `event_flags = 0x01` (EFLAG_REPEATABLE) for recurring events.

---

## Cast a Nuke on Cooldown (in combat)

```sql
-- Every 8-14s in combat: cast spell 20793 on the current victim
INSERT INTO creature_ai_events (id, creature_id, event_type, event_chance,
  event_flags, event_param1, event_param2, event_param3, event_param4,
  action1_script, comment)
VALUES (1230001, 1230, 0 /*TIMER_IN_COMBAT*/, 100, 1, 8000, 14000, 8000, 14000,
        1230001, 'Fireball timer');

INSERT INTO creature_ai_scripts (id, command, datalong, target_type, comments)
VALUES (1230001, 15 /*CAST_SPELL*/, 20793, 1 /*hostile*/, 'cast Fireball');
```

---

## Say Something on Aggro

```sql
INSERT INTO creature_ai_events (id, creature_id, event_type, event_chance,
  event_flags, action1_script, comment)
VALUES (1230002, 1230, 4 /*AGGRO*/, 100, 1, 1230002, 'aggro yell');

INSERT INTO creature_ai_scripts (id, command, datalong, dataint, dataint2,
                                 dataint3, dataint4, comments)
VALUES (1230002, 0 /*TALK*/, 1 /*yell*/, 500001, 500002, 500003, 500004,
        'random aggro line');
```

`dataint..dataint4` are broadcast_text ids; the core picks one at random.

---

## Phase System (talk sequence)

```sql
-- phase 0: after 3s out of combat, say line and switch to phase 1
INSERT INTO creature_ai_events (id, creature_id, event_type, event_chance,
  event_flags, event_param1, event_param2, event_param3, event_param4,
  event_inverse_phase_mask, action1_script, comment)
VALUES (1230003, 1230, 1 /*TIMER_OOC*/, 100, 1, 3000, 3000, 3000, 3000,
        2 /*skip ph.1*/, 1230003, 'idle line A');

INSERT INTO creature_ai_scripts (id, command, datalong, dataint, comments)
VALUES (1230003, 44 /*SET_PHASE*/, 1, 0, 'go to phase 1'),
       (1230004, 0 /*TALK*/, 0, 500010, 'say line');
```

Phases gate events through `event_inverse_phase_mask`; use 44/45/46 commands to move between
phases.

---

## Summon Adds at 50% HP

```sql
INSERT INTO creature_ai_events (id, creature_id, event_type, event_chance,
  event_flags, event_param1, event_param2, action1_script, comment)
VALUES (1230004, 1230, 2 /*HP*/, 100, 1, 50, 50, 1230004, 'adds at 50%');

INSERT INTO creature_ai_scripts (id, command, datalong, datalong2,
                                 datalong3, datalong4, dataint, comments)
VALUES (1230004, 10 /*TEMP_SUMMON_CREATURE*/, 12345, 120000,
        2, 20, 16, 'summon 2 adds for 2 min'),
       (1230005, 0 /*TALK*/, 1 /*yell*/, 500020, 0, 0, 0, 'shout');
```

`datalong3 = unique_limit`, `datalong4 = unique_distance`, `dataint = summon flags`
(see command 10 in [DB Script Tables](DB-Script-Tables.md)).

---

## Flee at Low Health

```sql
INSERT INTO creature_ai_events (id, creature_id, event_type, event_chance,
  event_flags, event_param1, event_param2, action1_script, comment)
VALUES (1230005, 1230, 2 /*HP*/, 100, 1, 15, 15, 1230005, 'flee at 15%');

INSERT INTO creature_ai_scripts (id, command, datalong, comments)
VALUES (1230005, 47 /*FLEE*/, 1, 'run away seeking help');
```

---

## React to a Player Emote

```sql
INSERT INTO creature_ai_events (id, creature_id, event_type, event_chance,
  event_flags, event_param1, action1_script, comment)
VALUES (1230006, 1230, 22 /*RECEIVE_EMOTE*/, 100, 1, 17 /*TEXTEMOTE_BOW = /bow*/,
        1230006, 'bow back');

INSERT INTO creature_ai_scripts (id, command, datalong, comments)
VALUES (1230006, 1 /*EMOTE*/, 2 /*EMOTE_ONESHOT_BOW*/, 'return the bow');
```

---

> **Two emote id spaces:** `RECEIVE_EMOTE` matches **text emotes** (`TEXTEMOTE_*`, e.g. `/bow` = 17), while EMOTE actions use `EMOTE_ONESHOT_*` ids (e.g. bow = 2).

## Tips

- One action per row; up to three actions per event (`action1/2/3_script`).
- With `EFLAG_RANDOM_ACTION` (0x02) only one of them runs - great for variety.
- Use `EFLAG_NOT_CASTING` (0x04) on caster mobs so timers don't clip casts.
- Test quickly with `.reload creature_ai_events` style reload commands
  ([GM Commands](GM-Commands.md)).
