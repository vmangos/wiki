# logs_player Table

Per-player audit log of notable account/character events written by the core when player logging is enabled.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(10) unsigned | PRI | NO |  | auto_increment |
| [`time`](#f-time) | timestamp |  | NO | current_timestamp() |  |
| [`type`](#f-type) | enum('Basic','WorldPacket','Chat','BG','Character','Honor','RA','DBError','DBErrorFix','ClientIds','Loot','LevelUp','Performance','MoneyTrade','GM','GMCritical','ChatSpam','Anticheat') |  | NO |  |  |
| [`subtype`](#f-subtype) | varchar(20) |  | YES |  |  |
| [`account`](#f-account) | int(10) unsigned | MUL | NO |  |  |
| [`ip`](#f-ip) | varchar(16) |  | YES |  |  |
| [`guid`](#f-guid) | int(11) | MUL | YES |  |  |
| [`name`](#f-name) | varchar(20) | MUL | YES |  |  |
| [`map`](#f-map) | int(10) unsigned |  | YES |  |  |
| [`pos_x`](#f-pos_x) | float |  | YES |  |  |
| [`pos_y`](#f-pos_y) | float |  | YES |  |  |
| [`pos_z`](#f-pos_z) | float |  | YES |  |  |
| [`text`](#f-text) | varchar(512) |  | NO |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Log row id.
- <a id="f-time"></a>**`time`** - Event timestamp.
- <a id="f-type"></a>**`type`** - Event category string. The column is declared as an `enum` (Basic, WorldPacket, Chat, BG, Character, Honor, RA, DBError, DBErrorFix, ClientIds, Loot, LevelUp, Performance, MoneyTrade, GM, GMCritical, ChatSpam, Anticheat); the core's `type_strings` additionally emit Scripts, Movement and Network, which fall outside the enum.
- <a id="f-subtype"></a>**`subtype`** - Optional sub-category string for the event type.
- <a id="f-account"></a>**`account`** - Account involved ([`account`](../realmd/account.md).id).
- <a id="f-ip"></a>**`ip`** - Source IP at event time.
- <a id="f-guid"></a>**`guid`** - Character involved (guid + name snapshot).
- <a id="f-name"></a>**`name`** - Character involved (guid + name snapshot).
- <a id="f-map"></a>**`map`** - Location at event time.
- <a id="f-pos_x"></a>**`pos_x`** - Location at event time.
- <a id="f-pos_y"></a>**`pos_y`** - Location at event time.
- <a id="f-pos_z"></a>**`pos_z`** - Location at event time.
- <a id="f-text"></a>**`text`** - Free-form payload/details for the event.

---

### type Values

| Value | Logged content |
| :--- | :--- |
| Basic | generic player events |
| WorldPacket | notable packet-level events |
| Chat | chat-related events |
| BG | battleground events |
| Character | login/logout/create/delete/rename events |
| Honor | honour calculation events |
| RA | remote-access console actions |
| DBError | database error context |
| DBErrorFix | automated DB error repairs |
| ClientIds | client identification data |
| Loot | loot events |
| LevelUp | level-ups |
| Performance | performance samples |
| MoneyTrade | money flow between players |
| GM | GM actions on players |
| GMCritical | critical GM actions |
| ChatSpam | spam detections/mutes |
| Anticheat | movement-anticheat and Warden detections |
