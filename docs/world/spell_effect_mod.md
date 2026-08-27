# spell_effect_mod Table

Overrides spell effect parameters (e.g., damage, radius, target) for custom tuning.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`Id`](#f-Id) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`EffectIndex`](#f-EffectIndex) | int(3) unsigned | PRI | NO | 0 |  |
| [`Effect`](#f-Effect) | int(3) |  | NO | -1 |  |
| [`EffectDieSides`](#f-EffectDieSides) | int(10) |  | NO | -1 |  |
| [`EffectBaseDice`](#f-EffectBaseDice) | int(10) |  | NO | -1 |  |
| [`EffectDicePerLevel`](#f-EffectDicePerLevel) | float |  | NO | -1 |  |
| [`EffectRealPointsPerLevel`](#f-EffectRealPointsPerLevel) | float |  | NO | -1 |  |
| [`EffectBasePoints`](#f-EffectBasePoints) | int(10) |  | NO | -1 |  |
| [`EffectAmplitude`](#f-EffectAmplitude) | int(10) |  | NO | -1 |  |
| [`EffectPointsPerComboPoint`](#f-EffectPointsPerComboPoint) | float |  | NO | -1 |  |
| [`EffectChainTarget`](#f-EffectChainTarget) | int(10) |  | NO | -1 |  |
| [`EffectMultipleValue`](#f-EffectMultipleValue) | float |  | NO | -1 |  |
| [`EffectMechanic`](#f-EffectMechanic) | int(10) |  | NO | -1 |  |
| [`EffectImplicitTargetA`](#f-EffectImplicitTargetA) | int(10) |  | NO | -1 |  |
| [`EffectImplicitTargetB`](#f-EffectImplicitTargetB) | int(10) |  | NO | -1 |  |
| [`EffectRadiusIndex`](#f-EffectRadiusIndex) | int(10) |  | NO | -1 |  |
| [`EffectApplyAuraName`](#f-EffectApplyAuraName) | int(10) |  | NO | -1 |  |
| [`EffectItemType`](#f-EffectItemType) | bigint(20) |  | NO | -1 |  |
| [`EffectMiscValue`](#f-EffectMiscValue) | int(10) |  | NO | -1 |  |
| [`EffectTriggerSpell`](#f-EffectTriggerSpell) | int(10) |  | NO | -1 |  |
| [`Comment`](#f-Comment) | varchar(255) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-Id"></a>**`Id`** - Primary Key. Spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-EffectIndex"></a>**`EffectIndex`** - Primary Key. Which effect slot (0-2) the row modifies.
- <a id="f-Effect"></a>**`Effect`** - Replacement effect type.
- <a id="f-EffectDieSides"></a>**`EffectDieSides`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectBaseDice"></a>**`EffectBaseDice`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectDicePerLevel"></a>**`EffectDicePerLevel`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectRealPointsPerLevel"></a>**`EffectRealPointsPerLevel`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectBasePoints"></a>**`EffectBasePoints`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectAmplitude"></a>**`EffectAmplitude`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectPointsPerComboPoint"></a>**`EffectPointsPerComboPoint`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectChainTarget"></a>**`EffectChainTarget`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectMultipleValue"></a>**`EffectMultipleValue`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectMechanic"></a>**`EffectMechanic`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectImplicitTargetA"></a>**`EffectImplicitTargetA`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectImplicitTargetB"></a>**`EffectImplicitTargetB`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectRadiusIndex"></a>**`EffectRadiusIndex`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectApplyAuraName"></a>**`EffectApplyAuraName`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectItemType"></a>**`EffectItemType`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectMiscValue"></a>**`EffectMiscValue`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-EffectTriggerSpell"></a>**`EffectTriggerSpell`** - Override for the same-named `effect` template field; only provided values replace client data.
- <a id="f-Comment"></a>**`Comment`** - Human note.
