# GM Workflows

Step-by-step procedures for common admin tasks. Commands are documented in full in the
[GM Commands Reference](GM-Commands.md); config references point into
`mangosd.conf`.

---

## 1. Investigate a Player Report

```
.lookup player <name>          ; find account/character info
.pinfo <name>                  ; player status, position, money
.send message <name> "text"    ; direct reply (broadcast: see `send mass`)
.ticket list → .ticket read    ; handle the ticket
```

Escalation: `.ban character|account|ip <name> <duration> <reason>`
(ban tables: [`account_banned`](realmd/account_banned.md), [`ip_banned`](realmd/ip_banned.md)).

## 2. Spawn & Position Content Live

```
.npc spawn add <entry>           ; spawn NPC at your feet
.gobject add <entry>             ; spawn object at your feet
.npc move <target or guid>       ; reposition NPC to your current target location
.gobject move <guid> <X> <Y> <Z> ; reposition object to set location
.npc spawn del <target or guid>  ; remove NPC (DB row stays until cleanup)
.gobject del <guid>              ; remove object (DB row stays until cleanup)
.go xyz x y z [map]              ; travel yourself
```

For permanent spawns still write SQL; live spawns are runtime state.

## 3. Test a Quest End-to-End

```
.lookup quest <name>  ; find the entry id
.quest status <id>    ; inspect a character's quest state
.quest remove <id>    ; clear state for a clean re-test
.additem <id> [count] ; deliver required items manually
```

Accept the quest from its giver as a normal player, then use the commands above to hand out
objective items or clear state between test runs.

Watch the server log while doing it; quest load errors are described in
[Troubleshooting](Troubleshooting-DB-Errors.md).

## 4. Control Game Events

```
.event list                 ; see events + active state
.event start <entry>        ; force-starts an already-enabled event
.event stop <entry>         ; force-stops an already-enabled event
.event enable <entry>       ; enables event; starts now if active, else waits for next check  
.event disable <entry>      ; disables event; stops it now if active, else just marks disabled  
```

See [Game Events](Game-Events.md).

## 5. Mass Respawn / Reset

```
.respawn              ; respawn creatures/GOs around you
.reload all           ; reload every reloadable store after big data changes
.server restart 30    ; schedule restart with warning
```

## 6. Grant Limited Access

Rather than raising an account's level, bind single commands through RBAC:

```sql
INSERT INTO rbac_command_permissions (command, permission_id) VALUES ('tele', 900);
INSERT INTO rbac_account_permissions (account_id, permission_id, granted)
VALUES (<account>, 900, 1);
```

Details: [Security & RBAC](Security-RBAC.md).

## 7. Debug a Bugged NPC

```
.npc info             ; AI name, faction, flags, loot ids
.guid                 ; only NPC guid and entry
.npc aiinfo           ; EventAI event bindings of your target
.damage <amount>      ; deal damage to the target
```

If EventAI never fires, check `event_inverse_phase_mask`, `event_chance`, and that
`ai_name = 'EventAI'` is set ([AI System](AI-System.md)).

---

## Related Pages

- [Tickets & Player Support](Tickets.md)
