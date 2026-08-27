# DB Scripts Examples

Examples for the generic script system ([DB Script Tables](DB-Script-Tables.md)) usable from
[`event_scripts`](world/event_scripts.md), [`gossip_scripts`](world/gossip_scripts.md), [`gameobject_scripts`](world/gameobject_scripts.md), `quest_start/end_scripts`,
[`generic_scripts`](world/generic_scripts.md), … Each example shows the essential columns; `id`/`comments` follow the usual
conventions.

---

## Timed Greeting Chain

```sql
-- 0s: say line 1 → 3s: emote → 5s: say line 2   (delay is in seconds)
INSERT INTO generic_scripts (id, delay, command, datalong, dataint, comments) VALUES
(500100, 0, 0 /*TALK*/, 0 /*say*/,    600001, 'line one'),
(500101, 3, 1 /*EMOTE*/,7 /*EMOTE_ONESHOT_EAT*/, 0,'take a snack'),
(500102, 5, 0 /*TALK*/, 0,            600002, 'line two');
```

All rows share one script id; `delay` sequences them.

---

## Random Response (50%)

```sql
INSERT INTO gossip_scripts (id, delay, command, datalong, dataint, comments) VALUES
(500200, 0, 39 /*START_SCRIPT*/, 500201, 50, '50% chance to run sub-script');

INSERT INTO generic_scripts (id, delay, command, datalong, dataint, comments) VALUES
(500201, 0, 0 /*TALK*/, 1 /*yell*/, 600010, 'rare response');
```

`dataint..4` on `START_SCRIPT` hold per-script chances (0 = skip).

---

## Open a Door, Then Close It

```sql
-- delay/reset_delay are in seconds
INSERT INTO event_scripts (id, delay, command, datalong, datalong2, comments) VALUES
(500300, 0,  11 /*OPEN_DOOR*/,  123456, 300, 'open GO guid 123456 (auto-resets after 5 min)'),
(500301, 35, 12 /*CLOSE_DOOR*/, 123456, 0,   'restore closed state');
```

Door commands take the **gameobject spawn guid** (`datalong`), not the template entry.
Note that `RESPAWN_GAMEOBJECT` (9) refuses doors - use `CLOSE_DOOR` (12) to close them.

---

## Teleport the Interacting Player

`TELEPORT_TO` (6) acts on the **source** and takes its destination from the row's
`x/y/z/o`; `datalong` is the destination map. In gossip scripts the player is the *target*
(the creature owns the gossip), so swap first (`data_flags = 0x01`):

```sql
-- gossip option → action_script_id = 500400
INSERT INTO gossip_scripts (id, delay, command, datalong, data_flags,
                            x, y, z, o, comments)
VALUES (500400, 0, 6 /*TELEPORT_TO*/, 0 /*map: Eastern Kingdoms*/,
        0x01 /*swap: act on the player*/,
        -9464.13, 61.94, 56.34, 2.42, 'send player to Stormwind');
```

Alternatively cast an existing portal/teleport spell on the player - no coordinates needed:

```sql
INSERT INTO gossip_scripts (id, delay, command, datalong, target_type, comments)
VALUES (500401, 0, 15 /*CAST_SPELL*/, 3561 /*Teleport: Stormwind*/, 16 /*friendly*/, '');
```

---

## Summon a Temporary NPC That Fights

```sql
INSERT INTO generic_scripts (id, delay, command, datalong, datalong2,
                             datalong3, datalong4, dataint, dataint2, dataint3, comments)
VALUES (500500, 0, 10 /*TEMP_SUMMON_CREATURE*/,
        12345 /*entry*/, 180000 /*2 min*/, 1 /*unique limit*/,
        30 /*unique distance*/, 8 /*summon flags: unique temp*/,
        500510 /*its script*/, 1 /*attack target: hostile*/, 'summon attacker');
```

---

## Phase Switching on a Creature

```sql
INSERT INTO generic_scripts (id, delay, command, datalong, datalong2,
                             datalong3, datalong4, comments) VALUES
(500600, 0, 44 /*SET_PHASE*/,        2, 0, 0, 0, 'jump to phase 2'),
(500601, 0, 45 /*SET_PHASE_RANDOM*/, 3, 4, 5, 6, 'random phase 3-6');
```

Events gated by phases are described in the [EventAI Examples](EventAI-Examples.md).

---

## Stop Everything Gracefully

```sql
INSERT INTO generic_scripts (id, delay, command, datalong, datalong2, comments)
VALUES (500700, 0, 31 /*TERMINATE_SCRIPT*/, 1230 /*creature entry*/, 40 /*radius*/,
        'stop running scripts on nearby copies of this creature');
```

Useful so two spawns of the same entry don't fight over the same scene.

---

## Related Pages

- [DB Script Tables](DB-Script-Tables.md) - full command/target/flag reference
- [EventAI Examples](EventAI-Examples.md)
