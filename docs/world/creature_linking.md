# creature_linking Table

Links a creature to a master creature. Used for leash logic (e.g., linked mobs reset together).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO |  |  |
| [`master_guid`](#f-master_guid) | int(10) unsigned |  | NO |  |  |
| [`flag`](#f-flag) | mediumint(8) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Creature GUID (the follower).; references [`creature`](creature.md).guid
- <a id="f-master_guid"></a>**`master_guid`** - GUID of the master creature.; references [`creature`](creature.md).guid
- <a id="f-flag"></a>**`flag`** - Link behaviour bitmask (`CreatureLinkingFlags`, `CreatureLinkingMgr.h`):

  | Bit | Flag | Effect |
  | ---: | :--- | :--- |
  | 0x0001 | AGGRO_ON_AGGRO | slave aggroes when master is attacked |
  | 0x0002 | TO_AGGRO_ON_AGGRO | master aggroes when slave is attacked |
  | 0x0004 | RESPAWN_ON_EVADE | slave respawns on master evade |
  | 0x0008 | TO_RESPAWN_ON_EVADE | master respawns on slave evade |
  | 0x0010 | DESPAWN_ON_DEATH | despawn slave on master death |
  | 0x0020 | SELFKILL_ON_DEATH | kill slave on master death |
  | 0x0040 | RESPAWN_ON_DEATH | respawn slave on master death |
  | 0x0080 | RESPAWN_ON_RESPAWN | respawn slave on master respawn |
  | 0x0100 | DESPAWN_ON_RESPAWN | despawn slave on master respawn |
  | 0x0200 | FOLLOW | slave follows master movement |
  | 0x0400 | CANT_SPAWN_IF_BOSS_DEAD | slave stays hidden after master dies |
  | 0x0800 | CANT_SPAWN_IF_BOSS_ALIVE | slave hidden until master dies |
  | 0x1000 | DESPAWN_ON_EVADE | despawn slave on master evade |
  | 0x2000 | DESPAWN_ON_DESPAWN | slave despawns with master |
  | 0x4000 | EVADE_ON_EVADE | slave evades with master |

  Trigger events (aggro/evade/die/respawn/despawn) are implied by the chosen flags.
