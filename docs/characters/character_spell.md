# character_spell Table

Spells learned by the character.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`spell`](#f-spell) | int(11) unsigned | PRI | NO | 0 |  |
| [`active`](#f-active) | tinyint(3) unsigned |  | NO | 1 |  |
| [`disabled`](#f-disabled) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-spell"></a>**`spell`** - Primary Key. Learned spell id.
- <a id="f-active"></a>**`active`** - `1` = spell shown as known in the spell book / usable on action bars;
  within a rank chain only the highest learned rank stays active (lower ranks are flipped off on supersede).
- <a id="f-disabled"></a>**`disabled`** - `1` = non-talent spell that was unlearned while it was a dependent/higher
  rank of a removed spell; the row is kept so re-training the base spell recursively re-enables these ranks.
  Disabled spells fail `HasSpell`. Talent spells are never marked disabled - they are removed outright.
