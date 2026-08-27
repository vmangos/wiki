# gm_tickets Table

Open and archived GM tickets written by players.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`ticket_id`](#f-ticket_id) | int(10) unsigned | PRI | NO |  | auto_increment |
| [`guid`](#f-guid) | int(10) unsigned |  | NO | 0 |  |
| [`name`](#f-name) | varchar(12) |  | NO |  |  |
| [`message`](#f-message) | text |  | NO |  |  |
| [`create_time`](#f-create_time) | bigint(20) unsigned |  | NO | 0 |  |
| [`map`](#f-map) | smallint(5) unsigned |  | NO | 0 |  |
| [`position_x`](#f-position_x) | float |  | NO | 0 |  |
| [`position_y`](#f-position_y) | float |  | NO | 0 |  |
| [`position_z`](#f-position_z) | float |  | NO | 0 |  |
| [`last_modified_time`](#f-last_modified_time) | bigint(20) unsigned |  | NO | 0 |  |
| [`closed_by`](#f-closed_by) | int(10) |  | NO | 0 |  |
| [`assigned_to`](#f-assigned_to) | int(10) unsigned |  | NO | 0 |  |
| [`comment`](#f-comment) | text |  | NO |  |  |
| [`response`](#f-response) | text |  | NO |  |  |
| [`completed`](#f-completed) | tinyint(3) unsigned |  | NO | 0 |  |
| [`escalated`](#f-escalated) | tinyint(3) unsigned |  | NO | 0 |  |
| [`viewed`](#f-viewed) | tinyint(3) unsigned |  | NO | 0 |  |
| [`have_ticket`](#f-have_ticket) | tinyint(3) unsigned |  | NO | 0 |  |
| [`ticket_type`](#f-ticket_type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`security_needed`](#f-security_needed) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-ticket_id"></a>**`ticket_id`** - Primary Key. Unique ticket number.
- <a id="f-guid"></a>**`guid`** - Authoring character guid + name snapshot ([`characters`](characters.md).guid).
- <a id="f-name"></a>**`name`** - Authoring character guid + name snapshot.
- <a id="f-message"></a>**`message`** - Ticket text written by the player.
- <a id="f-create_time"></a>**`create_time`** - Timestamps.
- <a id="f-map"></a>**`map`** - Player location at submission (for `.go` to reporter).
- <a id="f-position_x"></a>**`position_x`** - Player location at submission (for `.go` to reporter).
- <a id="f-position_y"></a>**`position_y`** - Reporter position at ticket creation.
- <a id="f-position_z"></a>**`position_z`** - Reporter position at ticket creation (Z).
- <a id="f-last_modified_time"></a>**`last_modified_time`** - Timestamps.
- <a id="f-closed_by"></a>**`closed_by`** - Who closed it (`0` = open; `-1` = console; character guid of the player who abandoned it or the GM who closed it).
- <a id="f-assigned_to"></a>**`assigned_to`** - Staff character guid handling the ticket (0 = unassigned).
- <a id="f-comment"></a>**`comment`** - Internal staff comment.
- <a id="f-response"></a>**`response`** - Answer sent back to the player.
- <a id="f-completed"></a>**`completed`** - Completion flag.
- <a id="f-escalated"></a>**`escalated`** - Ticket status (`GMTicketEscalationStatus`): 0 unassigned, 1 assigned, 2 in escalation queue, 3 escalated+assigned.
- <a id="f-viewed"></a>**`viewed`** - Whether staff opened it already.
- <a id="f-have_ticket"></a>**`have_ticket`** - Player requested further GM interaction on a ticket that was already responded to ("need more help").
- <a id="f-ticket_type"></a>**`ticket_type`** - Ticket category (`TicketType`): 1 stuck, 2 harassment, 3 guild, 4 item, 5 environmental, 6 non-quest creep, 7 quest/quest NPC, 8 technical, 9 account/billing, 10 character.
- <a id="f-security_needed"></a>**`security_needed`** - Minimum security level required to handle this ticket.
