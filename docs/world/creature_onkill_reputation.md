# creature_onkill_reputation Table

Reputation rewards granted when a player kills a creature of a specific entry.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`creature_id`](#f-creature_id) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`patch`](#f-patch) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`RewOnKillRepFaction1`](#f-RewOnKillRepFaction1) | smallint(6) |  | NO | 0 |  |
| [`RewOnKillRepFaction2`](#f-RewOnKillRepFaction2) | smallint(6) |  | NO | 0 |  |
| [`MaxStanding1`](#f-MaxStanding1) | tinyint(4) |  | NO | 0 |  |
| [`IsTeamAward1`](#f-IsTeamAward1) | tinyint(4) |  | NO | 0 |  |
| [`RewOnKillRepValue1`](#f-RewOnKillRepValue1) | mediumint(9) |  | NO | 0 |  |
| [`MaxStanding2`](#f-MaxStanding2) | tinyint(4) |  | NO | 0 |  |
| [`IsTeamAward2`](#f-IsTeamAward2) | tinyint(4) |  | NO | 0 |  |
| [`RewOnKillRepValue2`](#f-RewOnKillRepValue2) | mediumint(9) |  | NO | 0 |  |
| [`TeamDependent`](#f-TeamDependent) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-creature_id"></a>**`creature_id`** - Primary Key. Creature entry the reward applies to. (see [`creature_template`](creature_template.md).entry)
- <a id="f-patch"></a>**`patch`** - Primary Key. Client patch version.
- <a id="f-RewOnKillRepFaction1"></a>**`RewOnKillRepFaction1`** - Faction(s) receiving reputation on kill (two independent rows worth of settings).
- <a id="f-RewOnKillRepFaction2"></a>**`RewOnKillRepFaction2`** - Faction gaining reputation (second row).
- <a id="f-MaxStanding1"></a>**`MaxStanding1`** - Highest rank that still receives the reward.
- <a id="f-IsTeamAward1"></a>**`IsTeamAward1`** - 1 = also award half the reputation to the faction's parent team (Alliance/Horde).
- <a id="f-RewOnKillRepValue1"></a>**`RewOnKillRepValue1`** - Reputation points granted (negative = loss).
- <a id="f-MaxStanding2"></a>**`MaxStanding2`** - Highest rank still rewarded (second row).
- <a id="f-IsTeamAward2"></a>**`IsTeamAward2`** - Also award half the reputation to the faction's parent team (second row).
- <a id="f-RewOnKillRepValue2"></a>**`RewOnKillRepValue2`** - Reputation points granted (second row).
- <a id="f-TeamDependent"></a>**`TeamDependent`** - Whether reward depends on the killer's team.
