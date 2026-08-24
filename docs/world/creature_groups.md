# creature_groups Table

Groups creatures into formations, with a leader and relative positions.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`leader_guid`](#f-leader_guid) | int(11) unsigned |  | NO |  |  |
| [`member_guid`](#f-member_guid) | int(11) unsigned | PRI | NO |  |  |
| [`dist`](#f-dist) | float unsigned |  | NO |  |  |
| [`angle`](#f-angle) | float unsigned |  | NO |  |  |
| [`flags`](#f-flags) | int(11) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-leader_guid"></a>**`leader_guid`** - GUID of the group leader.; references [`creature`](creature.md).guid
- <a id="f-member_guid"></a>**`member_guid`** - Primary Key. GUID of a group member.; references [`creature`](creature.md).guid
- <a id="f-dist"></a>**`dist`** - Distance from the leader.
- <a id="f-angle"></a>**`angle`** - Angle (radians) relative to the leader's facing.
- <a id="f-flags"></a>**`flags`** - Per-member behaviour bits (`OPTION_*`, `CreatureGroups.h`). Group-wide
  behaviour is the combination of all member rows' flags (the leader's own row is ignored);
  groups created at runtime via `.npc group add` default to `0x001|0x002|0x004|0x008`:

  | Bit | Option |
  | ---: | :--- |
  | 0x001 | FORMATION_MOVE - keep formation offsets |
  | 0x002 | AGGRO_TOGETHER - join combat when a groupmate does |
  | 0x004 | EVADE_TOGETHER |
  | 0x008 | RESPAWN_TOGETHER |
  | 0x010 | RESPAWN_ALL_ON_MASTER_EVADE |
  | 0x020 | RESPAWN_ALL_ON_ANY_EVADE |
  | 0x040 | INFORM_LEADER_ON_MEMBER_DIED |
  | 0x080 | INFORM_MEMBERS_ON_ANY_DIED |
