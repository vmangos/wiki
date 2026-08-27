# logs_battleground Table

Per-participant battleground log rows written once, when a battleground finishes.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`time`](#f-time) | timestamp |  | YES | current_timestamp() |  |
| [`bgid`](#f-bgid) | int(11) |  | YES |  |  |
| [`bgtype`](#f-bgtype) | int(11) |  | YES |  |  |
| [`bgteamcount`](#f-bgteamcount) | int(11) |  | YES |  |  |
| [`bgduration`](#f-bgduration) | int(11) |  | YES |  |  |
| [`playerGuid`](#f-playerGuid) | int(11) |  | YES |  |  |
| [`team`](#f-team) | int(11) |  | YES |  |  |
| [`deaths`](#f-deaths) | int(11) |  | YES |  |  |
| [`honorBonus`](#f-honorBonus) | int(11) |  | YES |  |  |
| [`honorableKills`](#f-honorableKills) | int(11) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-time"></a>**`time`** - Row timestamp (insert time).
- <a id="f-bgid"></a>**`bgid`** - Battleground instance id of the finished match.
- <a id="f-bgtype"></a>**`bgtype`** - Battleground type id (AV/WSG/AB; matches [`battleground_template`](../world/battleground_template.md).id).
- <a id="f-bgteamcount"></a>**`bgteamcount`** - Player count on this player's team when the match ended.
- <a id="f-bgduration"></a>**`bgduration`** - Match duration seconds.
- <a id="f-playerGuid"></a>**`playerGuid`** - Participant character guid (from [`characters`](../characters/characters.md).guid).
- <a id="f-team"></a>**`team`** - Player's team inside the BG.
- <a id="f-deaths"></a>**`deaths`** - Deaths by this player in the match.
- <a id="f-honorBonus"></a>**`honorBonus`** - Bonus honour granted.
- <a id="f-honorableKills"></a>**`honorableKills`** - Honourable kills credited.
