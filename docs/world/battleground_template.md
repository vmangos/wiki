# battleground_template Table

Defines core parameters for each battleground: team sizes, level range, spawn locations, and reward spells.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | mediumint(8) unsigned | PRI | NO |  |  |
| [`patch`](#f-patch) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`min_players_per_team`](#f-min_players_per_team) | smallint(5) unsigned |  | NO | 0 |  |
| [`max_players_per_team`](#f-max_players_per_team) | smallint(5) unsigned |  | NO | 0 |  |
| [`min_level`](#f-min_level) | tinyint(3) unsigned |  | NO | 0 |  |
| [`max_level`](#f-max_level) | tinyint(3) unsigned |  | NO | 0 |  |
| [`alliance_win_spell`](#f-alliance_win_spell) | smallint(5) unsigned |  | NO | 0 |  |
| [`alliance_lose_spell`](#f-alliance_lose_spell) | smallint(5) unsigned |  | NO | 0 |  |
| [`horde_win_spell`](#f-horde_win_spell) | smallint(5) unsigned |  | NO | 0 |  |
| [`horde_lose_spell`](#f-horde_lose_spell) | smallint(5) unsigned |  | NO | 0 |  |
| [`alliance_start_location`](#f-alliance_start_location) | mediumint(8) unsigned |  | NO | 0 |  |
| [`horde_start_location`](#f-horde_start_location) | mediumint(8) unsigned |  | NO | 0 |  |
| [`player_loot_id`](#f-player_loot_id) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Battleground ID:
  - `1` - Alterac Valley
  - `2` - Warsong Gulch
  - `3` - Arathi Basin
- <a id="f-patch"></a>**`patch`** - Primary Key. Patch version - the core loads the highest patch ≤ current.
- <a id="f-max_players_per_team"></a><a id="f-min_players_per_team"></a>**`min_players_per_team` / `max_players_per_team`** - Team size limits.
- <a id="f-max_level"></a><a id="f-min_level"></a>**`min_level` / `max_level`** - Level bracket allowed to queue.
- <a id="f-alliance_lose_spell"></a><a id="f-alliance_win_spell"></a>**`alliance_win_spell` / `alliance_lose_spell`** - Spell cast on Alliance players on win/loss (from [`spell_template`](spell_template.md).entry).
- <a id="f-horde_lose_spell"></a><a id="f-horde_win_spell"></a>**`horde_win_spell` / `horde_lose_spell`** - Same for Horde.
- <a id="f-alliance_start_location"></a><a id="f-horde_start_location"></a>**`alliance_start_location` / `horde_start_location`** - WorldSafeLocs.dbc IDs (spawn points).
- <a id="f-player_loot_id"></a>**`player_loot_id`** - Reference loot template filled when skinning the bones of dead players in this battleground.
