# logs_player Table

Per-player audit log of notable account/character events, written by the core when the corresponding `LogDB.*` player-logging categories are enabled in `mangosd.conf`.

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
- <a id="f-type"></a>**`type`** - Event category, one of the `enum` values listed under [type Values](#type-values). Only a subset of these values is actually persisted; see that section.
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

All rows are valid members of the column `enum`. The core only persists a subset to this table, selected by the `LogDB.*` config settings in `mangosd.conf`:

| `LogDB.*` setting | Recorded `type` value(s) |
| :--- | :--- |
| `LogDB.Chat` | Chat |
| `LogDB.Battlegrounds` | BG |
| `LogDB.Characters` | Character |
| `LogDB.Loot` | Loot |
| `LogDB.LevelUp` | LevelUp |
| `LogDB.Trades` | MoneyTrade |
| `LogDB.GM` | GM, GMCritical |

The values actually written are therefore: **Chat, BG, Character, Loot, LevelUp, MoneyTrade, GM, GMCritical**. The remaining `enum` members (Basic, WorldPacket, Honor, RA, DBError, DBErrorFix, ClientIds, Performance, ChatSpam, Anticheat) are defined in the `enum` but are not currently recorded by the core.

| Value | Logged content | Persisted to DB? |
| :--- | :--- | :--- |
| Basic | generic player events | No |
| WorldPacket | notable packet-level events | No |
| Chat | chat-related events | Yes |
| BG | battleground events | Yes |
| Character | login/logout/create/delete/rename events | Yes |
| Honor | honour calculation events | No |
| RA | remote-access console actions | No |
| DBError | database error context | No |
| DBErrorFix | automated DB error repairs | No |
| ClientIds | client identification data | No |
| Loot | loot events | Yes |
| LevelUp | level-ups | Yes |
| Performance | performance samples | No |
| MoneyTrade | money flow between players | Yes |
| GM | GM actions on players | Yes |
| GMCritical | critical GM actions | Yes |
| ChatSpam | spam detections/mutes | No |
| Anticheat | movement-anticheat and Warden detections | No |
