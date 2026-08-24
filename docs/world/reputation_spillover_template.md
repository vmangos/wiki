# reputation_spillover_template Table

Defines spillover reputation - gaining reputation with one faction also grants partial reputation to others.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`faction`](#f-faction) | smallint(6) unsigned | PRI | NO | 0 |  |
| [`faction1`](#f-faction1) | smallint(6) unsigned |  | NO | 0 |  |
| [`rate_1`](#f-rate_1) | float |  | NO | 0 |  |
| [`rank_1`](#f-rank_1) | tinyint(3) unsigned |  | NO | 0 |  |
| [`faction2`](#f-faction2) | smallint(6) unsigned |  | NO | 0 |  |
| [`rate_2`](#f-rate_2) | float |  | NO | 0 |  |
| [`rank_2`](#f-rank_2) | tinyint(3) unsigned |  | NO | 0 |  |
| [`faction3`](#f-faction3) | smallint(6) unsigned |  | NO | 0 |  |
| [`rate_3`](#f-rate_3) | float |  | NO | 0 |  |
| [`rank_3`](#f-rank_3) | tinyint(3) unsigned |  | NO | 0 |  |
| [`faction4`](#f-faction4) | smallint(6) unsigned |  | NO | 0 |  |
| [`rate_4`](#f-rate_4) | float |  | NO | 0 |  |
| [`rank_4`](#f-rank_4) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-faction"></a>**`faction`** - Part of the primary key. Child faction whose gains spill over ([`faction`](faction.md).id).
- <a id="f-faction1"></a>**`faction1`** - Up to four parent factions receiving spillover ([`faction`](faction.md).id).
- <a id="f-rate_1"></a>**`rate_1`** - Multiplier applied to rep gained with `faction` and passed on to parent N (e.g. `0.25` = 25%).
- <a id="f-rank_1"></a>**`rank_1`** - Spillover applies only while player's standing toward parent N is at or below this rank.
- <a id="f-faction2"></a>**`faction2`** - Up to four parent factions receiving spillover ([`faction`](faction.md).id).
- <a id="f-rate_2"></a>**`rate_2`** - Multiplier applied to rep gained with `faction` and passed on to parent N (e.g. `0.25` = 25%).
- <a id="f-rank_2"></a>**`rank_2`** - Spillover applies only while player's standing toward parent N is at or below this rank.
- <a id="f-faction3"></a>**`faction3`** - Up to four parent factions receiving spillover ([`faction`](faction.md).id).
- <a id="f-rate_3"></a>**`rate_3`** - Multiplier applied to rep gained with `faction` and passed on to parent N (e.g. `0.25` = 25%).
- <a id="f-rank_3"></a>**`rank_3`** - Spillover applies only while player's standing toward parent N is at or below this rank.
- <a id="f-faction4"></a>**`faction4`** - Up to four parent factions receiving spillover ([`faction`](faction.md).id).
- <a id="f-rate_4"></a>**`rate_4`** - Multiplier applied to rep gained with `faction` and passed on to parent N (e.g. `0.25` = 25%).
- <a id="f-rank_4"></a>**`rank_4`** - Spillover applies only while player's standing toward parent N is at or below this rank.

