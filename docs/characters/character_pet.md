# character_pet Table

Persistent pet data (hunter pets and permanent warlock minions): stats, spells, loyalty, rename state.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(11) unsigned | PRI | NO | 0 |  |
| [`entry`](#f-entry) | int(11) unsigned |  | NO | 0 |  |
| [`owner_guid`](#f-owner_guid) | int(11) unsigned | MUL | NO | 0 |  |
| [`display_id`](#f-display_id) | int(11) unsigned |  | YES | 0 |  |
| [`created_by_spell`](#f-created_by_spell) | int(11) unsigned |  | NO | 0 |  |
| [`pet_type`](#f-pet_type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`level`](#f-level) | int(11) unsigned |  | NO | 1 |  |
| [`xp`](#f-xp) | int(11) unsigned |  | NO | 0 |  |
| [`react_state`](#f-react_state) | tinyint(1) unsigned |  | NO | 0 |  |
| [`loyalty_points`](#f-loyalty_points) | int(11) |  | NO | 0 |  |
| [`loyalty`](#f-loyalty) | int(11) unsigned |  | NO | 0 |  |
| [`training_points`](#f-training_points) | int(11) |  | NO | 0 |  |
| [`name`](#f-name) | varchar(100) |  | YES | 'Pet' |  |
| [`renamed`](#f-renamed) | tinyint(1) unsigned |  | NO | 0 |  |
| [`slot`](#f-slot) | int(11) unsigned |  | NO | 0 |  |
| [`current_health`](#f-current_health) | int(11) unsigned |  | NO | 1 |  |
| [`current_mana`](#f-current_mana) | int(11) unsigned |  | NO | 0 |  |
| [`current_happiness`](#f-current_happiness) | int(11) unsigned |  | NO | 0 |  |
| [`save_time`](#f-save_time) | bigint(20) unsigned |  | NO | 0 |  |
| [`reset_talents_cost`](#f-reset_talents_cost) | int(11) unsigned |  | NO | 0 |  |
| [`reset_talents_time`](#f-reset_talents_time) | bigint(20) unsigned |  | NO | 0 |  |
| [`action_bar_data`](#f-action_bar_data) | longtext |  | YES |  |  |
| [`teach_spell_data`](#f-teach_spell_data) | longtext |  | YES |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Persistent pet id (referenced by [`pet_aura`](pet_aura.md), [`pet_spell`](pet_spell.md), and [`pet_spell_cooldown`](pet_spell_cooldown.md) tables).
- <a id="f-entry"></a>**`entry`** - Creature template entry ([`creature_template`](../world/creature_template.md).entry).
- <a id="f-owner_guid"></a>**`owner_guid`** - Owner character guid ([`characters`](characters.md).guid).
- <a id="f-display_id"></a>**`display_id`** - Native (base) display model.
- <a id="f-created_by_spell"></a>**`created_by_spell`** - Spell that created/tamed the pet.
- <a id="f-pet_type"></a>**`pet_type`** - Pet type: `0` = summoned pet (warlock minion etc.), `1` = hunter pet;
  only these two values are ever persisted.
- <a id="f-level"></a>**`level`** - Pet level.
- <a id="f-xp"></a>**`xp`** - Experience towards next level.
- <a id="f-react_state"></a>**`react_state`** - Reaction: 0 passive, 1 defensive, 2 aggressive.
- <a id="f-loyalty_points"></a>**`loyalty_points`** - Accumulated loyalty experience points.
- <a id="f-loyalty"></a>**`loyalty`** - Loyalty rank level (1-6).
- <a id="f-training_points"></a>**`training_points`** - Points available for teaching abilities.
- <a id="f-name"></a>**`name`** - Current pet name.
- <a id="f-renamed"></a>**`renamed`** - Whether the owner already renamed the pet.
- <a id="f-slot"></a>**`slot`** - Pet save slot (`PetSaveMode`): 0 = active pet, 1-2 = stable slots, 100 = not in any slot, 101 = not in slot with reagent refund pending.
- <a id="f-current_health"></a>**`current_health`** - Saved vitals.
- <a id="f-current_mana"></a>**`current_mana`** - Saved vitals.
- <a id="f-current_happiness"></a>**`current_happiness`** - Happiness level (affects damage).
- <a id="f-save_time"></a>**`save_time`** - Unix timestamp of last save.
- <a id="f-reset_talents_cost"></a>**`reset_talents_cost`** - Cost paid at the last talent reset; scales the next price (10s → 50s → 1g → +1g per attempt, cap 10g).
- <a id="f-reset_talents_time"></a>**`reset_talents_time`** - Game time of the last talent reset (drives day-based price decay).
- <a id="f-action_bar_data"></a>**`action_bar_data`** - Serialized action bar assignment blob.
- <a id="f-teach_spell_data"></a>**`teach_spell_data`** - Serialized spell-teaching queue/state.
