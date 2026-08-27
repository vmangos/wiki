# LFG & Meeting Stones

Vanilla-era dungeon matchmaking via meeting stones, implemented in
`src/game/LFG/` (`LFGMgr`, `LFGQueue`). Unlike later expansions this is a **role-balanced
queue around meeting stones**, not an automatic teleport system.

---

## Configuration

From `mangosd.conf` ("Meeting Stone LFG" category):

| Setting | Default | Meaning |
| :--- | :---: | :--- |
| `LFG.Matchmaking` | 0 | use talent specs to determine queued players' roles (class-based priorities otherwise) |
| `LFG.MatchmakingTimer` | 600 | seconds in queue before a player stops using talent matchmaking |

Related accuracy toggle: `CONFIG_BOOL_ACCURATE_LFG` gates behaviour differences per
[progression timeline](Progression-System.md).

---

## Roles

Roles are assigned by the core when a player queues (`enum LfgRoles`), based on class
(or talents with `LFG.Matchmaking`):

| Role | Value |
| :--- | :---: |
| None | 0x00 |
| Tank | 0x01 |
| Healer | 0x02 |
| Damage | 0x04 |

Role priority for match selection uses `LFG_PRIORITY_NONE/LOW/NORMAL/HIGH`
(`enum LfgRolePriority`).

---

## Queue Status Codes

Sent to clients as meeting-stone status (`MeetingstoneQueueStatus`):

| Value | Meaning |
| :---: | :--- |
| 0 | left queue |
| 1 | joined queue |
| 2 | party member left LFG |
| 3 | party member removed / party removed |
| 4 | looking for new party, still in queue |
| 5 | none/idle |

Failure reasons use `MeetingstoneFailedStatus`; group dissolution distinguishes
`PLAYER_CLIENT_LEAVE/SYSTEM_LEAVE` and `GROUP_CLIENT_LEAVE/SYSTEM_LEAVE`.

---

## How Matching Works (simplified)

1. A full group standing at a meeting stone queues the stone's dungeon.
2. Solo players near the stone (or queued via UI) enter the pool with their role mask.
3. The matcher periodically proposes groups balancing roles (tank/healer/dps) and level
   bracket; proposals appear as invites rather than teleports.

---

## Related Pages

- [Groups & Parties](Groups.md)
- [Instances & Resets](Instances.md)
