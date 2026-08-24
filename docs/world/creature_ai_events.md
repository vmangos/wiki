# creature_ai_events Table

Defines events that trigger scripts for creatures using EventAI. This AI type must be assigned in [`creature_template`](creature_template.md).ai_name. It is recommended to use the ScriptEditor for creating these scripts.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(11) unsigned | PRI | NO |  | auto_increment |
| [`creature_id`](#f-creature_id) | int(11) unsigned |  | NO | 0 |  |
| [`condition_id`](#f-condition_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`event_type`](#f-event_type) | tinyint(5) unsigned |  | NO | 0 |  |
| [`event_inverse_phase_mask`](#f-event_inverse_phase_mask) | int(11) |  | NO | 0 |  |
| [`event_chance`](#f-event_chance) | tinyint(3) unsigned |  | NO | 100 |  |
| [`event_flags`](#f-event_flags) | int(3) unsigned |  | NO | 0 |  |
| [`event_param1`](#f-event_param1) | int(11) |  | NO | 0 |  |
| [`event_param2`](#f-event_param2) | int(11) |  | NO | 0 |  |
| [`event_param3`](#f-event_param3) | int(11) |  | NO | 0 |  |
| [`event_param4`](#f-event_param4) | int(11) |  | NO | 0 |  |
| [`action1_script`](#f-action1_script) | int(11) unsigned |  | NO | 0 |  |
| [`action2_script`](#f-action2_script) | int(11) unsigned |  | NO | 0 |  |
| [`action3_script`](#f-action3_script) | int(11) unsigned |  | NO | 0 |  |
| [`comment`](#f-comment) | varchar(255) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Convention: multiply creature_id by 100 and increment for each event.
- <a id="f-creature_id"></a>**`creature_id`** - Creature template entry ([`creature_template`](creature_template.md).entry).
- <a id="f-condition_id"></a>**`condition_id`** - Optional condition (from [`conditions`](conditions.md).condition_entry).
- <a id="f-event_type"></a>**`event_type`** - The trigger type; see the [Event Types table](#event-types) below.
- <a id="f-event_inverse_phase_mask"></a>**`event_inverse_phase_mask`** - Phases where this event will **not** trigger. Compute as sum of 2^phase; e.g. `1` = phase 0 disabled, `3` = phases 0 and 1 disabled.
- <a id="f-event_chance"></a>**`event_chance`** - Percentage chance (1-100) for the event to fire.
- <a id="f-event_flags"></a>**`event_flags`** - Bitmask (`EventFlags`, CreatureEventAI.h):
  - `0x01` - `EFLAG_REPEATABLE` - Event repeats.
  - `0x02` - `EFLAG_RANDOM_ACTION` - Only one of the assigned actions executes instead of all.
  - `0x04` - `EFLAG_NOT_CASTING` - Will not occur while the creature is casting a spell.
  - `0x08` - `EFLAG_CHECK_RESULT` - Will not go on cooldown if the script actions fail.
  - `0x10` - `EFLAG_DEBUG_ONLY` - Only occurs in debug builds.
- <a id="f-event_param1"></a>**`event_param1`** - Meaning depends on `event_type`; see [Event Types](#event-types).
- <a id="f-event_param2"></a>**`event_param2`** - See [Event Types](#event-types).
- <a id="f-event_param3"></a>**`event_param3`** - See [Event Types](#event-types).
- <a id="f-event_param4"></a>**`event_param4`** - See [Event Types](#event-types).
- <a id="f-action1_script"></a>**`action1_script`** - Script executed by this event slot (from [`creature_ai_scripts`](creature_ai_scripts.md).id).
- <a id="f-action2_script"></a>**`action2_script`** - Second script slot (from [`creature_ai_scripts`](creature_ai_scripts.md).id).
- <a id="f-action3_script"></a>**`action3_script`** - Third script slot (from [`creature_ai_scripts`](creature_ai_scripts.md).id).
- <a id="f-comment"></a>**`comment`** - Descriptive comment, convention: `Creature Name - Action Type on Event Type`.

---

## Event Types

The `event_type` field defines when the event triggers. The meaning of `event_param1-4` depends on the type.

| Type | Name | Description | param1 | param2 | param3 | param4 |
| :---: | :--- | :--- | :--- | :--- | :--- | :--- |
| 0 | `EVENT_T_TIMER_IN_COMBAT` | Timer while in combat. | initial_min | initial_max | repeat_min | repeat_max |
| 1 | `EVENT_T_TIMER_OOC` | Timer while out of combat. | initial_min | initial_max | repeat_min | repeat_max |
| 2 | `EVENT_T_HP` | Creature health percentage. | hp_max% | hp_min% | repeat_min | repeat_max |
| 3 | `EVENT_T_MANA` | Creature mana percentage. | mana_max% | mana_min% | repeat_min | repeat_max |
| 4 | `EVENT_T_AGGRO` | On entering combat. | - | - | - | - |
| 5 | `EVENT_T_KILL` | On killing a player. | repeat_min | repeat_max | player_only | - |
| 6 | `EVENT_T_DEATH` | On death. | - | - | - | - |
| 7 | `EVENT_T_EVADE` | On evading. | - | - | - | - |
| 8 | `EVENT_T_HIT_BY_SPELL` | Creature is hit by a spell. | spell_id | school_mask | repeat_min | repeat_max |
| 9 | `EVENT_T_RANGE` | Target within distance range. | min_dist | max_dist | repeat_min | repeat_max |
| 10 | `EVENT_T_OOC_LOS` | Line of sight out of combat. | reaction (0 any / 1 hostile / 2 non-hostile) | max_range | repeat_min | repeat_max |
| 11 | `EVENT_T_SPAWNED` | On spawn/respawn. | - | - | - | - |
| 12 | `EVENT_T_TARGET_HP` | Victim health percentage. | hp_max% | hp_min% | repeat_min | repeat_max |
| 13 | `EVENT_T_TARGET_CASTING` | Victim is casting a spell. | repeat_min | repeat_max | - | - |
| 14 | `EVENT_T_FRIENDLY_HP` | Friendly unit health deficit. | hp_deficit | radius | repeat_min | repeat_max |
| 15 | `EVENT_T_FRIENDLY_IS_CC` | Friendly unit under crowd control. | dispel_type | radius | repeat_min | repeat_max |
| 16 | `EVENT_T_FRIENDLY_MISSING_BUFF` | Friendly unit missing an aura. | spell_id | radius | repeat_min | repeat_max |
| 17 | `EVENT_T_SUMMONED_UNIT` | A creature was summoned. | creature_id | repeat_min | repeat_max | - |
| 18 | `EVENT_T_TARGET_MANA` | Victim mana percentage. | mana_max% | mana_min% | repeat_min | repeat_max |
| 19 | `EVENT_T_QUEST_ACCEPT` | Player accepts a quest from the creature. | quest_id | - | - | - |
| 20 | `EVENT_T_QUEST_COMPLETE` | Player completes a quest from the creature. | quest_id | - | - | - |
| 21 | `EVENT_T_REACHED_HOME` | Creature returned to its home position. | - | - | - | - |
| 22 | `EVENT_T_RECEIVE_EMOTE` | Creature receives an emote. | emote_id | condition_id | cond_value1 | cond_value2 |
| 23 | `EVENT_T_AURA` | Creature has a specific aura/stack count. | spell_id | stack_count | repeat_min | repeat_max |
| 24 | `EVENT_T_TARGET_AURA` | Victim has a specific aura/stack count. | spell_id | stack_count | repeat_min | repeat_max |
| 25 | `EVENT_T_SUMMONED_JUST_DIED` | A summoned creature died. | creature_id | repeat_min | repeat_max | - |
| 26 | `EVENT_T_SUMMONED_JUST_DESPAWN` | A summoned creature despawned. | creature_id | repeat_min | repeat_max | - |
| 27 | `EVENT_T_MISSING_AURA` | Creature lacks a specific aura/stack count. | spell_id | stack_count | repeat_min | repeat_max |
| 28 | `EVENT_T_TARGET_MISSING_AURA` | Victim lacks a specific aura/stack count. | spell_id | stack_count | repeat_min | repeat_max |
| 29 | `EVENT_T_MOVEMENT_INFORM` | Movement generator reached a point. | motion_type | point_id | repeat_min | repeat_max |
| 30 | `EVENT_T_LEAVE_COMBAT` | On leaving combat. | - | - | - | - |
| 31 | `EVENT_T_SCRIPT` | Triggered by script command 85 SEND_SCRIPT_EVENT. | event_id | data | - | - |
| 32 | `EVENT_T_GROUP_MEMBER_DIED` | A creature group member died. | creature_id | is_leader | - | - |
| 33 | `EVENT_T_VICTIM_ROOTED` | Victim is rooted. | repeat_min | repeat_max | - | - |
| 34 | `EVENT_T_HIT_BY_AURA` | Creature is hit by an aura of this type. | aura_type | unused | repeat_min | repeat_max |
| 35 | `EVENT_T_STEALTH_ALERT` | Stealth detection alert. | repeat_min | repeat_max | - | - |
| 36 | `EVENT_T_SPELL_HIT_TARGET` | Victim is hit by a spell. | spell_id | school_mask | repeat_min | repeat_max |

> **Note:** For repeating events set `EFLAG_REPEATABLE` (`0x01`); otherwise the event fires only once per spawn.
