# creature_template Table

Defines base properties for all creature types - stats, display, faction, AI, loot, and more.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`patch`](#f-patch) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`name`](#f-name) | char(100) |  | NO | '0' |  |
| [`subname`](#f-subname) | char(100) |  | YES |  |  |
| [`level_min`](#f-level_min) | tinyint(3) unsigned |  | NO | 1 |  |
| [`level_max`](#f-level_max) | tinyint(3) unsigned |  | NO | 1 |  |
| [`faction`](#f-faction) | smallint(5) unsigned |  | NO | 0 |  |
| [`npc_flags`](#f-npc_flags) | int(10) unsigned |  | NO | 0 |  |
| [`gossip_menu_id`](#f-gossip_menu_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`display_id1`](#f-display_id1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`display_id2`](#f-display_id2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`display_id3`](#f-display_id3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`display_id4`](#f-display_id4) | mediumint(8) unsigned |  | NO | 0 |  |
| [`display_scale1`](#f-display_scale1) | float |  | NO | 0 |  |
| [`display_scale2`](#f-display_scale2) | float |  | NO | 0 |  |
| [`display_scale3`](#f-display_scale3) | float |  | NO | 0 |  |
| [`display_scale4`](#f-display_scale4) | float |  | NO | 0 |  |
| [`display_probability1`](#f-display_probability1) | smallint(5) unsigned |  | NO | 0 |  |
| [`display_probability2`](#f-display_probability2) | smallint(5) unsigned |  | NO | 0 |  |
| [`display_probability3`](#f-display_probability3) | smallint(5) unsigned |  | NO | 0 |  |
| [`display_probability4`](#f-display_probability4) | smallint(5) unsigned |  | NO | 0 |  |
| [`display_total_probability`](#f-display_total_probability) | smallint(5) unsigned |  | NO | 0 |  |
| [`mount_display_id`](#f-mount_display_id) | smallint(5) unsigned |  | NO | 0 |  |
| [`speed_walk`](#f-speed_walk) | float |  | NO | 1 |  |
| [`speed_run`](#f-speed_run) | float |  | NO | 1.14286 |  |
| [`detection_range`](#f-detection_range) | float |  | NO | 18 |  |
| [`call_for_help_range`](#f-call_for_help_range) | float |  | NO | 5 |  |
| [`leash_range`](#f-leash_range) | float |  | NO | 0 |  |
| [`type`](#f-type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`pet_family`](#f-pet_family) | tinyint(4) unsigned |  | NO | 0 |  |
| [`rank`](#f-rank) | tinyint(3) unsigned |  | NO | 0 |  |
| [`unit_class`](#f-unit_class) | tinyint(3) unsigned |  | NO | 0 |  |
| [`xp_multiplier`](#f-xp_multiplier) | float |  | NO | 1 |  |
| [`health_multiplier`](#f-health_multiplier) | float |  | NO | 1 |  |
| [`mana_multiplier`](#f-mana_multiplier) | float |  | NO | 1 |  |
| [`armor_multiplier`](#f-armor_multiplier) | float |  | NO | 1 |  |
| [`damage_multiplier`](#f-damage_multiplier) | float |  | NO | 1 |  |
| [`damage_variance`](#f-damage_variance) | float |  | NO | 0.14 |  |
| [`damage_school`](#f-damage_school) | tinyint(4) unsigned |  | NO | 0 |  |
| [`base_attack_time`](#f-base_attack_time) | int(10) unsigned |  | NO | 2000 |  |
| [`ranged_attack_time`](#f-ranged_attack_time) | int(10) unsigned |  | NO | 2000 |  |
| [`holy_res`](#f-holy_res) | smallint(5) |  | NO | 0 |  |
| [`fire_res`](#f-fire_res) | smallint(5) |  | NO | 0 |  |
| [`nature_res`](#f-nature_res) | smallint(5) |  | NO | 0 |  |
| [`frost_res`](#f-frost_res) | smallint(5) |  | NO | 0 |  |
| [`shadow_res`](#f-shadow_res) | smallint(5) |  | NO | 0 |  |
| [`arcane_res`](#f-arcane_res) | smallint(5) |  | NO | 0 |  |
| [`trainer_type`](#f-trainer_type) | tinyint(4) unsigned |  | NO | 0 |  |
| [`trainer_spell`](#f-trainer_spell) | smallint(5) unsigned |  | NO | 0 |  |
| [`trainer_class`](#f-trainer_class) | tinyint(3) unsigned |  | NO | 0 |  |
| [`trainer_race`](#f-trainer_race) | tinyint(3) unsigned |  | NO | 0 |  |
| [`loot_id`](#f-loot_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`pickpocket_loot_id`](#f-pickpocket_loot_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`skinning_loot_id`](#f-skinning_loot_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`gold_min`](#f-gold_min) | mediumint(8) unsigned |  | NO | 0 |  |
| [`gold_max`](#f-gold_max) | mediumint(8) unsigned |  | NO | 0 |  |
| [`spell_list_id`](#f-spell_list_id) | int(11) unsigned |  | NO | 0 |  |
| [`pet_spell_list_id`](#f-pet_spell_list_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`spawn_spell_id`](#f-spawn_spell_id) | smallint(5) unsigned |  | NO | 0 |  |
| [`totem_spell_id`](#f-totem_spell_id) | smallint(5) unsigned |  | NO | 0 |  |
| [`auras`](#f-auras) | text |  | YES |  |  |
| [`ai_name`](#f-ai_name) | char(64) |  | NO | '' |  |
| [`movement_type`](#f-movement_type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`inhabit_type`](#f-inhabit_type) | tinyint(3) unsigned |  | NO | 3 |  |
| [`civilian`](#f-civilian) | tinyint(3) unsigned |  | NO | 0 |  |
| [`racial_leader`](#f-racial_leader) | tinyint(3) unsigned |  | NO | 0 |  |
| [`equipment_id`](#f-equipment_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`trainer_id`](#f-trainer_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`vendor_id`](#f-vendor_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`mechanic_immune_mask`](#f-mechanic_immune_mask) | int(10) unsigned |  | NO | 0 |  |
| [`school_immune_mask`](#f-school_immune_mask) | int(10) unsigned |  | NO | 0 |  |
| [`immunity_flags`](#f-immunity_flags) | int(10) unsigned |  | NO | 0 |  |
| [`static_flags1`](#f-static_flags1) | int(10) unsigned |  | NO | 0 |  |
| [`static_flags2`](#f-static_flags2) | int(10) unsigned |  | NO | 0 |  |
| [`flags_extra`](#f-flags_extra) | int(10) unsigned |  | NO | 0 |  |
| [`script_name`](#f-script_name) | char(64) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Unique creature ID.
- <a id="f-patch"></a>**`patch`** - Primary Key. Client patch version.
- <a id="f-subname"></a><a id="f-name"></a>**`name`** / **`subname`** - Creature name and title.
- <a id="f-level_max"></a><a id="f-level_min"></a>**`level_min` / `level_max`** - Level range.
- <a id="f-faction"></a>**`faction`** - Faction template id ([`faction_template`](faction_template.md).id).
- <a id="f-npc_flags"></a>**`npc_flags`** - Interaction bitmask; see the full table in [Flag Bitmasks](#flag-bitmasks) below.
- <a id="f-gossip_menu_id"></a>**`gossip_menu_id`** - Default gossip menu (from [`gossip_menu`](gossip_menu.md).entry).
- <a id="f-display_id1"></a><a id="f-display_id2"></a><a id="f-display_id3"></a><a id="f-display_id4"></a>**`display_id1-4`** - Model display IDs.
- <a id="f-display_scale1"></a><a id="f-display_scale2"></a><a id="f-display_scale3"></a><a id="f-display_scale4"></a>**`display_scale1-4`** - Scale multipliers.
- <a id="f-display_probability1"></a><a id="f-display_probability2"></a><a id="f-display_probability3"></a><a id="f-display_probability4"></a>**`display_probability1-4`** - Chance weights for each display.
- <a id="f-display_total_probability"></a>**`display_total_probability`** - Sum of the four weights; used to normalise random display selection.
- <a id="f-mount_display_id"></a>**`mount_display_id`** - Mount model.
- <a id="f-speed_run"></a><a id="f-speed_walk"></a>**`speed_walk` / `speed_run`** - Movement speeds.
- <a id="f-detection_range"></a>**`detection_range`** - Aggro/visibility range.
- <a id="f-call_for_help_range"></a>**`call_for_help_range`** - Radius to call allies.
- <a id="f-leash_range"></a>**`leash_range`** - Max distance before resetting.
- <a id="f-type"></a>**`type`** - Creature type (`CREATURE_TYPE_*`): `1` Beast · `2` Dragonkin · `3` Demon ·
  `4` Elemental · `5` Giant · `6` Undead · `7` Humanoid · `8` Critter · `9` Mechanical ·
  `10` Not specified · `11` Totem.
- <a id="f-pet_family"></a>**`pet_family`** - Pet family (for hunter pets).
- <a id="f-rank"></a>**`rank`** - `0` Normal, `1` Elite, `2` Rare elite, `3` World boss, `4` Rare (`CREATURE_ELITE_*`).
- <a id="f-unit_class"></a>**`unit_class`** - Combat class driving base stats (`enum Classes`): `1` Warrior, `2` Paladin,
  `4` Rogue, `8` Mage (`CLASSMASK_ALL_CREATURES`).
- <a id="f-armor_multiplier"></a><a id="f-damage_multiplier"></a><a id="f-health_multiplier"></a><a id="f-mana_multiplier"></a><a id="f-xp_multiplier"></a>**`*_multiplier`** - Stat multipliers.
- <a id="f-damage_variance"></a>**`damage_variance`** - Damage spread.
- <a id="f-base_attack_time"></a><a id="f-ranged_attack_time"></a>**`base_attack_time` / `ranged_attack_time`** - Attack speed (ms).
- <a id="f-arcane_res"></a><a id="f-fire_res"></a><a id="f-frost_res"></a><a id="f-holy_res"></a><a id="f-nature_res"></a><a id="f-shadow_res"></a>**`*_res`** - Resistances (holy/fire/nature/frost/shadow/arcane).
- <a id="f-damage_school"></a>**`damage_school`** - School used for melee damage (`SPELL_SCHOOL_*`): `0` Physical,
  `1` Holy, `2` Fire, `3` Nature, `4` Frost, `5` Shadow, `6` Arcane.
- <a id="f-trainer_class"></a><a id="f-trainer_race"></a><a id="f-trainer_spell"></a><a id="f-trainer_type"></a>**`trainer_*`** - Trainer configuration.
- <a id="f-loot_id"></a>**`loot_id`** - Creature loot template.
- <a id="f-pickpocket_loot_id"></a>**`pickpocket_loot_id`** - Pickpocket loot.
- <a id="f-skinning_loot_id"></a>**`skinning_loot_id`** - Skinning loot.
- <a id="f-gold_max"></a><a id="f-gold_min"></a>**`gold_min` / `gold_max`** - Coin drop range.
- <a id="f-spell_list_id"></a>**`spell_list_id`** - Reference to [`creature_spells`](creature_spells.md).entry.
- <a id="f-pet_spell_list_id"></a>**`pet_spell_list_id`** - Spells for pets.
- <a id="f-spawn_spell_id"></a>**`spawn_spell_id`** - Spell cast on spawn.
- <a id="f-totem_spell_id"></a>**`totem_spell_id`** - Spell cast by this creature when summoned as a totem (`TotemAI`).
- <a id="f-auras"></a>**`auras`** - Permanent auras.
- <a id="f-ai_name"></a>**`ai_name`** - AI script name.
- <a id="f-movement_type"></a>**`movement_type`** - Default movement.
- <a id="f-inhabit_type"></a>**`inhabit_type`** - Bitmask (`INHABIT_*`): `1` Ground · `2` Water · `4` Air; combine by
  summing (e.g. `3` = ground+water swimmer, `7` = anywhere).
- <a id="f-civilian"></a>**`civilian`** - `1` if civilian (no aggro).
- <a id="f-racial_leader"></a>**`racial_leader`** - `1` if racial leader (bonus honor when killed).
- <a id="f-equipment_id"></a>**`equipment_id`** - Equipment set.
- <a id="f-trainer_id"></a>**`trainer_id`** - Trainer template.
- <a id="f-vendor_id"></a>**`vendor_id`** - Vendor template.
- <a id="f-mechanic_immune_mask"></a>**`mechanic_immune_mask`** - Bit per spell mechanic; see the [Mechanics Reference](#mechanic-immune-mask) below.
- <a id="f-school_immune_mask"></a>**`school_immune_mask`** - Bit per damage school; see the [table](#school-immune-mask--immunity-flags) below.
- <a id="f-immunity_flags"></a>**`immunity_flags`** - Behaviour immunity bitmask; see the [table](#immunity-flags-table) below.
- <a id="f-static_flags1"></a><a id="f-static_flags2"></a>**`static_flags1` / `static_flags2`** - Behaviour bits; see the [tables](#static_flags1) below.
- <a id="f-flags_extra"></a>**`flags_extra`** - Extra behaviour flags; see the complete reference below.
- <a id="f-script_name"></a>**`script_name`** - C++ script binding.

---

## Flag Bitmasks

Values come from `src/game/Objects/CreatureDefines.h` and `UnitDefines.h`.

### `npc_flags` (interaction flags) {#flag-bitmasks}

| Flag | Name | Effect |
| ---: | :--- | :--- |
| 0x00000001 | GOSSIP | shows gossip menu |
| 0x00000002 | QUESTGIVER | quest offering |
| 0x00000004 | VENDOR | sell items ([`npc_vendor`](npc_vendor.md)) |
| 0x00000008 | FLIGHTMASTER | taxi routes |
| 0x00000010 | TRAINER | teach spells ([`npc_trainer`](npc_trainer.md)) |
| 0x00000020 | SPIRITHEALER | resurrect player |
| 0x00000040 | SPIRITGUIDE | BG resurrection |
| 0x00000080 | INNKEEPER | set hearthstone |
| 0x00000100 | BANKER | access bank |
| 0x00000200 | PETITIONER | guild charters |
| 0x00000400 | TABARDDESIGNER | guild tabard purchase |
| 0x00000800 | BATTLEMASTER | BG queues |
| 0x00001000 | AUCTIONEER | auction house |
| 0x00002000 | STABLEMASTER | pet stable |
| 0x00004000 | REPAIR | equipment repair |

---

### `static_flags1`

| Flag | Name | Effect |
| ---: | :--- | :--- |
| 0x00000001 | MOUNTABLE | *(unused by core)* |
| 0x00000002 | NO_XP | no experience from killing |
| 0x00000004 | NO_LOOT | *(unused by core)* |
| 0x00000008 | UNKILLABLE | invincibility threshold at 1 HP |
| 0x00000010 | TAMEABLE | huntable by hunters |
| 0x00000020 | IMMUNE_TO_PC | applies UNIT_FLAG_IMMUNE_TO_PLAYER |
| 0x00000040 | IMMUNE_TO_NPC | applies UNIT_FLAG_IMMUNE_TO_NPC |
| 0x00000080 | CAN_WIELD_LOOT | generates loot on spawn, wields weapons |
| 0x00000100 | SESSILE | cannot move |
| 0x00000200 | UNINTERACTIBLE | NOT_SELECTABLE on spawn |
| 0x00000400 | NO_AUTOMATIC_REGEN | no health/mana regen |
| 0x00000800 | DESPAWN_INSTANTLY | corpse disappears at once |
| 0x00001000 | CORPSE_RAID | death ignores distance/damage-origin checks for loot+XP |
| 0x00002000 | CREATOR_LOOT | creator may loot summoned corpse |
| 0x00004000 | NO_DEFENSE | defense skill = 0 |
| 0x00008000 | NO_SPELL_DEFENSE | cannot resist spells |
| 0x00010000 | RAID_BOSS_MOB | *(unused)* |
| 0x00020000 | COMBAT_PING | minimap ping when entering combat |
| 0x00040000 | AQUATIC | water-only (inhabit override) |
| 0x00080000 | AMPHIBIOUS | ground + water inhabit |
| 0x00100000 | NO_MELEE | does not auto-attack |
| 0x00200000 | VISIBLE_TO_GHOSTS | visible to ghosts (spirit healers) |
| 0x00400000 | PVP_ENABLING | flagged for PvP; targetable by beneficial spells |
| 0x00800000 | DO_NOT_PLAY_WOUND_ANIM | will not play EMOTE_ONESHOT_WOUNDCRITICAL |
| 0x01000000 | NO_FACTION_TOOLTIP | *(unused by core)* |
| 0x02000000 | IGNORE_COMBAT | react state = passive |
| 0x04000000 | ONLY_ATTACK_PVP_ENABLING | no proximity aggro for non-PvP-flagged players |
| 0x08000000 | CALLS_GUARDS | summons a guard near/at opposite-faction players |
| 0x10000000 | CAN_SWIM | applies UNIT_FLAG_USE_SWIM_ANIMATION on spawn |
| 0x20000000 | FLOATING | applies MOVEFLAG_FIXED_Z on spawn |
| 0x40000000 | MORE_AUDIBLE | larger audible range |
| 0x80000000 | LARGE_AOI | visibility distance increased to 200 yards |

**`static_flags2`** continues the list:

| Flag | Name | Effect |
| ---: | :--- | :--- |
| 0x00000001 | NO_PET_SCALING | not used by the core |
| 0x00000002 | FORCE_RAID_COMBAT | enters combat with the zone on aggro |
| 0x00000004 | LOCK_TAPPERS_TO_RAID_ON_DEATH | killing it binds players to the raid |
| 0x00000008 | NO_HARMFUL_VERTEX_COLORING | not used by the core |
| 0x00000010 | NO_CRUSHING_BLOWS | will not deal crushing blows |
| 0x00000020 | NO_OWNER_THREAT | does not pull its owner into combat |
| 0x00000040 | NO_WOUNDED_SLOWDOWN | run speed unaffected at low health |

---

### `mechanic_immune_mask` {#mechanic-immune-mask}

Bit per spell mechanic (`SpellMechanic.dbc` index). Common values:

| Mask value | Immune to mechanic |
| ---: | :--- |
| 0x1 | Charm (MECHANIC_CHARM) |
| 0x2 | Disorient (MECHANIC_DISORIENTED) |
| 0x4 | Disarm (MECHANIC_DISARM) |
| 0x10 | Fear (MECHANIC_FEAR) |
| 0x40 | Root (MECHANIC_ROOT) |
| 0x100 | Silence (MECHANIC_SILENCE) |
| 0x400 | Snare (MECHANIC_SNARE) |
| 0x800 | Stun (MECHANIC_STUN) |
| 0x1000 | Freeze (MECHANIC_FREEZE) |
| 0x2000 | Knockout/incapacitate (MECHANIC_KNOCKOUT) |
| 0x10000 | Polymorph (MECHANIC_POLYMORPH) |
| … | one bit per mechanic (`1 << (mechanic - 1)`) |

The common boss crowd-control immunity mask in vanilla content is
`mechanic_immune_mask = 617299803`.

### `school_immune_mask` / `immunity_flags` {#school-immune-mask--immunity-flags}

- `school_immune_mask`: bit per damage school, physical(1), holy(2), fire(4), nature(8), frost(16),
  shadow(32), arcane(64).
- <a id="immunity-flags-table"></a>**`immunity_flags`** - Behaviour immunity bitmask (`enum CreatureImmunityFlags`,
  `CreatureDefines.h`):

  | Flag | Name | Effect |
  | ---: | :--- | :--- |
  | 0x01 | AOE | immune to AoE effects |
  | 0x02 | TAUNT | immune to taunt (`SPELL_AURA_MOD_TAUNT`, `SPELL_EFFECT_ATTACK_ME`) |
  | 0x04 | MOD_STAT | immune to stat modification auras |
  | 0x08 | MOD_CAST_SPEED | immune to casting speed modification |
  | 0x10 | DISEASE | immune to Disease dispel-type effects |
  | 0x20 | POISON | immune to Poison dispel-type effects |
  | 0x40 | CURSE | immune to Curse dispel-type effects |

<a id="flags-extra-reference"></a>
### Flags Extra Reference

All bits from `enum CreatureFlagsExtra` in `src/game/Objects/CreatureDefines.h`:

| Flag | Name | Effect |
| ---: | :--- | :--- |
| 0x00000001 | NO_LEASH_EVADE | will not evade when target runs away |
| 0x00000002 | NO_AGGRO | defensive; does not attack nearby hostiles |
| 0x00000004 | NO_PARRY | can't parry |
| 0x00000008 | NO_UNREACHABLE_EVADE | won't evade when target is unreachable |
| 0x00000010 | NO_BLOCK | can't block |
| 0x00000020 | NO_MOVEMENT_PAUSE | won't pause movement when a player talks to it |
| 0x00000040 | ALWAYS_RUN | uses run speed out of combat |
| 0x00000080 | INVISIBLE | always invisible to players (trigger creatures) |
| 0x00000100 | GIGANTIC_AOI | 400-yard area of interest |
| 0x00000200 | INFINITE_AOI | infinite area of interest |
| 0x00000400 | GUARD | is a guard |
| 0x00000800 | NO_THREAT_LIST | no threat list; 5-second player-style combat timer |
| 0x00001000 | KEEP_POSITIVE_AURAS_ON_EVADE | keeps positive auras at reset |
| 0x00002000 | ALWAYS_CRUSH | always roll crushing blows unless miss/crit/dodge/parry/block |
| 0x00004000 | APPEAR_DEAD | has UNIT_DYNFLAG_DEAD applied |
| 0x00008000 | CHASE_GEN_NO_BACKING | does not back up when target is inside bounding radius |
| 0x00010000 | NO_ASSIST | does not aggro when nearby creatures are attacked |
| 0x00020000 | NO_TARGET | passive; does not acquire targets |
| 0x00040000 | ONLY_VISIBLE_TO_FRIENDLY | visible only to friendly units |
| 0x00080000 | CAN_ASSIST | can assist other creatures in combat |
