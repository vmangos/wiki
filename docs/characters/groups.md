# groups Table

Party and raid group headers (leader, loot rules, difficulty).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`group_id`](#f-group_id) | int(11) unsigned | PRI | NO |  |  |
| [`leader_guid`](#f-leader_guid) | int(11) unsigned | UNI | NO |  |  |
| [`main_tank_guid`](#f-main_tank_guid) | int(11) unsigned |  | NO |  |  |
| [`main_assistant_guid`](#f-main_assistant_guid) | int(11) unsigned |  | NO |  |  |
| [`loot_method`](#f-loot_method) | tinyint(4) unsigned |  | NO |  |  |
| [`loot_threshold`](#f-loot_threshold) | tinyint(4) unsigned |  | NO |  |  |
| [`looter_guid`](#f-looter_guid) | int(11) unsigned |  | NO |  |  |
| [`icon1`](#f-icon1) | int(11) unsigned |  | NO |  |  |
| [`icon2`](#f-icon2) | int(11) unsigned |  | NO |  |  |
| [`icon3`](#f-icon3) | int(11) unsigned |  | NO |  |  |
| [`icon4`](#f-icon4) | int(11) unsigned |  | NO |  |  |
| [`icon5`](#f-icon5) | int(11) unsigned |  | NO |  |  |
| [`icon6`](#f-icon6) | int(11) unsigned |  | NO |  |  |
| [`icon7`](#f-icon7) | int(11) unsigned |  | NO |  |  |
| [`icon8`](#f-icon8) | int(11) unsigned |  | NO |  |  |
| [`is_raid`](#f-is_raid) | tinyint(1) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-group_id"></a>**`group_id`** - Primary Key. Group identifier (also referenced by [`group_member`](group_member.md)/[`group_instance`](group_instance.md)).
- <a id="f-leader_guid"></a>**`leader_guid`** - Unique. Current leader.
- <a id="f-main_tank_guid"></a>**`main_tank_guid`** - Raid-assigned roles.
- <a id="f-main_assistant_guid"></a>**`main_assistant_guid`** - Raid-assigned roles.
- <a id="f-loot_method"></a>**`loot_method`** - 0 Free-for-all, 1 Round-robin, 2 Master loot, 3 Group loot, 4 Need-before-greed.
- <a id="f-loot_threshold"></a>**`loot_threshold`** - Quality threshold for group loot rules (0 white … 4 epic).
- <a id="f-looter_guid"></a>**`looter_guid`** - Master looter character when applicable.
- <a id="f-icon1"></a>**`icon1`** - Target icon assignments (skull/cross… → member guid).
- <a id="f-icon2"></a>**`icon2`** - Target icon assignments (skull/cross… → member guid).
- <a id="f-icon3"></a>**`icon3`** - Target icon assignments (skull/cross… → member guid).
- <a id="f-icon4"></a>**`icon4`** - Target icon assignments (skull/cross… → member guid).
- <a id="f-icon5"></a>**`icon5`** - Target icon assignments (skull/cross… → member guid).
- <a id="f-icon6"></a>**`icon6`** - Target icon assignments (skull/cross… → member guid).
- <a id="f-icon7"></a>**`icon7`** - Target icon assignments (skull/cross… → member guid).
- <a id="f-icon8"></a>**`icon8`** - Target icon assignments (skull/cross… → member guid).
- <a id="f-is_raid"></a>**`is_raid`** - 1 once converted to raid.

---

### loot_method Values

| Value | Name |
| :---: | :--- |
| 0 | Free-for-all |
| 1 | Round robin |
| 2 | Master looter |
| 3 | Group loot |
| 4 | Need before greed |
