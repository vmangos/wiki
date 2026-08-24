# spell_mod Table

Overrides various spell attributes - proc chance, cooldown, duration, casting time, etc.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`Id`](#f-Id) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`procChance`](#f-procChance) | int(11) |  | YES | -1 |  |
| [`procFlags`](#f-procFlags) | int(11) |  | YES | -1 |  |
| [`procCharges`](#f-procCharges) | int(11) |  | YES | -1 |  |
| [`DurationIndex`](#f-DurationIndex) | int(11) |  | YES | -1 |  |
| [`Category`](#f-Category) | int(11) |  | YES | -1 |  |
| [`CastingTimeIndex`](#f-CastingTimeIndex) | int(11) |  | YES | -1 |  |
| [`StackAmount`](#f-StackAmount) | int(11) |  | YES | -1 |  |
| [`SpellIconID`](#f-SpellIconID) | int(11) |  | YES | -1 |  |
| [`activeIconID`](#f-activeIconID) | int(11) |  | YES | -1 |  |
| [`manaCost`](#f-manaCost) | int(11) |  | YES | -1 |  |
| [`Attributes`](#f-Attributes) | int(11) |  | YES | -1 |  |
| [`AttributesEx`](#f-AttributesEx) | int(11) |  | YES | -1 |  |
| [`AttributesEx2`](#f-AttributesEx2) | int(11) |  | YES | -1 |  |
| [`AttributesEx3`](#f-AttributesEx3) | int(11) |  | YES | -1 |  |
| [`AttributesEx4`](#f-AttributesEx4) | int(11) |  | YES | -1 |  |
| [`Custom`](#f-Custom) | int(11) |  | YES | 0 |  |
| [`InterruptFlags`](#f-InterruptFlags) | int(11) |  | YES | -1 |  |
| [`AuraInterruptFlags`](#f-AuraInterruptFlags) | int(11) |  | YES | -1 |  |
| [`ChannelInterruptFlags`](#f-ChannelInterruptFlags) | int(11) |  | YES | -1 |  |
| [`Dispel`](#f-Dispel) | int(10) |  | NO | -1 |  |
| [`Stances`](#f-Stances) | int(11) |  | YES | -1 |  |
| [`StancesNot`](#f-StancesNot) | int(11) |  | YES | -1 |  |
| [`SpellVisual`](#f-SpellVisual) | int(11) |  | YES | -1 |  |
| [`ManaCostPercentage`](#f-ManaCostPercentage) | int(11) |  | YES | -1 |  |
| [`StartRecoveryCategory`](#f-StartRecoveryCategory) | int(11) |  | YES | -1 |  |
| [`StartRecoveryTime`](#f-StartRecoveryTime) | int(11) |  | YES | -1 |  |
| [`MaxAffectedTargets`](#f-MaxAffectedTargets) | int(11) |  | YES | -1 |  |
| [`MaxTargetLevel`](#f-MaxTargetLevel) | int(11) |  | YES | -1 |  |
| [`DmgClass`](#f-DmgClass) | int(11) |  | YES | -1 |  |
| [`rangeIndex`](#f-rangeIndex) | int(11) |  | YES | -1 |  |
| [`RecoveryTime`](#f-RecoveryTime) | int(11) |  | NO | -1 |  |
| [`CategoryRecoveryTime`](#f-CategoryRecoveryTime) | int(11) |  | NO | -1 |  |
| [`SpellFamilyName`](#f-SpellFamilyName) | int(11) |  | NO | -1 |  |
| [`SpellFamilyFlags`](#f-SpellFamilyFlags) | bigint(20) unsigned |  | YES | 0 |  |
| [`Mechanic`](#f-Mechanic) | int(2) |  | YES | -1 |  |
| [`EquippedItemClass`](#f-EquippedItemClass) | int(2) |  | YES | -1 |  |
| [`Comment`](#f-Comment) | varchar(255) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-Id"></a>**`Id`** - Primary Key. Spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-procChance"></a>**`procChance`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-procFlags"></a>**`procFlags`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-procCharges"></a>**`procCharges`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-DurationIndex"></a>**`DurationIndex`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-Category"></a>**`Category`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-CastingTimeIndex"></a>**`CastingTimeIndex`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-StackAmount"></a>**`StackAmount`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-SpellIconID"></a>**`SpellIconID`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-activeIconID"></a>**`activeIconID`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-manaCost"></a>**`manaCost`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-Attributes"></a>**`Attributes`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-AttributesEx"></a>**`AttributesEx`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-AttributesEx2"></a>**`AttributesEx2`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-AttributesEx3"></a>**`AttributesEx3`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-AttributesEx4"></a>**`AttributesEx4`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-Custom"></a>**`Custom`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-InterruptFlags"></a>**`InterruptFlags`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-AuraInterruptFlags"></a>**`AuraInterruptFlags`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-ChannelInterruptFlags"></a>**`ChannelInterruptFlags`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-Dispel"></a>**`Dispel`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-Stances"></a>**`Stances`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-StancesNot"></a>**`StancesNot`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-SpellVisual"></a>**`SpellVisual`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-ManaCostPercentage"></a>**`ManaCostPercentage`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-StartRecoveryCategory"></a>**`StartRecoveryCategory`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-StartRecoveryTime"></a>**`StartRecoveryTime`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-MaxAffectedTargets"></a>**`MaxAffectedTargets`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-MaxTargetLevel"></a>**`MaxTargetLevel`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-DmgClass"></a>**`DmgClass`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-rangeIndex"></a>**`rangeIndex`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-RecoveryTime"></a>**`RecoveryTime`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-CategoryRecoveryTime"></a>**`CategoryRecoveryTime`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-SpellFamilyName"></a>**`SpellFamilyName`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-SpellFamilyFlags"></a>**`SpellFamilyFlags`** - Override for the same-named `spell` template field; only provided values replace client data.
- <a id="f-Mechanic"></a>**`Mechanic`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-EquippedItemClass"></a>**`EquippedItemClass`** - Override for the same-named `Spell.dbc` field of spell `entry`; only provided values replace client data.
- <a id="f-Comment"></a>**`Comment`** - Human note; not read by the core.
