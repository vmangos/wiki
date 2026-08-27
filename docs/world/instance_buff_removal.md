# [`instance_buff_removal`](instance_buff_removal.md) Table

Defines spells (buffs) that are removed when entering specific instances.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`map_id`](#f-map_id) | int(10) unsigned | PRI | NO |  |  |
| [`spell_id`](#f-spell_id) | smallint(5) unsigned | PRI | NO |  |  |
| [`enabled`](#f-enabled) | tinyint(1) |  | NO |  |  |
| [`flags`](#f-flags) | int(10) |  | NO |  |  |
| [`comment`](#f-comment) | varchar(256) |  | NO |  |  |

---

## Field Breakdown

- <a id="f-map_id"></a>**`map_id`** - Primary Key. Map being entered (`Map.dbc` id).
- <a id="f-spell_id"></a>**`spell_id`** - Primary Key. Spell removed on entry (see [`spell_template`](spell_template.md).entry)*.
- <a id="f-enabled"></a>**`enabled`** - `1` if this removal rule is active.
- <a id="f-flags"></a>**`flags`** - Behaviour flags (`AuraRemovalFlags`, `AuraRemovalMgr.h`):
  - `1` - EXCLUDE_HORDE (keep the buff on Horde players)
  - `2` - EXCLUDE_ALLIANCE (keep the buff on Alliance players)
- <a id="f-comment"></a>**`comment`** - Description.

The manager (`src/game/AuraRemovalMgr.h`) strips listed auras from players when they enter the
map, used to strip world buffs before raid encounters.
