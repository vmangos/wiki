# game_event_mail Table

Sends mail to players during events based on race, quest, and faction.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`event`](#f-event) | smallint(6) | PRI | NO | 0 |  |
| [`raceMask`](#f-raceMask) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`quest`](#f-quest) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`mailTemplateId`](#f-mailTemplateId) | mediumint(8) unsigned |  | NO | 0 |  |
| [`senderEntry`](#f-senderEntry) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-event"></a>**`event`** - Primary Key. Event ID. (see [`game_event`](game_event.md).entry)
- <a id="f-raceMask"></a>**`raceMask`** - Primary Key. Which races receive the mail (bitmask).
- <a id="f-quest"></a>**`quest`** - Primary Key. Quest that must be **rewarded/completed** by the player for the mail to be sent. (see [`quest_template`](quest_template.md).entry)
- <a id="f-mailTemplateId"></a>**`mailTemplateId`** - Mail template ID. (see [`mail_text_template`](mail_text_template.md).entry)
- <a id="f-senderEntry"></a>**`senderEntry`** - NPC or creature ID as sender. (see [`creature_template`](creature_template.md).entry)
