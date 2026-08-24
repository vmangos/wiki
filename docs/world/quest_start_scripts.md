# quest_start_scripts Table

Scripts executed when a quest is accepted. Uses the [generic script system](../DB-Script-Tables.md).

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| `id` | int(10) unsigned |  | NO | 0 |  |
| `delay` | int(10) unsigned |  | NO | 0 |  |
| `priority` | tinyint(3) unsigned |  | NO | 0 |  |
| [`command`](../DB-Script-Tables.md) | tinyint(3) unsigned |  | NO | 0 |  |
| `datalong` | int(10) unsigned |  | NO | 0 |  |
| `datalong2` | int(10) unsigned |  | NO | 0 |  |
| `datalong3` | int(10) unsigned |  | NO | 0 |  |
| `datalong4` | int(10) unsigned |  | NO | 0 |  |
| `target_param1` | int(10) unsigned |  | NO | 0 |  |
| `target_param2` | int(10) unsigned |  | NO | 0 |  |
| `target_type` | tinyint(3) unsigned |  | NO | 0 |  |
| `data_flags` | tinyint(3) unsigned |  | NO | 0 |  |
| `dataint` | int(11) |  | NO | 0 |  |
| `dataint2` | int(11) |  | NO | 0 |  |
| `dataint3` | int(11) |  | NO | 0 |  |
| `dataint4` | int(11) |  | NO | 0 |  |
| `x` | float |  | NO | 0 |  |
| `y` | float |  | NO | 0 |  |
| `z` | float |  | NO | 0 |  |
| `o` | float |  | NO | 0 |  |
| `condition_id` | mediumint(8) unsigned |  | NO | 0 |  |
| `comments` | varchar(255) |  | NO |  |  |
