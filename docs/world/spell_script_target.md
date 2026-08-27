# spell_script_target Table

Defines script targets for spells - restricts spell to specific creatures or game objects.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO |  |  |
| [`type`](#f-type) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`targetEntry`](#f-targetEntry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`conditionId`](#f-conditionId) | mediumint(8) unsigned |  | NO | 0 |  |
| [`inverseEffectMask`](#f-inverseEffectMask) | mediumint(8) unsigned |  | NO | 0 |  |
| [`build_min`](#f-build_min) | smallint(4) unsigned |  | NO | 0 |  |
| [`build_max`](#f-build_max) | smallint(4) unsigned |  | NO | 5875 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-type"></a>**`type`** - Target kind (`enum SpellTargetType`, `SpellMgr.h`):

  | Value | Meaning | `targetEntry` is |
  | :---: | :--- | :--- |
  | 0 | GAMEOBJECT | gameobject template entry |
  | 1 | CREATURE | creature template entry |
  | 2 | DEAD creature | creature entry, must be dead |
  | 3 | PLAYER | - (`targetEntry` unused) |
- <a id="f-targetEntry"></a>**`targetEntry`** - Template entry of the required target (see table). (see [`creature_template`](creature_template.md).entry or [`gameobject_template`](gameobject_template.md).entry)
- <a id="f-conditionId"></a>**`conditionId`** - Condition. (see [`conditions`](conditions.md).condition_entry)
- <a id="f-inverseEffectMask"></a>**`inverseEffectMask`** - Bitmask over effect indexes (`1` = effect 1, `2` = effect 2,
  `4` = effect 3): effects with their bit set do **not** hit the scripted target defined here.
- <a id="f-build_max"></a><a id="f-build_min"></a>**`build_min` / `build_max`** - Client build range.
