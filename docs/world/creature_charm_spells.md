# creature_charm_spells Table

Defines randomized spell pools for the spell slots of charmed creatures (e.g., mind-controlled mobs). For each slot, one spell is selected at spawn via a weighted roll, so a controlled creature can carry different spells each time.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`slot`](#f-slot) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`availability`](#f-availability) | float |  | NO | 100 |  |
| [`spell_id`](#f-spell_id) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`cooldown_min`](#f-cooldown_min) | smallint(5) unsigned |  | NO | 0 |  |
| [`cooldown_max`](#f-cooldown_max) | smallint(5) unsigned |  | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned |  | NO | 10 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Part of the composite primary key. Creature template ID from [`creature_template`](creature_template.md).entry.
- <a id="f-slot"></a>**`slot`** - Part of the composite primary key. Spell slot index (0-3). Multiple rows for the same slot form a pool from which one spell is chosen.
- <a id="f-availability"></a>**`availability`** - Percentage weight used in the random selection. At spawn, a roll between 0-100 is made and each row of the slot claims an interval proportional to its `availability`. Example: two rows with `50` each give a 50/50 split.
- <a id="f-spell_id"></a>**`spell_id`** - Part of the composite primary key. Spell ID from [`spell_template`](spell_template.md).entry assigned to this slot if selected.
- <a id="f-cooldown_min"></a>**`cooldown_min`** - Minimum cooldown (seconds) applied to the spell when used.
- <a id="f-cooldown_max"></a>**`cooldown_max`** - Maximum cooldown (seconds) applied to the spell when used. A random value between `cooldown_min` and `cooldown_max` is used.
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Content patch range (progression system). Rows only load if the current patch falls inside the range (0 = 1.2, 10 = 1.12.1).
