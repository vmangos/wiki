# item_required_target Table

Defines targets required for quest items (e.g., "use this on that creature").

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO |  |  |
| [`type`](#f-type) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`target_entry`](#f-target_entry) | mediumint(8) unsigned | PRI | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Item ID ([`item_template`](item_template.md).entry).
- <a id="f-type"></a>**`type`** - Target type: `0` creature, `1` game object.
- <a id="f-target_entry"></a>**`target_entry`** - Target entry ID. (see [`creature_template`](creature_template.md).entry or [`gameobject_template`](gameobject_template.md).entry)
