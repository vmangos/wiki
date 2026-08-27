# Quest System

How quests work in VMaNGOS: the master [`quest_template`](world/quest_template.md) table, the
tables that attach quests to the world, and the character-side progress tables.

---

## Anatomy of a Quest

All quest definition lives in [`quest_template`](world/quest_template.md). The most important
field groups:

| Group | Fields |
| :--- | :--- |
| Identity | `entry`, `patch` ([progression](Progression-System.md)), `Title`, `Details`, text fields |
| Availability | `MinLevel`, `MaxLevel`, `QuestLevel`, `RequiredClasses`, `RequiredRaces`, `RequiredSkill(Value)`, `RequiredCondition`, reputation min/max pairs |
| Objectives | `ReqItemId1-4` (+count), `ReqCreatureOrGOId1-4` (+counts), `ReqSpellCast1-4`, kill credit fields |
| Flow control | `PrevQuestId`, `NextQuestId`, `ExclusiveGroup`, `BreadcrumbForQuestId`, `NextQuestInChain`, `SpecialFlags`, `QuestFlags`, `LimitTime` |
| Rewards | `RewItemId1-4`, choice items, `RewOrReqMoney`, XP, honour, spell rewards, mail templates |
| Starter text/items | `SrcItemId/Count/Spell` - given on accept |

Objectives are validated at load: referenced items/creatures/gameobjects must exist.

---

## Attaching Quests to the World

| Table | Purpose |
| :--- | :--- |
| [`creature_questrelation`](world/creature_questrelation.md) | Quest **givers** (NPCs offering the quest). |
| [`creature_involvedrelation`](world/creature_involvedrelation.md) | Quest **enders** (NPCs to turn in to). |
| [`gameobject_questrelation`](world/gameobject_questrelation.md) / [`gameobject_involvedrelation`](world/gameobject_involvedrelation.md) | Same for objects. |
| [`quest_greeting`](world/quest_greeting.md) | Custom greeting text/emotes for quest NPCs. |
| [`points_of_interest`](world/points_of_interest.md) | Map markers shown by gossip options pointing players toward objectives. |

Scripts can interact with quests via these DB script commands: 7 `QUEST_EXPLORED`,
70 `FAIL_QUEST` and 83 `QUEST_CREDIT`
(see [DB Script Tables](DB-Script-Tables.md)).

---

## Character-Side State

Stored per player in the characters database:

| Table | Contents |
| :--- | :--- |
| [`character_queststatus`](characters/character_queststatus.md) | Accepted/rewarded quests, kill counters, timers. |
| [`character_spell_cooldown`](characters/character_spell_cooldown.md) | Cooldowns (also used for timed quests). |
| [`character_reputation`](characters/character_reputation.md) | Reputation gates checked on offer. |

---

## Conditions

`RequiredCondition` gates availability with a [conditions](world/conditions.md) row; EventAI can
react to quest lifecycle via `EVENT_T_QUEST_ACCEPT` / `EVENT_T_QUEST_COMPLETE`
([EventAI types](world/creature_ai_events.md#event-types)).

---

## Related Pages

- [quest_template](world/quest_template.md)
- [Tutorial: Adding a Custom Quest](Tutorial-Custom-Quest.md)
