# character_instance Table

Instance binds of a character (which dungeon/raid saves they belong to).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`instance`](#f-instance) | int(11) unsigned | PRI | NO | 0 |  |
| [`permanent`](#f-permanent) | tinyint(1) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Part of the primary key. Character bound to the instance ([`characters`](characters.md).guid).
- <a id="f-instance"></a>**`instance`** - Part of the primary key. Save id ([`instance`](instance.md).id).
- <a id="f-permanent"></a>**`permanent`** - 1 = real raid/dungeon bind; 0 = temporary (e.g. solo-visit) binding.
