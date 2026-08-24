# player_premade_item Table

Defines items granted to premade characters (used for testing or templates).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | int(10) unsigned |  | NO |  |  |
| [`item`](#f-item) | int(10) unsigned |  | NO |  |  |
| [`enchant`](#f-enchant) | int(10) unsigned |  | NO | 0 |  |
| [`team`](#f-team) | int(10) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Premade template ID.
- <a id="f-item"></a>**`item`** - Item ID ([`item_template`](item_template.md).entry).
- <a id="f-enchant"></a>**`enchant`** - Enchantment ID.
- <a id="f-team"></a>**`team`** - Faction restriction: `0` both, `469` Alliance, `67` Horde (Team enum).
