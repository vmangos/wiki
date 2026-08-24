# creature_battleground Table

Links creature spawns to battleground events, allowing specific NPCs to react to battleground state changes.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO |  |  |
| [`event1`](#f-event1) | tinyint(3) unsigned | PRI | NO |  |  |
| [`event2`](#f-event2) | tinyint(3) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** (int(10) unsigned) - Primary Key. References [`creature`](creature.md).guid.
- <a id="f-event1"></a>**`event1`** (tinyint(3) unsigned) - Primary Key. First battleground event ID. (see [`battleground_events`](battleground_events.md).event1)
- <a id="f-event2"></a>**`event2`** (tinyint(3) unsigned) - Secondary event ID for more granular control.
