# Tickets & Player Support

The in-game ticket system (`src/game/GMTicketMgr.cpp`) and its database footprint.

---

## Tables

| Table ([characters DB](Characters-Database.md)) | Purpose |
| :--- | :--- |
| [`gm_tickets`](characters/gm_tickets.md) | Open/resolved tickets: author, map/position at submission, text, timestamps. |
| [`gm_surveys`](characters/gm_surveys.md) | Post-resolution satisfaction survey (rating + comment). |
| [`gm_subsurveys`](characters/gm_subsurveys.md) | Additional per-question answers attached to a survey. |

---

## Flow

1. Player opens a ticket from the help request window; position and text are stored.
2. Staff see the queue with the `ticket` commands (level 2 *Ticket Master* and above - [GM Commands](GM-Commands.md)):
   `ticket list`, `ticket assign`, `ticket comment`, `ticket complete`, `ticket close`,
   `ticket delete`, `ticket escalate`, plus `go`-style travel to the reporter.
3. Closing can trigger a survey; answers land in [`gm_surveys`](characters/gm_surveys.md) / [`gm_subsurveys`](characters/gm_subsurveys.md).

Ticket behaviour is configurable via `GM.AcceptTickets`, `GM.Ticket` related settings
(`mangosd.conf`).

---

## Related Pages

- [GM Commands Reference](GM-Commands.md)
- [Security & RBAC](Security-RBAC.md)
