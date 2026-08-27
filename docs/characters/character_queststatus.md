# character_queststatus Table

Quest progress: accepted quests, kill/credit counters, rewarded status and timers.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`quest`](#f-quest) | int(11) unsigned | PRI | NO | 0 |  |
| [`status`](#f-status) | int(11) unsigned |  | NO | 0 |  |
| [`rewarded`](#f-rewarded) | tinyint(1) unsigned |  | NO | 0 |  |
| [`explored`](#f-explored) | tinyint(1) unsigned |  | NO | 0 |  |
| [`timer`](#f-timer) | bigint(20) unsigned |  | NO | 0 |  |
| [`mob_count1`](#f-mob_count1) | int(11) unsigned |  | NO | 0 |  |
| [`mob_count2`](#f-mob_count2) | int(11) unsigned |  | NO | 0 |  |
| [`mob_count3`](#f-mob_count3) | int(11) unsigned |  | NO | 0 |  |
| [`mob_count4`](#f-mob_count4) | int(11) unsigned |  | NO | 0 |  |
| [`item_count1`](#f-item_count1) | int(11) unsigned |  | NO | 0 |  |
| [`item_count2`](#f-item_count2) | int(11) unsigned |  | NO | 0 |  |
| [`item_count3`](#f-item_count3) | int(11) unsigned |  | NO | 0 |  |
| [`item_count4`](#f-item_count4) | int(11) unsigned |  | NO | 0 |  |
| [`reward_choice`](#f-reward_choice) | int(11) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-quest"></a>**`quest`** - Primary Key. [`quest_template`](../world/quest_template.md).entry.
- <a id="f-status"></a>**`status`** - Quest state - see the [Status Values table](#status-values) below.
- <a id="f-rewarded"></a>**`rewarded`** - 1 once turned in (drives repeatable re-offers).
- <a id="f-explored"></a>**`explored`** - Boolean flag (0/1), set when the exploration/event objective fires.
- <a id="f-timer"></a>**`timer`** - Expiry timestamp for timed quests.
- <a id="f-mob_count1"></a>**`mob_count1`** - Kill/credit counters for objectives 1-4.
- <a id="f-mob_count2"></a>**`mob_count2`** - Kill/credit counters for objectives 1-4.
- <a id="f-mob_count3"></a>**`mob_count3`** - Kill/credit counters for objectives 1-4.
- <a id="f-mob_count4"></a>**`mob_count4`** - Kill/credit counters for objectives 1-4.
- <a id="f-item_count1"></a>**`item_count1`** - Collected item counters for objectives 1-4.
- <a id="f-item_count2"></a>**`item_count2`** - Collected item counters for objectives 1-4.
- <a id="f-item_count3"></a>**`item_count3`** - Collected item counters for objectives 1-4.
- <a id="f-item_count4"></a>**`item_count4`** - Collected item counters for objectives 1-4.
- <a id="f-reward_choice"></a>**`reward_choice`** - Item entry of the optional reward chosen at turn-in
  (stored once the quest is rewarded).

---

### status Values {#status-values}

| Value | Meaning |
| :---: | :--- |
| 0 | None (not accepted) |
| 1 | Complete (objectives done, ready to hand in) |
| 2 | Unavailable |
| 3 | Incomplete (accepted, objectives pending) |
| 5 | Failed (timed quests) |

> `rewarded = 1` marks completed-and-turned-in separately so repeatable quests can be re-taken.
