# instance_custom_counters Table

Generic counters instance scripts increment during progression (used for statistics).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`index`](#f-index) | int(10) unsigned | PRI | NO |  |  |
| [`count`](#f-count) | int(10) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-index"></a>**`index`** - Primary Key. index as defined in InstanceStatistics.h
- <a id="f-count"></a>**`count`** - counter
