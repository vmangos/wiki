# characters Table

The central table: one row per player character with race/class/level, position, money and appearance.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`account`](#f-account) | int(11) unsigned | MUL | NO | 0 |  |
| [`name`](#f-name) | varchar(12) | MUL | NO | '' |  |
| [`race`](#f-race) | tinyint(3) unsigned |  | NO | 0 |  |
| [`class`](#f-class) | tinyint(3) unsigned |  | NO | 0 |  |
| [`gender`](#f-gender) | tinyint(3) unsigned |  | NO | 0 |  |
| [`skin`](#f-skin) | tinyint(3) unsigned |  | NO | 0 |  |
| [`face`](#f-face) | tinyint(3) unsigned |  | NO | 0 |  |
| [`hair_style`](#f-hair_style) | tinyint(3) unsigned |  | NO | 0 |  |
| [`hair_color`](#f-hair_color) | tinyint(3) unsigned |  | NO | 0 |  |
| [`facial_hair`](#f-facial_hair) | tinyint(3) unsigned |  | NO | 0 |  |
| [`level`](#f-level) | tinyint(3) unsigned |  | NO | 0 |  |
| [`xp`](#f-xp) | int(10) unsigned |  | NO | 0 |  |
| [`money`](#f-money) | int(10) unsigned |  | NO | 0 |  |
| [`character_flags`](#f-character_flags) | int(10) unsigned |  | NO | 0 |  |
| [`zone`](#f-zone) | int(11) unsigned |  | NO | 0 |  |
| [`map`](#f-map) | int(11) unsigned |  | NO | 0 |  |
| [`instance`](#f-instance) | int(11) unsigned | MUL | NO | 0 |  |
| [`position_x`](#f-position_x) | float |  | NO | 0 |  |
| [`position_y`](#f-position_y) | float |  | NO | 0 |  |
| [`position_z`](#f-position_z) | float |  | NO | 0 |  |
| [`orientation`](#f-orientation) | float |  | NO | 0 |  |
| [`transport_guid`](#f-transport_guid) | bigint(20) unsigned |  | NO | 0 |  |
| [`transport_x`](#f-transport_x) | float |  | NO | 0 |  |
| [`transport_y`](#f-transport_y) | float |  | NO | 0 |  |
| [`transport_z`](#f-transport_z) | float |  | NO | 0 |  |
| [`transport_o`](#f-transport_o) | float |  | NO | 0 |  |
| [`known_taxi_mask`](#f-known_taxi_mask) | longtext |  | YES |  |  |
| [`current_taxi_path`](#f-current_taxi_path) | text |  | YES |  |  |
| [`online`](#f-online) | tinyint(3) unsigned | MUL | NO | 0 |  |
| [`played_time_total`](#f-played_time_total) | int(11) unsigned |  | NO | 0 |  |
| [`played_time_level`](#f-played_time_level) | int(11) unsigned |  | NO | 0 |  |
| [`create_time`](#f-create_time) | bigint(20) unsigned |  | NO | 0 |  |
| [`logout_time`](#f-logout_time) | bigint(20) unsigned |  | NO | 0 |  |
| [`rest_bonus`](#f-rest_bonus) | float |  | NO | 0 |  |
| [`reset_talents_multiplier`](#f-reset_talents_multiplier) | int(11) unsigned |  | NO | 0 |  |
| [`reset_talents_time`](#f-reset_talents_time) | bigint(20) unsigned |  | NO | 0 |  |
| [`death_expire_time`](#f-death_expire_time) | bigint(20) unsigned |  | NO | 0 |  |
| [`stable_slots`](#f-stable_slots) | tinyint(1) unsigned |  | NO | 0 |  |
| [`bank_bag_slots`](#f-bank_bag_slots) | tinyint(1) unsigned |  | NO | 0 |  |
| [`extra_flags`](#f-extra_flags) | int(11) unsigned |  | NO | 0 |  |
| [`honor_rank_points`](#f-honor_rank_points) | float |  | NO | 0 |  |
| [`honor_highest_rank`](#f-honor_highest_rank) | int(11) unsigned |  | NO | 0 |  |
| [`honor_standing`](#f-honor_standing) | int(11) unsigned |  | NO | 0 |  |
| [`honor_last_week_hk`](#f-honor_last_week_hk) | int(11) unsigned |  | NO | 0 |  |
| [`honor_last_week_cp`](#f-honor_last_week_cp) | float |  | NO | 0 |  |
| [`honor_stored_hk`](#f-honor_stored_hk) | int(11) |  | NO | 0 |  |
| [`honor_stored_dk`](#f-honor_stored_dk) | int(11) |  | NO | 0 |  |
| [`watched_faction`](#f-watched_faction) | int(11) |  | NO | -1 |  |
| [`drunk`](#f-drunk) | smallint(5) unsigned |  | NO | 0 |  |
| [`health`](#f-health) | int(10) unsigned |  | NO | 0 |  |
| [`power1`](#f-power1) | int(10) unsigned |  | NO | 0 |  |
| [`power2`](#f-power2) | int(10) unsigned |  | NO | 0 |  |
| [`power3`](#f-power3) | int(10) unsigned |  | NO | 0 |  |
| [`power4`](#f-power4) | int(10) unsigned |  | NO | 0 |  |
| [`power5`](#f-power5) | int(10) unsigned |  | NO | 0 |  |
| [`explored_zones`](#f-explored_zones) | longtext |  | YES |  |  |
| [`equipment_cache`](#f-equipment_cache) | longtext |  | YES |  |  |
| [`ammo_id`](#f-ammo_id) | int(10) unsigned |  | NO | 0 |  |
| [`action_bars`](#f-action_bars) | tinyint(3) unsigned |  | NO | 0 |  |
| [`deleted_account`](#f-deleted_account) | int(11) unsigned |  | YES |  |  |
| [`deleted_name`](#f-deleted_name) | varchar(12) |  | YES |  |  |
| [`deleted_time`](#f-deleted_time) | bigint(20) |  | YES |  |  |
| [`world_phase_mask`](#f-world_phase_mask) | int(11) |  | YES | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Global unique character id, referenced everywhere (inventory, mail, guilds...).
- <a id="f-account"></a>**`account`** - Account identifier ([`account`](../realmd/account.md).id).
- <a id="f-name"></a>**`name`** - Character name (unique per realm).
- <a id="f-race"></a>**`race`** - Character race id (`ChrRaces.dbc`).
- <a id="f-class"></a>**`class`** - Character class id (`ChrClasses.dbc`).
- <a id="f-gender"></a>**`gender`** - `0` male, `1` female.
- <a id="f-skin"></a>**`skin`** - Skin colour index.
- <a id="f-face"></a>**`face`** - Face shape index.
- <a id="f-hair_style"></a>**`hair_style`** - Hairstyle index.
- <a id="f-hair_color"></a>**`hair_color`** - Hair colour index.
- <a id="f-facial_hair"></a>**`facial_hair`** - Facial hair style index.
- <a id="f-level"></a>**`level`** - Character level.
- <a id="f-xp"></a>**`xp`** - Experience towards next level.
- <a id="f-money"></a>**`money`** - Copper total (10000 copper = 1 gold).
- <a id="f-character_flags"></a>**`character_flags`** - Misc persisted player flags.
- <a id="f-zone"></a>**`zone`** - Zone id of the logout position.
- <a id="f-map"></a>**`map`** - Map id of the logout position.
- <a id="f-instance"></a>**`instance`** - Instance save id ([`instance`](instance.md).id) when logged out inside a dungeon/raid.
- <a id="f-position_x"></a>**`position_x`** - Logout X coordinate.
- <a id="f-position_y"></a>**`position_y`** - Logout Y coordinate.
- <a id="f-position_z"></a>**`position_z`** - Logout Z coordinate.
- <a id="f-orientation"></a>**`orientation`** - Logout facing.
- <a id="f-transport_guid"></a>**`transport_guid`** - If logged out on a boat/zeppelin: transport object and local offset.
- <a id="f-transport_x"></a>**`transport_x`** - Coordinate relative to the transport when saved on a boat/zeppelin.
- <a id="f-transport_y"></a>**`transport_y`** - Coordinate relative to the transport when saved on a boat/zeppelin.
- <a id="f-transport_z"></a>**`transport_z`** - Coordinate relative to the transport when saved on a boat/zeppelin.
- <a id="f-transport_o"></a>**`transport_o`** - Orientation relative to the transport when saved on a boat/zeppelin.
- <a id="f-known_taxi_mask"></a>**`known_taxi_mask`** - Bitmask of discovered flight paths.
- <a id="f-current_taxi_path"></a>**`current_taxi_path`** - Active flight path when saving mid-flight.
- <a id="f-online"></a>**`online`** - 1 while logged in; guards against double login.
- <a id="f-played_time_total"></a>**`played_time_total`** - Total seconds played on this character.
- <a id="f-played_time_level"></a>**`played_time_level`** - Seconds played at the current level.
- <a id="f-create_time"></a>**`create_time`** - Character creation date.
- <a id="f-logout_time"></a>**`logout_time`** - Last logout timestamp.
- <a id="f-rest_bonus"></a>**`rest_bonus`** - Accumulated rest bonus (XP %) for the resting system.
- <a id="f-reset_talents_multiplier"></a>**`reset_talents_multiplier`** - Talent reset cost escalation multiplier.
- <a id="f-reset_talents_time"></a>**`reset_talents_time`** - Last talent reset timestamp.
- <a id="f-death_expire_time"></a>**`death_expire_time`** - Expiry timestamp of the repeated-death cooldown used to
  escalate the corpse reclaim delay (5-minute steps per recent death).
- <a id="f-stable_slots"></a>**`stable_slots`** - Hunter pet stable slots purchased.
- <a id="f-bank_bag_slots"></a>**`bank_bag_slots`** - Bank bag slots purchased.
- <a id="f-extra_flags"></a>**`extra_flags`** - Persistent per-character toggles from `PlayerExtraFlags`: GM mode, ticket/whisper acceptance, taxi cheat, GM invisibility/chat badge, auction-house faction preference, pending PvP death, city protector (full table in [Data Lifecycle](../Data-Lifecycle.md)).
- <a id="f-honor_rank_points"></a>**`honor_rank_points`** - Current rank points from the last honour day.
- <a id="f-honor_highest_rank"></a>**`honor_highest_rank`** - Highest rank ever achieved.
- <a id="f-honor_standing"></a>**`honor_standing`** - Position within the rank for this honour week.
- <a id="f-honor_last_week_hk"></a>**`honor_last_week_hk`** - Yesterday/last-week HK & CP bookkeeping for the honour day tick.
- <a id="f-honor_last_week_cp"></a>**`honor_last_week_cp`** - Yesterday/last-week HK & CP bookkeeping for the honour day tick.
- <a id="f-honor_stored_hk"></a>**`honor_stored_hk`** - Lifetime total honorable kills accumulated across honour-week ticks.
- <a id="f-honor_stored_dk"></a>**`honor_stored_dk`** - Lifetime total dishonorable kills accumulated across honour-week ticks.
- <a id="f-watched_faction"></a>**`watched_faction`** - Faction id currently watched in the rep panel.
- <a id="f-drunk"></a>**`drunk`** - Soberness level 0-255 (Drunk status tiers).
- <a id="f-health"></a>**`health`** - Saved vitals: health + mana/rage/focus/energy/happiness.
- <a id="f-power1"></a>**`power1`** - Saved vitals: health + mana/rage/focus/energy/happiness.
- <a id="f-power2"></a>**`power2`** - Saved vitals: health + mana/rage/focus/energy/happiness.
- <a id="f-power3"></a>**`power3`** - Saved vitals: health + mana/rage/focus/energy/happiness.
- <a id="f-power4"></a>**`power4`** - Saved vitals: health + mana/rage/focus/energy/happiness.
- <a id="f-power5"></a>**`power5`** - Saved vitals: health + mana/rage/focus/energy/happiness.
- <a id="f-explored_zones"></a>**`explored_zones`** - Exploration bitmasks per continent (discovery XP).
- <a id="f-equipment_cache"></a>**`equipment_cache`** - Cached appearance blob for other-player equipment display.
- <a id="f-ammo_id"></a>**`ammo_id`** - Currently equipped ranged ammo.
- <a id="f-action_bars"></a>**`action_bars`** - Action bar configuration mode bits.
- <a id="f-deleted_account"></a>**`deleted_account`** - Set while the character sits in the deletion grace window
  (`CharDelete.Method=1`); `name` is blanked and `account` zeroed, with originals kept in `deleted_name`/`deleted_account`.
  With method 0 the row is wiped immediately instead.
- <a id="f-deleted_name"></a>**`deleted_name`** - Original name preserved during the deletion grace window.
- <a id="f-deleted_time"></a>**`deleted_time`** - When the character entered the deletion grace window.
- <a id="f-world_phase_mask"></a>**`world_phase_mask`** - Phase mask for phased content visibility.
