# spell_check Table

Internal spell validation table - lists spells whose properties are relied on in code (`Code`), so `.debug spellcheck` can verify them against the client data.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`spellid`](#f-spellid) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`SpellFamilyName`](#f-SpellFamilyName) | smallint(5) | PRI | NO | -1 |  |
| [`SpellFamilyMask`](#f-SpellFamilyMask) | bigint(30) | PRI | NO | -1 |  |
| [`SpellIcon`](#f-SpellIcon) | int(10) | PRI | NO | -1 |  |
| [`SpellVisual`](#f-SpellVisual) | int(10) | PRI | NO | -1 |  |
| [`SpellCategory`](#f-SpellCategory) | int(10) | PRI | NO | -1 |  |
| [`EffectType`](#f-EffectType) | int(10) |  | NO | -1 |  |
| [`EffectAura`](#f-EffectAura) | int(10) |  | NO | -1 |  |
| [`EffectIdx`](#f-EffectIdx) | tinyint(3) |  | NO | -1 |  |
| [`Name`](#f-Name) | varchar(40) |  | NO | '' |  |
| [`Code`](#f-Code) | varchar(40) | PRI | NO | '' |  |

---

## Field Breakdown

- <a id="f-spellid"></a>**`spellid`** - Primary Key. Spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-SpellFamilyName"></a>**`SpellFamilyName`** - Family name.
- <a id="f-SpellFamilyMask"></a>**`SpellFamilyMask`** - Family mask.
- <a id="f-SpellIcon"></a>**`SpellIcon`** - Icon ID.
- <a id="f-SpellVisual"></a>**`SpellVisual`** - Visual ID.
- <a id="f-SpellCategory"></a>**`SpellCategory`** - Category.
- <a id="f-EffectType"></a>**`EffectType`** - Effect type.
- <a id="f-EffectAura"></a>**`EffectAura`** - Aura type.
- <a id="f-EffectIdx"></a>**`EffectIdx`** - Effect index.
- <a id="f-Name"></a>**`Name`** - Internal name.
- <a id="f-Code"></a>**`Code`** - Primary Key. Internal code.
