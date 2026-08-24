# areatrigger_tavern Table

Defines area triggers that act as inns/taverns. Players gain rested XP and can log out instantly while in these zones.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`name`](#f-name) | text |  | YES |  |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Areatrigger ID from [`areatrigger_template`](areatrigger_template.md).entry.
- <a id="f-name"></a>**`name`** - Name of the inn. Not used by the core - purely descriptive.
- <a id="f-patch_min"></a>**`patch_min`** - Minimum content patch in which this inn is active. Patch values start from 0 (1.2.4) up to 10 (1.12.1).
