# game_weather Table

Defines weather patterns for zones by season.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`zone`](#f-zone) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`spring_rain_chance`](#f-spring_rain_chance) | tinyint(3) unsigned |  | NO | 25 |  |
| [`spring_snow_chance`](#f-spring_snow_chance) | tinyint(3) unsigned |  | NO | 25 |  |
| [`spring_storm_chance`](#f-spring_storm_chance) | tinyint(3) unsigned |  | NO | 25 |  |
| [`summer_rain_chance`](#f-summer_rain_chance) | tinyint(3) unsigned |  | NO | 25 |  |
| [`summer_snow_chance`](#f-summer_snow_chance) | tinyint(3) unsigned |  | NO | 25 |  |
| [`summer_storm_chance`](#f-summer_storm_chance) | tinyint(3) unsigned |  | NO | 25 |  |
| [`fall_rain_chance`](#f-fall_rain_chance) | tinyint(3) unsigned |  | NO | 25 |  |
| [`fall_snow_chance`](#f-fall_snow_chance) | tinyint(3) unsigned |  | NO | 25 |  |
| [`fall_storm_chance`](#f-fall_storm_chance) | tinyint(3) unsigned |  | NO | 25 |  |
| [`winter_rain_chance`](#f-winter_rain_chance) | tinyint(3) unsigned |  | NO | 25 |  |
| [`winter_snow_chance`](#f-winter_snow_chance) | tinyint(3) unsigned |  | NO | 25 |  |
| [`winter_storm_chance`](#f-winter_storm_chance) | tinyint(3) unsigned |  | NO | 25 |  |

---

## Field Breakdown

- <a id="f-zone"></a>**`zone`** - Primary Key. Zone id these chances apply to. (see `AreaTable.dbc`)
- <a id="f-spring_rain_chance"></a>**`spring_rain_chance`** - Chance of rain in spring (0-100).
- <a id="f-spring_snow_chance"></a>**`spring_snow_chance`** - Chance of snow in spring.
- <a id="f-spring_storm_chance"></a>**`spring_storm_chance`** - Chance of storm in spring.
- <a id="f-summer_rain_chance"></a>**`summer_rain_chance`** - Rain chance in summer (%).
- <a id="f-summer_snow_chance"></a>**`summer_snow_chance`** - Snow chance in summer (%).
- <a id="f-summer_storm_chance"></a>**`summer_storm_chance`** - Storm chance in summer (%).
- <a id="f-fall_rain_chance"></a>**`fall_rain_chance`** - Rain chance in fall (%).
- <a id="f-fall_snow_chance"></a>**`fall_snow_chance`** - Snow chance in fall (%).
- <a id="f-fall_storm_chance"></a>**`fall_storm_chance`** - Storm chance in fall (%).
- <a id="f-winter_rain_chance"></a>**`winter_rain_chance`** - Rain chance in winter (%).
- <a id="f-winter_snow_chance"></a>**`winter_snow_chance`** - Snow chance in winter (%).
- <a id="f-winter_storm_chance"></a>**`winter_storm_chance`** - Storm chance in winter (%).
