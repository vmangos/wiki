# spell_template Table

Defines spell data - the primary table for all spells in the world database.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`build`](#f-build) | smallint(4) unsigned | PRI | NO | 5875 |  |
| [`school`](#f-school) | int(4) unsigned |  | NO | 0 |  |
| [`category`](#f-category) | int(4) unsigned |  | NO | 0 |  |
| [`castUI`](#f-castUI) | int(4) unsigned |  | NO | 0 |  |
| [`dispel`](#f-dispel) | int(4) unsigned |  | NO | 0 |  |
| [`mechanic`](#f-mechanic) | int(4) unsigned |  | NO | 0 |  |
| [`attributes`](#f-attributes) | int(4) unsigned |  | NO | 0 |  |
| [`attributesEx`](#f-attributesEx) | int(4) unsigned |  | NO | 0 |  |
| [`attributesEx2`](#f-attributesEx2) | int(4) unsigned |  | NO | 0 |  |
| [`attributesEx3`](#f-attributesEx3) | int(4) unsigned |  | NO | 0 |  |
| [`attributesEx4`](#f-attributesEx4) | int(4) unsigned |  | NO | 0 |  |
| [`stances`](#f-stances) | int(4) unsigned |  | NO | 0 |  |
| [`stancesNot`](#f-stancesNot) | int(4) unsigned |  | NO | 0 |  |
| [`targets`](#f-targets) | int(4) unsigned |  | NO | 0 |  |
| [`targetCreatureType`](#f-targetCreatureType) | int(4) unsigned |  | NO | 0 |  |
| [`requiresSpellFocus`](#f-requiresSpellFocus) | int(4) unsigned |  | NO | 0 |  |
| [`casterAuraState`](#f-casterAuraState) | int(4) unsigned |  | NO | 0 |  |
| [`targetAuraState`](#f-targetAuraState) | int(4) unsigned |  | NO | 0 |  |
| [`castingTimeIndex`](#f-castingTimeIndex) | int(4) unsigned |  | NO | 0 |  |
| [`recoveryTime`](#f-recoveryTime) | int(4) unsigned |  | NO | 0 |  |
| [`categoryRecoveryTime`](#f-categoryRecoveryTime) | int(4) unsigned |  | NO | 0 |  |
| [`interruptFlags`](#f-interruptFlags) | int(4) unsigned |  | NO | 0 |  |
| [`auraInterruptFlags`](#f-auraInterruptFlags) | int(4) unsigned |  | NO | 0 |  |
| [`channelInterruptFlags`](#f-channelInterruptFlags) | int(4) unsigned |  | NO | 0 |  |
| [`procFlags`](#f-procFlags) | int(4) unsigned |  | NO | 0 |  |
| [`procChance`](#f-procChance) | int(4) unsigned |  | NO | 0 |  |
| [`procCharges`](#f-procCharges) | int(4) unsigned |  | NO | 0 |  |
| [`maxLevel`](#f-maxLevel) | int(4) unsigned |  | NO | 0 |  |
| [`baseLevel`](#f-baseLevel) | int(4) unsigned |  | NO | 0 |  |
| [`spellLevel`](#f-spellLevel) | int(4) unsigned |  | NO | 0 |  |
| [`durationIndex`](#f-durationIndex) | int(4) unsigned |  | NO | 0 |  |
| [`powerType`](#f-powerType) | int(4) unsigned |  | NO | 0 |  |
| [`manaCost`](#f-manaCost) | int(4) unsigned |  | NO | 0 |  |
| [`manCostPerLevel`](#f-manCostPerLevel) | int(4) unsigned |  | NO | 0 |  |
| [`manaPerSecond`](#f-manaPerSecond) | int(4) unsigned |  | NO | 0 |  |
| [`manaPerSecondPerLevel`](#f-manaPerSecondPerLevel) | int(4) unsigned |  | NO | 0 |  |
| [`rangeIndex`](#f-rangeIndex) | int(4) unsigned |  | NO | 0 |  |
| [`speed`](#f-speed) | float |  | NO | 0 |  |
| [`modelNextSpell`](#f-modelNextSpell) | int(4) unsigned |  | NO | 0 |  |
| [`stackAmount`](#f-stackAmount) | int(4) unsigned |  | NO | 0 |  |
| [`totem1`](#f-totem1) | int(4) unsigned |  | NO | 0 |  |
| [`totem2`](#f-totem2) | int(4) unsigned |  | NO | 0 |  |
| [`reagent1`](#f-reagent1) | int(4) |  | NO | 0 |  |
| [`reagent2`](#f-reagent2) | int(4) |  | NO | 0 |  |
| [`reagent3`](#f-reagent3) | int(4) |  | NO | 0 |  |
| [`reagent4`](#f-reagent4) | int(4) |  | NO | 0 |  |
| [`reagent5`](#f-reagent5) | int(4) |  | NO | 0 |  |
| [`reagent6`](#f-reagent6) | int(4) |  | NO | 0 |  |
| [`reagent7`](#f-reagent7) | int(4) |  | NO | 0 |  |
| [`reagent8`](#f-reagent8) | int(4) |  | NO | 0 |  |
| [`reagentCount1`](#f-reagentCount1) | int(4) unsigned |  | NO | 0 |  |
| [`reagentCount2`](#f-reagentCount2) | int(4) unsigned |  | NO | 0 |  |
| [`reagentCount3`](#f-reagentCount3) | int(4) unsigned |  | NO | 0 |  |
| [`reagentCount4`](#f-reagentCount4) | int(4) unsigned |  | NO | 0 |  |
| [`reagentCount5`](#f-reagentCount5) | int(4) unsigned |  | NO | 0 |  |
| [`reagentCount6`](#f-reagentCount6) | int(4) unsigned |  | NO | 0 |  |
| [`reagentCount7`](#f-reagentCount7) | int(4) unsigned |  | NO | 0 |  |
| [`reagentCount8`](#f-reagentCount8) | int(4) unsigned |  | NO | 0 |  |
| [`equippedItemClass`](#f-equippedItemClass) | int(4) |  | NO | 0 |  |
| [`equippedItemSubClassMask`](#f-equippedItemSubClassMask) | int(4) |  | NO | 0 |  |
| [`equippedItemInventoryTypeMask`](#f-equippedItemInventoryTypeMask) | int(4) |  | NO | 0 |  |
| [`effect1`](#f-effect1) | int(4) unsigned |  | NO | 0 |  |
| [`effect2`](#f-effect2) | int(4) unsigned |  | NO | 0 |  |
| [`effect3`](#f-effect3) | int(4) unsigned |  | NO | 0 |  |
| [`effectDieSides1`](#f-effectDieSides1) | int(4) |  | NO | 0 |  |
| [`effectDieSides2`](#f-effectDieSides2) | int(4) |  | NO | 0 |  |
| [`effectDieSides3`](#f-effectDieSides3) | int(4) |  | NO | 0 |  |
| [`effectBaseDice1`](#f-effectBaseDice1) | int(4) unsigned |  | NO | 0 |  |
| [`effectBaseDice2`](#f-effectBaseDice2) | int(4) unsigned |  | NO | 0 |  |
| [`effectBaseDice3`](#f-effectBaseDice3) | int(4) unsigned |  | NO | 0 |  |
| [`effectDicePerLevel1`](#f-effectDicePerLevel1) | float |  | NO | 0 |  |
| [`effectDicePerLevel2`](#f-effectDicePerLevel2) | float |  | NO | 0 |  |
| [`effectDicePerLevel3`](#f-effectDicePerLevel3) | float |  | NO | 0 |  |
| [`effectRealPointsPerLevel1`](#f-effectRealPointsPerLevel1) | float |  | NO | 0 |  |
| [`effectRealPointsPerLevel2`](#f-effectRealPointsPerLevel2) | float |  | NO | 0 |  |
| [`effectRealPointsPerLevel3`](#f-effectRealPointsPerLevel3) | float |  | NO | 0 |  |
| [`effectBasePoints1`](#f-effectBasePoints1) | int(4) |  | NO | 0 |  |
| [`effectBasePoints2`](#f-effectBasePoints2) | int(4) |  | NO | 0 |  |
| [`effectBasePoints3`](#f-effectBasePoints3) | int(4) |  | NO | 0 |  |
| [`effectBonusCoefficient1`](#f-effectBonusCoefficient1) | float |  | NO | -1 |  |
| [`effectBonusCoefficient2`](#f-effectBonusCoefficient2) | float |  | NO | -1 |  |
| [`effectBonusCoefficient3`](#f-effectBonusCoefficient3) | float |  | NO | -1 |  |
| [`effectMechanic1`](#f-effectMechanic1) | int(4) unsigned |  | NO | 0 |  |
| [`effectMechanic2`](#f-effectMechanic2) | int(4) unsigned |  | NO | 0 |  |
| [`effectMechanic3`](#f-effectMechanic3) | int(4) unsigned |  | NO | 0 |  |
| [`effectImplicitTargetA1`](#f-effectImplicitTargetA1) | int(4) unsigned |  | NO | 0 |  |
| [`effectImplicitTargetA2`](#f-effectImplicitTargetA2) | int(4) unsigned |  | NO | 0 |  |
| [`effectImplicitTargetA3`](#f-effectImplicitTargetA3) | int(4) unsigned |  | NO | 0 |  |
| [`effectImplicitTargetB1`](#f-effectImplicitTargetB1) | int(4) unsigned |  | NO | 0 |  |
| [`effectImplicitTargetB2`](#f-effectImplicitTargetB2) | int(4) unsigned |  | NO | 0 |  |
| [`effectImplicitTargetB3`](#f-effectImplicitTargetB3) | int(4) unsigned |  | NO | 0 |  |
| [`effectRadiusIndex1`](#f-effectRadiusIndex1) | int(4) unsigned |  | NO | 0 |  |
| [`effectRadiusIndex2`](#f-effectRadiusIndex2) | int(4) unsigned |  | NO | 0 |  |
| [`effectRadiusIndex3`](#f-effectRadiusIndex3) | int(4) unsigned |  | NO | 0 |  |
| [`effectApplyAuraName1`](#f-effectApplyAuraName1) | int(4) unsigned |  | NO | 0 |  |
| [`effectApplyAuraName2`](#f-effectApplyAuraName2) | int(4) unsigned |  | NO | 0 |  |
| [`effectApplyAuraName3`](#f-effectApplyAuraName3) | int(4) unsigned |  | NO | 0 |  |
| [`effectAmplitude1`](#f-effectAmplitude1) | int(4) unsigned |  | NO | 0 |  |
| [`effectAmplitude2`](#f-effectAmplitude2) | int(4) unsigned |  | NO | 0 |  |
| [`effectAmplitude3`](#f-effectAmplitude3) | int(4) unsigned |  | NO | 0 |  |
| [`effectMultipleValue1`](#f-effectMultipleValue1) | float |  | NO | 0 |  |
| [`effectMultipleValue2`](#f-effectMultipleValue2) | float |  | NO | 0 |  |
| [`effectMultipleValue3`](#f-effectMultipleValue3) | float |  | NO | 0 |  |
| [`effectChainTarget1`](#f-effectChainTarget1) | int(4) unsigned |  | NO | 0 |  |
| [`effectChainTarget2`](#f-effectChainTarget2) | int(4) unsigned |  | NO | 0 |  |
| [`effectChainTarget3`](#f-effectChainTarget3) | int(4) unsigned |  | NO | 0 |  |
| [`effectItemType1`](#f-effectItemType1) | bigint(20) unsigned |  | NO | 0 |  |
| [`effectItemType2`](#f-effectItemType2) | bigint(20) unsigned |  | NO | 0 |  |
| [`effectItemType3`](#f-effectItemType3) | bigint(20) unsigned |  | NO | 0 |  |
| [`effectMiscValue1`](#f-effectMiscValue1) | int(4) |  | NO | 0 |  |
| [`effectMiscValue2`](#f-effectMiscValue2) | int(4) |  | NO | 0 |  |
| [`effectMiscValue3`](#f-effectMiscValue3) | int(4) |  | NO | 0 |  |
| [`effectTriggerSpell1`](#f-effectTriggerSpell1) | int(4) unsigned |  | NO | 0 |  |
| [`effectTriggerSpell2`](#f-effectTriggerSpell2) | int(4) unsigned |  | NO | 0 |  |
| [`effectTriggerSpell3`](#f-effectTriggerSpell3) | int(4) unsigned |  | NO | 0 |  |
| [`effectPointsPerComboPoint1`](#f-effectPointsPerComboPoint1) | float |  | NO | 0 |  |
| [`effectPointsPerComboPoint2`](#f-effectPointsPerComboPoint2) | float |  | NO | 0 |  |
| [`effectPointsPerComboPoint3`](#f-effectPointsPerComboPoint3) | float |  | NO | 0 |  |
| [`spellVisual1`](#f-spellVisual1) | int(4) unsigned |  | NO | 0 |  |
| [`spellVisual2`](#f-spellVisual2) | int(4) unsigned |  | NO | 0 |  |
| [`spellIconId`](#f-spellIconId) | int(4) unsigned |  | NO | 0 |  |
| [`activeIconId`](#f-activeIconId) | int(4) unsigned |  | NO | 0 |  |
| [`spellPriority`](#f-spellPriority) | int(4) unsigned |  | NO | 0 |  |
| [`name`](#f-name) | varchar(256) |  | NO | '' |  |
| [`nameFlags`](#f-nameFlags) | int(4) unsigned |  | NO | 0 |  |
| [`nameSubtext`](#f-nameSubtext) | varchar(256) |  | NO | '' |  |
| [`nameSubtextFlags`](#f-nameSubtextFlags) | int(4) unsigned |  | NO | 0 |  |
| [`description`](#f-description) | varchar(1024) |  | NO | '' |  |
| [`descriptionFlags`](#f-descriptionFlags) | int(4) unsigned |  | NO | 0 |  |
| [`auraDescription`](#f-auraDescription) | varchar(512) |  | NO | '' |  |
| [`auraDescriptionFlags`](#f-auraDescriptionFlags) | int(4) unsigned |  | NO | 0 |  |
| [`manaCostPercentage`](#f-manaCostPercentage) | int(4) unsigned |  | NO | 0 |  |
| [`startRecoveryCategory`](#f-startRecoveryCategory) | int(4) unsigned |  | NO | 0 |  |
| [`startRecoveryTime`](#f-startRecoveryTime) | int(4) unsigned |  | NO | 0 |  |
| [`minTargetLevel`](#f-minTargetLevel) | int(4) unsigned |  | NO | 0 |  |
| [`maxTargetLevel`](#f-maxTargetLevel) | int(4) unsigned |  | NO | 0 |  |
| [`spellFamilyName`](#f-spellFamilyName) | int(4) unsigned |  | NO | 0 |  |
| [`spellFamilyFlags`](#f-spellFamilyFlags) | bigint(20) unsigned |  | NO | 0 |  |
| [`maxAffectedTargets`](#f-maxAffectedTargets) | int(4) unsigned |  | NO | 0 |  |
| [`dmgClass`](#f-dmgClass) | int(4) unsigned |  | NO | 0 |  |
| [`preventionType`](#f-preventionType) | int(4) unsigned |  | NO | 0 |  |
| [`stanceBarOrder`](#f-stanceBarOrder) | int(4) |  | NO | 0 |  |
| [`dmgMultiplier1`](#f-dmgMultiplier1) | float |  | NO | 0 |  |
| [`dmgMultiplier2`](#f-dmgMultiplier2) | float |  | NO | 0 |  |
| [`dmgMultiplier3`](#f-dmgMultiplier3) | float |  | NO | 0 |  |
| [`minFactionId`](#f-minFactionId) | int(4) unsigned |  | NO | 0 |  |
| [`minReputation`](#f-minReputation) | int(4) unsigned |  | NO | 0 |  |
| [`requiredAuraVision`](#f-requiredAuraVision) | int(4) unsigned |  | NO | 0 |  |
| [`customFlags`](#f-customFlags) | int(10) unsigned |  | NO | 0 |  |
| [`script_name`](#f-script_name) | varchar(64) |  | NO | '' |  |

---

## Field Breakdown

### Identity & Text

- <a id="f-entry"></a>**`entry`** - Spell ID (`Spell.dbc` id).
- <a id="f-build"></a>**`build`** - Client build this row applies to.
- <a id="f-auraDescription"></a><a id="f-description"></a><a id="f-name"></a><a id="f-nameSubtext"></a>**`name`**, **`nameSubtext`**, **`description`**, **`auraDescription`** - Display text
  (name, subtext/rank line, tooltip body, aura tooltip).
- <a id="f-auraDescriptionFlags"></a><a id="f-descriptionFlags"></a><a id="f-nameFlags"></a><a id="f-nameSubtextFlags"></a>**`nameFlags`**, **`nameSubtextFlags`**, **`descriptionFlags`**, **`auraDescriptionFlags`** -
  Broadcast-text-style flag companions for each text column (locale handling).

### Identity Extras

- <a id="f-castUI"></a>**`castUI`** - DBC passthrough column; not used by the current core loader.

### Classification

- <a id="f-school"></a>**`school`** - Base magic school: `0` physical, `1` holy, `2` fire, `3` nature,
  `4` frost, `5` shadow, `6` arcane.
- <a id="f-category"></a>**`category`** - Category id; spells sharing a category share cooldowns
  (e.g. all Hearthstone-like items).
- <a id="f-dispel"></a>**`dispel`** - Dispel type (`enum DispelType`, `SpellDefines.h`):

  | Value | Name |
  | :---: | :--- |
  | 0 | NONE |
  | 1 | MAGIC |
  | 2 | CURSE |
  | 3 | DISEASE |
  | 4 | POISON |
  | 5 | STEALTH |
  | 6 | INVISIBILITY |
  | 7 | ALL |
  | 8 | SPE_NPC_ONLY |
  | 9 | ENRAGE |
  | 10 | ZG_TICKET |
- <a id="f-mechanic"></a>**`mechanic`** - Combat mechanic granted/inflicted (`SpellDefines.h`):

  | Value | Name |
  | :---: | :--- |
  | 0 | NONE |
  | 1 | CHARM |
  | 2 | DISORIENTED |
  | 3 | DISARM |
  | 4 | DISTRACT |
  | 5 | FEAR |
  | 6 | FUMBLE |
  | 7 | ROOT |
  | 8 | PACIFY |
  | 9 | SILENCE |
  | 10 | SLEEP |
  | 11 | SNARE |
  | 12 | STUN |
  | 13 | FREEZE |
  | 14 | KNOCKOUT |
  | 15 | BLEED |
  | 16 | BANDAGE |
  | 17 | POLYMORPH |
  | 18 | BANISH |
  | 19 | SHIELD |
  | 20 | SHACKLE |
  | 21 | MOUNT |
  | 22 | PERSUADE |
  | 23 | TURN |
  | 24 | HORROR |
  | 25 | INVULNERABILITY |
  | 26 | INTERRUPT |
  | 27 | DAZE |
  | 28 | DISCOVERY |
  | 29 | IMMUNE_SHIELD |
  | 30 | SAPPED |
  | 31 | SLOW_CAST_SPEED |

### Attribute Flags

Bitmask columns; every bit is defined as `SPELL_ATTR_*` in
`src/game/Spells/SpellDefines.h`.

#### `attributes` {#f-attributes}

| Flag | Name | Notes |
| ---: | :--- | :--- |
| 0x00000001 | PROC_FAILURE_BURNS_CHARGE |  |
| 0x00000002 | USES_RANGED_SLOT | All ranged abilites have this flag |
| 0x00000004 | ON_NEXT_SWING_NO_DAMAGE |  |
| 0x00000008 | NEED_EXOTIC_AMMO | Vanilla only attribute removed in TBC |
| 0x00000010 | IS_ABILITY | Client puts 'ability' instead of 'spell' in game strings for these spells |
| 0x00000020 | IS_TRADESKILL | Trade spells, will be added by client to a sublist of profession spell |
| 0x00000040 | PASSIVE |  |
| 0x00000080 | DO_NOT_DISPLAY | Spells with this attribute are not visible in spellbook or aura bar |
| 0x00000100 | DO_NOT_LOG | This attributes controls whether spell appears in combat logs |
| 0x00000200 | HELD_ITEM_ONLY | Client automatically selects item from mainhand slot as a cast target |
| 0x00000400 | ON_NEXT_SWING |  |
| 0x00000800 | WEARER_CASTS_PROC_TRIGGER |  |
| 0x00001000 | DAYTIME_ONLY | Only useable at daytime, not set in 2.4.2 |
| 0x00002000 | NIGHT_ONLY | Only useable at night, not set in 2.4.2 |
| 0x00004000 | ONLY_INDOORS | Only useable indoors, not set in 2.4.2 |
| 0x00008000 | ONLY_OUTDOORS | Only useable outdoors |
| 0x00010000 | NOT_SHAPESHIFT | Not while shapeshifted |
| 0x00020000 | ONLY_STEALTHED | Must be in stealth |
| 0x00040000 | DO_NOT_SHEATH | Client won't hide unit weapons in sheath on cast/channel |
| 0x00080000 | SCALES_WITH_CREATURE_LEVEL | Spell damage depends on caster level |
| 0x00100000 | CANCELS_AUTO_ATTACK_COMBAT | Stop attack after use this spell (and not begin attack if use) |
| 0x00200000 | NO_ACTIVE_DEFENSE | Cannot be dodged/parried/blocked |
| 0x00400000 | TRACK_TARGET_IN_CAST_PLAYER_ONLY | SetTrackingTarget |
| 0x00800000 | ALLOW_CAST_WHILE_DEAD | Castable while dead |
| 0x01000000 | ALLOW_WHILE_MOUNTED | Castable while mounted |
| 0x02000000 | COOLDOWN_ON_EVENT | Activate and start cooldown after aura fade or remove summoned creature or go |
| 0x04000000 | AURA_IS_DEBUFF | Almost all negative spells have it |
| 0x08000000 | ALLOW_WHILE_SITTING | Castable while sitting |
| 0x10000000 | NOT_IN_COMBAT_ONLY_PEACEFUL | Cannot be used in combat |
| 0x20000000 | NO_IMMUNITIES | Unaffected by invulnerability |
| 0x40000000 | HEARTBEAT_RESIST | Chance for spell effects to break early (heartbeat resist) |
| 0x80000000 | NO_AURA_CANCEL | Positive aura can't be canceled |
| 0x80000000 | CAN_BREAK_ON_DAMAGE | Taking damage has chance to remove the aura |

#### `attributesEx` {#f-attributesEx}

| Flag | Name | Notes |
| ---: | :--- | :--- |
| 0x00000001 | EX_DISMISS_PET_FIRST | For spells without this flag client doesn't allow to summon pet if caster has a pet |
| 0x00000002 | EX_USE_ALL_MANA | Use all power (Only paladin Lay of Hands and Bunyanize) |
| 0x00000004 | EX_IS_CHANNELED |  |
| 0x00000008 | EX_NO_REDIRECTION |  |
| 0x00000010 | EX_NO_SKILL_INCREASE | Only assigned to stealth spells for some reason |
| 0x00000020 | EX_ALLOW_WHILE_STEALTHED | Does not break stealth |
| 0x00000040 | EX_IS_SELF_CHANNELED |  |
| 0x00000080 | EX_NO_REFLECTION |  |
| 0x00000100 | EX_ONLY_PEACEFUL_TARGETS | Target must not be in combat |
| 0x00000200 | EX_INITIATES_COMBAT | Enables Auto-Attack |
| 0x00000400 | EX_NO_THREAT |  |
| 0x00000800 | EX_AURA_UNIQUE |  |
| 0x00001000 | EX_FAILURE_BREAKS_STEALTH |  |
| 0x00002000 | EX_TOGGLE_FARSIGHT |  |
| 0x00004000 | EX_TRACK_TARGET_IN_CHANNEL | Client automatically forces player to face target when channeling |
| 0x00008000 | EX_IMMUNITY_PURGES_EFFECT | Remove auras on immunity |
| 0x00010000 | EX_IMMUNITY_TO_HOSTILE_AND_FRIENDLY_EFFECTS | Aura that provides immunity prevents positive effects too |
| 0x00020000 | EX_NO_AUTOCAST_AI |  |
| 0x00040000 | EX_PREVENTS_ANIM | Stun, polymorph, daze, sleep |
| 0x00080000 | EX_EXCLUDE_CASTER |  |
| 0x00100000 | EX_FINISHING_MOVE_DAMAGE | Uses combo points |
| 0x00200000 | EX_THREAT_ONLY_ON_MISS |  |
| 0x00400000 | EX_FINISHING_MOVE_DURATION | Uses combo points (in 4.x not required combo point target selected) |
| 0x00800000 | EX_IGNORE_CASTER_AND_TARGET_RESTRICTIONS | Skips all cast checks, moved to AttributesEx3 after 1.10 (100% correlation) |
| 0x01000000 | EX_SPECIAL_SKILLUP | Only fishing spells |
| 0x02000000 | EX_UNK25 | Different in vanilla |
| 0x04000000 | EX_REQUIRE_ALL_TARGETS |  |
| 0x08000000 | EX_DISCOUNT_POWER_ON_MISS | All these spells refund power on parry or deflect |
| 0x10000000 | EX_NO_AURA_ICON | Client doesn't display these spells in aura bar |
| 0x20000000 | EX_NAME_IN_CHANNEL_BAR | Spell name is displayed in cast bar instead of 'channeling' text |
| 0x40000000 | EX_COMBO_ON_BLOCK | Overpower |
| 0x80000000 | EX_CAST_WHEN_LEARNED |  |

#### `attributesEx2` {#f-attributesEx2}

| Flag | Name | Notes |
| ---: | :--- | :--- |
| 0x00000001 | ALLOW_DEAD_TARGET | Can target dead unit or corpse |
| 0x00000002 | NO_SHAPESHIFT_UI |  |
| 0x00000004 | IGNORE_LINE_OF_SIGHT |  |
| 0x00000008 | ALLOW_LOW_LEVEL_BUFF |  |
| 0x00000010 | USE_SHAPESHIFT_BAR | Client displays icon in stance bar when learned, even if not shapeshift |
| 0x00000020 | AUTO_REPEAT |  |
| 0x00000040 | CANNOT_CAST_ON_TAPPED | Target must be tapped by caster |
| 0x00000080 | DO_NOT_REPORT_SPELL_FAILURE |  |
| 0x00000100 | UNK8 | Unused |
| 0x00000200 | UNK9 | Unused |
| 0x00000400 | SPECIAL_TAMING_FLAG |  |
| 0x00000800 | NO_TARGET_PER_SECOND_COSTS |  |
| 0x00001000 | CHAIN_FROM_CASTER |  |
| 0x00002000 | ENCHANT_OWN_ITEM_ONLY |  |
| 0x00004000 | ALLOW_WHILE_INVISIBLE |  |
| 0x00008000 | ENABLE_AFTER_PARRY | Deprecated in patch 1.8 and moved to CasterAuraState |
| 0x00010000 | NO_ACTIVE_PETS |  |
| 0x00020000 | DO_NOT_RESET_COMBAT_TIMERS | Don't reset timers for melee autoattacks (swings) or ranged autoattacks (autoshoots) |
| 0x00040000 | REQ_DEAD_PET | Only Revive pet has it |
| 0x00080000 | ALLOW_WHILE_NOT_SHAPESHIFTED | Does not necessary need shapeshift (pre-3.x not have passive spells with this attribute) |
| 0x00100000 | INITIATE_COMBAT_POST_CAST | Client will send CMSG_ATTACK_SWING after SMSG_SPELL_GO |
| 0x00200000 | FAIL_ON_ALL_TARGETS_IMMUNE | For ice blocks, pala immunity buffs, priest absorb shields |
| 0x00400000 | NO_INITIAL_THREAT |  |
| 0x00800000 | PROC_COOLDOWN_ON_FAILURE |  |
| 0x01000000 | ITEM_CAST_WITH_OWNER_SKILL | NYI |
| 0x02000000 | DONT_BLOCK_MANA_REGEN |  |
| 0x04000000 | NO_SCHOOL_IMMUNITIES |  |
| 0x08000000 | IGNORE_WEAPONSKILL | NYI (only fishing has it) |
| 0x10000000 | NOT_AN_ACTION |  |
| 0x20000000 | CANT_CRIT |  |
| 0x40000000 | ACTIVE_THREAT | Caster is put in combat for 5.5 seconds on cast at enemy unit |
| 0x80000000 | RETAIN_ITEM_CAST | Food or Drink Buff (like Well Fed) |

#### `attributesEx3` {#f-attributesEx3}

| Flag | Name | Notes |
| ---: | :--- | :--- |
| 0x00000001 | PVP_ENABLING | Spell landed counts as hostile action against enemy even if it doesn't trigger combat state, propagates PvP flags |
| 0x00000002 | NO_PROC_EQUIP_REQUIREMENT |  |
| 0x00000004 | NO_CASTING_BAR_TEXT |  |
| 0x00000008 | COMPLETELY_BLOCKED | All effects prevented on block |
| 0x00000010 | NO_RES_TIMER | Corpse reclaim delay does not apply to accepting resurrection (only Rebirth has it) |
| 0x00000020 | NO_DURABILITY_LOSS |  |
| 0x00000040 | NO_AVOIDANCE | Persistent Area Aura not removed on leaving radius |
| 0x00000080 | DOT_STACKING_RULE | Create a separate (de)buff stack for each caster |
| 0x00000100 | ONLY_ON_PLAYER | Can target only players |
| 0x00000200 | NOT_A_PROC | Aura periodic trigger is not evaluated as triggered |
| 0x00000400 | REQUIRES_MAIN_HAND_WEAPON |  |
| 0x00000800 | ONLY_BATTLEGROUNDS |  |
| 0x00001000 | ONLY_ON_GHOSTS |  |
| 0x00002000 | HIDE_CHANNEL_BAR | Client will not display channeling bar |
| 0x00004000 | HIDE_IN_RAID_FILTER | Only "Honorless Target" has this flag |
| 0x00008000 | NORMAL_RANGED_ATTACK | Spells with this attribute are processed as ranged attacks in client |
| 0x00010000 | SUPPRESS_CASTER_PROCS |  |
| 0x00020000 | SUPPRESS_TARGET_PROCS |  |
| 0x00040000 | ALWAYS_HIT | Spell should always hit its target |
| 0x00080000 | INSTANT_TARGET_PROCS | Related to spell batching |
| 0x00100000 | ALLOW_AURA_WHILE_DEAD | Death persistent spells |
| 0x00200000 | ONLY_PROC_OUTDOORS |  |
| 0x00400000 | CASTING_CANCELS_AUTOREPEAT | NYI (only Shoot with Wand has it) |
| 0x00800000 | NO_DAMAGE_HISTORY | NYI |
| 0x01000000 | REQUIRES_OFFHAND_WEAPON |  |
| 0x02000000 | TREAT_AS_PERIODIC | Does not cause spell pushback |
| 0x04000000 | CAN_PROC_FROM_PROCS | Auras with this attribute can proc off procced spells (periodic triggers etc) |
| 0x08000000 | ONLY_PROC_ON_CASTER |  |
| 0x10000000 | IGNORE_CASTER_AND_TARGET_RESTRICTIONS | Skips all cast checks, moved from AttributesEx after 1.10 (100% correlation) |
| 0x20000000 | IGNORE_CASTER_MODIFIERS |  |
| 0x40000000 | DO_NOT_DISPLAY_RANGE |  |
| 0x80000000 | NOT_ON_AOE_IMMUNE |  |

#### `attributesEx4` {#f-attributesEx4}

| Flag | Name | Notes |
| ---: | :--- | :--- |
| 0x00000001 | IGNORE_RESISTANCES | From TC 3.3.5, but not present in 1.12 native DBCs. Add it with spell_mod to prevent a spell from being resisted. |
| 0x00000002 | CLASS_TRIGGER_ONLY_ON_TARGET |  |
| 0x00000004 | AURA_EXPIRES_OFFLINE | Aura continues to expire while player is offline |
| 0x00000008 | NO_HELPFUL_THREAT |  |
| 0x00000010 | NO_HARMFUL_THREAT |  |
| 0x00000020 | ALLOW_CLIENT_TARGETING | NYI |
| 0x00000040 | CANNOT_BE_STOLEN | Unused |
| 0x00000080 | CAN_CAST_WHILE_CASTING | NYI (does not seem to work client side either) |
| 0x00000100 | IGNORE_DAMAGE_TAKEN_MODIFIERS |  |
| 0x00000200 | COMBAT_FEEDBACK_WHEN_USABLE | Initially disabled / Trigger activate from event (Execute, Riposte, Deep Freeze...) |

### Stances & Target Restrictions

- <a id="f-stances"></a><a id="f-stancesNot"></a>**`stances`** / **`stancesNot`** - Shapeshift forms required / forbidden (bitmask).
- <a id="f-targets"></a>**`targets`** - Extra target mask (e.g. corpse targets).
- <a id="f-targetCreatureType"></a>**`targetCreatureType`** - Only affects creatures of this type (`CreatureTypeMask`).
- <a id="f-requiresSpellFocus"></a>**`requiresSpellFocus`** - Requires a nearby spell-focus object
  ([`gameobject_template`](gameobject_template.md) type 8 objects).
- <a id="f-casterAuraState"></a><a id="f-targetAuraState"></a>**`casterAuraState`** / **`targetAuraState`** - Caster/victim must have this aura state.

### Timers & Cooldowns

- <a id="f-castingTimeIndex"></a>**`castingTimeIndex`** - Row in `CastTime.dbc` (cast duration).
- <a id="f-recoveryTime"></a>**`recoveryTime`** - Cooldown (ms) before the same spell may be recast.
- <a id="f-categoryRecoveryTime"></a>**`categoryRecoveryTime`** - Cooldown applied to the whole `category`.
- <a id="f-auraInterruptFlags"></a><a id="f-channelInterruptFlags"></a><a id="f-interruptFlags"></a>**`interruptFlags`** / **`auraInterruptFlags`** / **`channelInterruptFlags`** -
  What breaks the cast / removes auras / stops channeling (movement, damage, ...).
- <a id="f-startRecoveryCategory"></a><a id="f-startRecoveryTime"></a>**`startRecoveryCategory`** / **`startRecoveryTime`** - Global cooldown category and time
  applied when the cast starts.
- <a id="f-maxAffectedTargets"></a>**`maxAffectedTargets`** - Hard cap on number of targets hit.

### Procs

- <a id="f-procFlags"></a>**`procFlags`** - Event mask that can trigger the proc (melee hit, spell cast, ...).
- <a id="f-procChance"></a>**`procChance`** - Proc frequency (PPM handling and flat % values).
- <a id="f-procCharges"></a>**`procCharges`** - Charges consumed when the proc fires.

### Levels & Scaling

- <a id="f-maxLevel"></a>**`maxLevel`** - Highest character level that may learn/receive it.
- <a id="f-baseLevel"></a>**`baseLevel`** - Level of the base rank.
- <a id="f-spellLevel"></a>**`spellLevel`** - Required level shown on tooltips / used in downranking math.

### Power Costs

- <a id="f-durationIndex"></a>**`durationIndex`** - Row in `SpellDuration.dbc`.
- <a id="f-powerType"></a>**`powerType`** - Power consumed (`enum Powers`, `SharedDefines.h`): `0` Mana,
  `1` Rage, `2` Focus, `3` Energy, `4` Happiness (`0xFFFFFFFE` Health).
- <a id="f-manaCost"></a>**`manaCost`** - Flat cost percentage/value depending on power type.
- <a id="f-manCostPerLevel"></a>**`manCostPerLevel`** - Additional cost per caster level.
- <a id="f-manaPerSecond"></a><a id="f-manaPerSecondPerLevel"></a>**`manaPerSecond`** / **`manaPerSecondPerLevel`** - Upkeep costs while active/channeling.
- <a id="f-manaCostPercentage"></a>**`manaCostPercentage`** - Cost as % of total mana.

### Range, Speed & Stacking

- <a id="f-rangeIndex"></a>**`rangeIndex`** - Row in `SpellRange.dbc` (max/min range).
- <a id="f-speed"></a>**`speed`** - Projectile travel speed (yards/sec); 0 = instant.
- <a id="f-stackAmount"></a>**`stackAmount`** - Max stacks of the produced aura.
- <a id="f-modelNextSpell"></a>**`modelNextSpell`** - DBC passthrough field; not used by the current core loader.

### Reagents, Totems & Equipment Requirements

- <a id="f-totem1"></a><a id="f-totem2"></a>**`totem1` / `totem2`** - Required totem items ([`item_template`](item_template.md).entry; shaman spells).
- <a id="f-reagent1"></a><a id="f-reagent2"></a><a id="f-reagent3"></a><a id="f-reagent4"></a><a id="f-reagent5"></a><a id="f-reagent6"></a><a id="f-reagent7"></a><a id="f-reagent8"></a>**`reagent1`**, **`reagent2`**, **`reagent3`**, **`reagent4`**, **`reagent5`**, **`reagent6`**, **`reagent7`**, **`reagent8`** - Consumed reagent item entries. (see [`item_template`](item_template.md).entry)
- <a id="f-reagentCount1"></a><a id="f-reagentCount2"></a><a id="f-reagentCount3"></a><a id="f-reagentCount4"></a><a id="f-reagentCount5"></a><a id="f-reagentCount6"></a><a id="f-reagentCount7"></a><a id="f-reagentCount8"></a>**`reagentCount1`**, **`reagentCount2`**, **`reagentCount3`**, **`reagentCount4`**, **`reagentCount5`**, **`reagentCount6`**, **`reagentCount7`**, **`reagentCount8`** - Amount for the matching reagent.
- <a id="f-equippedItemClass"></a><a id="f-equippedItemInventoryTypeMask"></a><a id="f-equippedItemSubClassMask"></a>**`equippedItemClass` / `equippedItemSubClassMask` / `equippedItemInventoryTypeMask`** -
  Weapon/armor requirements for combat procs (-1 = any).

### Effects 1-3

Each effect slot has the same set of columns:

- <a id="f-effect1"></a><a id="f-effect2"></a><a id="f-effect3"></a>**`effect1` / `effect2` / `effect3`** - Effect type (`SPELL_EFFECT_*`), see the [Effect Types table](#effect-types) below.
- <a id="f-effectDieSides1"></a><a id="f-effectDieSides2"></a><a id="f-effectDieSides3"></a>**`effectDieSides1` / `effectDieSides2` / `effectDieSides3`** - Random dice portion of the magnitude.
- <a id="f-effectBaseDice1"></a><a id="f-effectBaseDice2"></a><a id="f-effectBaseDice3"></a>**`effectBaseDice1` / `effectBaseDice2` / `effectBaseDice3`** - Base die count.
- <a id="f-effectDicePerLevel1"></a><a id="f-effectDicePerLevel2"></a><a id="f-effectDicePerLevel3"></a>**`effectDicePerLevel1` / `effectDicePerLevel2` / `effectDicePerLevel3`** - Dice added per caster level.
- <a id="f-effectRealPointsPerLevel1"></a><a id="f-effectRealPointsPerLevel2"></a><a id="f-effectRealPointsPerLevel3"></a>**`effectRealPointsPerLevel1` / `effectRealPointsPerLevel2` / `effectRealPointsPerLevel3`** - Flat points added per caster level.
- <a id="f-effectBasePoints1"></a><a id="f-effectBasePoints2"></a><a id="f-effectBasePoints3"></a>**`effectBasePoints1` / `effectBasePoints2` / `effectBasePoints3`** - Base value (dice roll is added to this).
- <a id="f-effectBonusCoefficient1"></a><a id="f-effectBonusCoefficient2"></a><a id="f-effectBonusCoefficient3"></a>**`effectBonusCoefficient1` / `effectBonusCoefficient2` / `effectBonusCoefficient3`** - Spell-power coefficient.
- <a id="f-effectMechanic1"></a><a id="f-effectMechanic2"></a><a id="f-effectMechanic3"></a>**`effectMechanic1` / `effectMechanic2` / `effectMechanic3`** - Mechanic applied by this effect.
- <a id="f-effectImplicitTargetA1"></a><a id="f-effectImplicitTargetA2"></a><a id="f-effectImplicitTargetA3"></a><a id="f-effectImplicitTargetB1"></a><a id="f-effectImplicitTargetB2"></a><a id="f-effectImplicitTargetB3"></a>**`effectImplicitTargetA1`**, **`effectImplicitTargetA2`**, **`effectImplicitTargetA3`**, **`effectImplicitTargetB1`**, **`effectImplicitTargetB2`**, **`effectImplicitTargetB3`** - Target selection rules (`TARGET_*` ids from `Spell.dbc`).
- <a id="f-effectRadiusIndex1"></a><a id="f-effectRadiusIndex2"></a><a id="f-effectRadiusIndex3"></a>**`effectRadiusIndex1` / `effectRadiusIndex2` / `effectRadiusIndex3`** - Row in `SpellRadius.dbc`.
- <a id="f-effectApplyAuraName1"></a><a id="f-effectApplyAuraName2"></a><a id="f-effectApplyAuraName3"></a>**`effectApplyAuraName1` / `effectApplyAuraName2` / `effectApplyAuraName3`** - Aura applied by the effect (`SPELL_AURA_*`).
- <a id="f-effectAmplitude1"></a><a id="f-effectAmplitude2"></a><a id="f-effectAmplitude3"></a>**`effectAmplitude1` / `effectAmplitude2` / `effectAmplitude3`** - Tick interval for periodic auras (ms).
- <a id="f-effectMultipleValue1"></a><a id="f-effectMultipleValue2"></a><a id="f-effectMultipleValue3"></a>**`effectMultipleValue1` / `effectMultipleValue2` / `effectMultipleValue3`** - Multiplier for combo-point/hot scaling values.
- <a id="f-effectChainTarget1"></a><a id="f-effectChainTarget2"></a><a id="f-effectChainTarget3"></a>**`effectChainTarget1` / `effectChainTarget2` / `effectChainTarget3`** - Additional targets hit by chaining.
- <a id="f-effectItemType1"></a><a id="f-effectItemType2"></a><a id="f-effectItemType3"></a>**`effectItemType1` / `effectItemType2` / `effectItemType3`** - Item created (CREATE_ITEM) or loot item (for some effects).
- <a id="f-effectMiscValue1"></a><a id="f-effectMiscValue2"></a><a id="f-effectMiscValue3"></a>**`effectMiscValue1` / `effectMiscValue2` / `effectMiscValue3`** - Generic per-effect payload (faction id, aura slot, school...).
- <a id="f-effectTriggerSpell1"></a><a id="f-effectTriggerSpell2"></a><a id="f-effectTriggerSpell3"></a>**`effectTriggerSpell1` / `effectTriggerSpell2` / `effectTriggerSpell3`** - Spell triggered/taught/applied by this effect ([`spell_template`](spell_template.md).entry).
- <a id="f-effectPointsPerComboPoint1"></a><a id="f-effectPointsPerComboPoint2"></a><a id="f-effectPointsPerComboPoint3"></a>**`effectPointsPerComboPoint1` / `effectPointsPerComboPoint2` / `effectPointsPerComboPoint3`** - Value added per combo point.

### Effect Types

All `SPELL_EFFECT_*` values from `src/game/Spells/SpellDefines.h`:

| Effect | Name |
| :---: | :--- |
| 0 | NONE |
| 1 | INSTAKILL |
| 2 | SCHOOL_DAMAGE |
| 3 | DUMMY |
| 4 | PORTAL_TELEPORT |
| 5 | TELEPORT_UNITS |
| 6 | APPLY_AURA |
| 7 | ENVIRONMENTAL_DAMAGE |
| 8 | POWER_DRAIN |
| 9 | HEALTH_LEECH |
| 10 | HEAL |
| 11 | BIND |
| 12 | PORTAL |
| 13 | RITUAL_BASE |
| 14 | RITUAL_SPECIALIZE |
| 15 | RITUAL_ACTIVATE_PORTAL |
| 16 | QUEST_COMPLETE |
| 17 | WEAPON_DAMAGE_NOSCHOOL |
| 18 | RESURRECT |
| 19 | ADD_EXTRA_ATTACKS |
| 20 | DODGE |
| 21 | EVADE |
| 22 | PARRY |
| 23 | BLOCK |
| 24 | CREATE_ITEM |
| 25 | WEAPON |
| 26 | DEFENSE |
| 27 | PERSISTENT_AREA_AURA |
| 28 | SUMMON |
| 29 | LEAP |
| 30 | ENERGIZE |
| 31 | WEAPON_PERCENT_DAMAGE |
| 32 | TRIGGER_MISSILE |
| 33 | OPEN_LOCK |
| 34 | SUMMON_CHANGE_ITEM |
| 35 | APPLY_AREA_AURA_PARTY |
| 36 | LEARN_SPELL |
| 37 | SPELL_DEFENSE |
| 38 | DISPEL |
| 39 | LANGUAGE |
| 40 | DUAL_WIELD |
| 41 | SUMMON_WILD |
| 42 | SUMMON_GUARDIAN |
| 43 | TELEPORT_UNITS_FACE_CASTER |
| 44 | SKILL_STEP |
| 45 | ADD_HONOR |
| 46 | SPAWN |
| 47 | TRADE_SKILL |
| 48 | STEALTH |
| 49 | DETECT |
| 50 | TRANS_DOOR |
| 51 | FORCE_CRITICAL_HIT |
| 52 | GUARANTEE_HIT |
| 53 | ENCHANT_ITEM |
| 54 | ENCHANT_ITEM_TEMPORARY |
| 55 | TAMECREATURE |
| 56 | SUMMON_PET |
| 57 | LEARN_PET_SPELL |
| 58 | WEAPON_DAMAGE |
| 59 | OPEN_LOCK_ITEM |
| 60 | PROFICIENCY |
| 61 | SEND_EVENT |
| 62 | POWER_BURN |
| 63 | THREAT |
| 64 | TRIGGER_SPELL |
| 65 | HEALTH_FUNNEL |
| 66 | POWER_FUNNEL |
| 67 | HEAL_MAX_HEALTH |
| 68 | INTERRUPT_CAST |
| 69 | DISTRACT |
| 70 | PULL |
| 71 | PICKPOCKET |
| 72 | ADD_FARSIGHT |
| 73 | SUMMON_POSSESSED |
| 74 | SUMMON_TOTEM |
| 75 | HEAL_MECHANICAL |
| 76 | SUMMON_OBJECT_WILD |
| 77 | SCRIPT_EFFECT |
| 78 | ATTACK |
| 79 | SANCTUARY |
| 80 | ADD_COMBO_POINTS |
| 81 | CREATE_HOUSE |
| 82 | BIND_SIGHT |
| 83 | DUEL |
| 84 | STUCK |
| 85 | SUMMON_PLAYER |
| 86 | ACTIVATE_OBJECT |
| 87 | SUMMON_TOTEM_SLOT1 |
| 88 | SUMMON_TOTEM_SLOT2 |
| 89 | SUMMON_TOTEM_SLOT3 |
| 90 | SUMMON_TOTEM_SLOT4 |
| 91 | THREAT_ALL |
| 92 | ENCHANT_HELD_ITEM |
| 93 | SUMMON_PHANTASM |
| 94 | SELF_RESURRECT |
| 95 | SKINNING |
| 96 | CHARGE |
| 97 | SUMMON_CRITTER |
| 98 | KNOCK_BACK |
| 99 | DISENCHANT |
| 100 | INEBRIATE |
| 101 | FEED_PET |
| 102 | DISMISS_PET |
| 103 | REPUTATION |
| 104 | SUMMON_OBJECT_SLOT1 |
| 105 | SUMMON_OBJECT_SLOT2 |
| 106 | SUMMON_OBJECT_SLOT3 |
| 107 | SUMMON_OBJECT_SLOT4 |
| 108 | DISPEL_MECHANIC |
| 109 | SUMMON_DEAD_PET |
| 110 | DESTROY_ALL_TOTEMS |
| 111 | DURABILITY_DAMAGE |
| 112 | SUMMON_DEMON |
| 113 | RESURRECT_NEW |
| 114 | ATTACK_ME |
| 115 | DURABILITY_DAMAGE_PCT |
| 116 | SKIN_PLAYER_CORPSE |
| 117 | SPIRIT_HEAL |
| 118 | SKILL |
| 119 | APPLY_AREA_AURA_PET |
| 120 | TELEPORT_GRAVEYARD |
| 121 | NORMALIZED_WEAPON_DMG |
| 122 | 122 |
| 123 | SEND_TAXI |
| 124 | PLAYER_PULL |
| 125 | MODIFY_THREAT_PERCENT |
| 126 | 126 |
| 127 | 127 |
| 128 | APPLY_AREA_AURA_FRIEND |
| 129 | APPLY_AREA_AURA_ENEMY |
| 130 | DESPAWN_OBJECT |
| 131 | NOSTALRIUS |
| 132 | APPLY_AREA_AURA_RAID |
| 133 | APPLY_AREA_AURA_OWNER |

### Visuals, Icons & Family

- <a id="f-spellVisual1"></a><a id="f-spellVisual2"></a>**`spellVisual1` / `spellVisual2`** - Cast visual ids (`SpellVisual.dbc`).
- <a id="f-activeIconId"></a><a id="f-spellIconId"></a>**`spellIconId`** / **`activeIconId`** - Tooltip/action icons.
- <a id="f-spellPriority"></a>**`spellPriority`** - Aura display priority.
- <a id="f-spellFamilyFlags"></a><a id="f-spellFamilyName"></a>**`spellFamilyName`** / **`spellFamilyFlags`** - Class/family identification used by procs
  and talent interactions.
- <a id="f-maxTargetLevel"></a><a id="f-minTargetLevel"></a>**`minTargetLevel`** / **`maxTargetLevel`** - Target level restrictions.
- <a id="f-dmgClass"></a>**`dmgClass`** - Damage class: `0` none, `1` magic, `2` melee, `3` ranged.
- <a id="f-preventionType"></a>**`preventionType`** - What blocks casting: `0` none, `1` Silence, `2` Pacify
  (`SPELL_PREVENTION_TYPE_*`).
- <a id="f-stanceBarOrder"></a>**`stanceBarOrder`** - Position in the shapeshift bar (DBC passthrough; not read by the current core loader).

### Misc & Server Fields

- <a id="f-dmgMultiplier1"></a><a id="f-dmgMultiplier2"></a><a id="f-dmgMultiplier3"></a>**`dmgMultiplier1`**, **`dmgMultiplier2`**, **`dmgMultiplier3`** - Per-effect damage
  multiplier (e.g. AoE falloff).
- <a id="f-minFactionId"></a><a id="f-minReputation"></a>**`minFactionId`** / **`minReputation`** - Reputation requirement for the spell to work (DBC passthrough; not read by the current core loader).
- <a id="f-requiredAuraVision"></a>**`requiredAuraVision`** - Caster needs an aura allowing them to see stealth/invisible
  targets of this kind (DBC passthrough; not read by the current core loader).
- <a id="f-customFlags"></a>**`customFlags`** - Server-side flags loaded into `SpellEntry::Custom` (`SPELL_CUSTOM_*`,
  `SpellDefines.h`: allow stacking between casters, fixed damage, ignore armor, separate aura per caster...).
- <a id="f-script_name"></a>**`script_name`** - C++ spell script binding ([Scripts Library](../Scripts-Library.md));
  also referenced from [`spell_script_target`](spell_script_target.md) setups.

### Proc Behaviour

- `procFlags`: event mask (melee/ranged swing or ability dealt & taken, spell cast, kill,
  heartbeat tick...), bits defined as `PROC_FLAG_*` in `src/game/Spells/SpellDefines.h`.
- `procChance`, `procCharges`: frequency & charge consumption.
- Detailed triggers: [`spell_proc_event`](spell_proc_event.md).
