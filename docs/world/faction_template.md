# faction_template Table

Defines faction reactions - which factions are friendly, hostile, or enemy.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | smallint(4) unsigned | PRI | NO | 0 |  |
| [`build`](#f-build) | smallint(4) unsigned | PRI | NO | 5875 |  |
| [`faction_id`](#f-faction_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`faction_flags`](#f-faction_flags) | mediumint(8) unsigned |  | NO | 0 |  |
| [`our_mask`](#f-our_mask) | mediumint(8) unsigned |  | NO | 0 |  |
| [`friendly_mask`](#f-friendly_mask) | mediumint(8) unsigned |  | NO | 0 |  |
| [`hostile_mask`](#f-hostile_mask) | mediumint(8) unsigned |  | NO | 0 |  |
| [`enemy_faction1`](#f-enemy_faction1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`enemy_faction2`](#f-enemy_faction2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`enemy_faction3`](#f-enemy_faction3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`enemy_faction4`](#f-enemy_faction4) | mediumint(8) unsigned |  | NO | 0 |  |
| [`friend_faction1`](#f-friend_faction1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`friend_faction2`](#f-friend_faction2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`friend_faction3`](#f-friend_faction3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`friend_faction4`](#f-friend_faction4) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Faction template id used by creatures/GOs ([`creature_template`](creature_template.md).faction).
- <a id="f-build"></a>**`build`** - Primary Key. Client build targeting.
- <a id="f-faction_id"></a>**`faction_id`** - Link to [`faction`](faction.md) reputation group (if any).
- <a id="f-faction_flags"></a>**`faction_flags`** - Behaviour flags (`FACTION_TEMPLATE_*`): call-for-help response/flee, enemy and friend search/broadcast priorities, assist players, attack PvP-active players.
- <a id="f-our_mask"></a>**`our_mask`** - Faction team mask this template belongs to (see `FactionMasks`).
- <a id="f-friendly_mask"></a>**`friendly_mask`** - Team masks this faction is friendly toward.
- <a id="f-hostile_mask"></a>**`hostile_mask`** - Team masks this faction is hostile toward.
- <a id="f-enemy_faction1"></a>**`enemy_faction1`** - Explicit hostile faction templates.
- <a id="f-enemy_faction2"></a>**`enemy_faction2`** - Explicit hostile faction templates.
- <a id="f-enemy_faction3"></a>**`enemy_faction3`** - Explicit hostile faction templates.
- <a id="f-enemy_faction4"></a>**`enemy_faction4`** - Explicit hostile faction templates.
- <a id="f-friend_faction1"></a>**`friend_faction1`** - Explicit friendly faction templates.
- <a id="f-friend_faction2"></a>**`friend_faction2`** - Explicit friendly faction templates.
- <a id="f-friend_faction3"></a>**`friend_faction3`** - Explicit friendly faction templates.
- <a id="f-friend_faction4"></a>**`friend_faction4`** - Explicit friendly faction templates.
