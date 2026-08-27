# pool_template Table

Defines spawn pools - groups of spawns that collectively follow a spawn limit.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`max_limit`](#f-max_limit) | int(10) unsigned |  | NO | 0 |  |
| [`description`](#f-description) | varchar(255) |  | NO |  |  |
| [`flags`](#f-flags) | int(11) unsigned |  | NO | 0 |  |
| [`instance`](#f-instance) | mediumint(8) |  | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned | PRI | NO | 10 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Pool ID.
- <a id="f-max_limit"></a>**`max_limit`** - Maximum number of active spawns from this pool at once.
- <a id="f-description"></a>**`description`** - Comment.
- <a id="f-flags"></a>**`flags`** - Pool flags.
- <a id="f-instance"></a>**`instance`** - Continent-instance region id used only with the `ContinentsInstanciate` config enabled (0 = shared/world); ignored for instanced (dungeon) maps.
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
