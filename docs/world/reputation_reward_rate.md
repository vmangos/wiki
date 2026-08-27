# reputation_reward_rate Table

Defines reputation reward multipliers for quests, creatures, and spells by faction.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`faction`](#f-faction) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`quest_rate`](#f-quest_rate) | float |  | NO | 1 |  |
| [`creature_rate`](#f-creature_rate) | float |  | NO | 1 |  |
| [`spell_rate`](#f-spell_rate) | float |  | NO | 1 |  |

---

## Field Breakdown

- <a id="f-faction"></a>**`faction`** - Primary Key. Reputation group id ([`faction`](faction.md).id).
- <a id="f-quest_rate"></a>**`quest_rate`** - Multiplier for quest reputation rewards.
- <a id="f-creature_rate"></a>**`creature_rate`** - Multiplier for creature kill reputation rewards.
- <a id="f-spell_rate"></a>**`spell_rate`** - Multiplier for spell reputation rewards.
