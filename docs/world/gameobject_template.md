# gameobject_template Table

Defines base properties for game object types - type, display, data fields, and script.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`patch`](#f-patch) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`type`](#f-type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`displayId`](#f-displayId) | mediumint(8) unsigned |  | NO | 0 |  |
| [`name`](#f-name) | varchar(100) |  | NO | '' |  |
| [`icon`](#f-icon) | varchar(100) |  | NO | '' |  |
| [`faction`](#f-faction) | smallint(5) unsigned |  | NO | 0 |  |
| [`flags`](#f-flags) | int(10) unsigned |  | NO | 0 |  |
| [`size`](#f-size) | float |  | NO | 1 |  |
| [`data0`](#f-data0) | int(10) |  | NO | 0 |  |
| [`data1`](#f-data1) | int(11) |  | NO | 0 |  |
| [`data2`](#f-data2) | int(10) |  | NO | 0 |  |
| [`data3`](#f-data3) | int(10) |  | NO | 0 |  |
| [`data4`](#f-data4) | int(10) |  | NO | 0 |  |
| [`data5`](#f-data5) | int(10) |  | NO | 0 |  |
| [`data6`](#f-data6) | int(11) |  | NO | 0 |  |
| [`data7`](#f-data7) | int(10) |  | NO | 0 |  |
| [`data8`](#f-data8) | int(10) |  | NO | 0 |  |
| [`data9`](#f-data9) | int(10) |  | NO | 0 |  |
| [`data10`](#f-data10) | int(10) |  | NO | 0 |  |
| [`data11`](#f-data11) | int(10) |  | NO | 0 |  |
| [`data12`](#f-data12) | int(10) |  | NO | 0 |  |
| [`data13`](#f-data13) | int(10) |  | NO | 0 |  |
| [`data14`](#f-data14) | int(10) |  | NO | 0 |  |
| [`data15`](#f-data15) | int(10) |  | NO | 0 |  |
| [`data16`](#f-data16) | int(10) |  | NO | 0 |  |
| [`data17`](#f-data17) | int(10) |  | NO | 0 |  |
| [`data18`](#f-data18) | int(10) |  | NO | 0 |  |
| [`data19`](#f-data19) | int(10) |  | NO | 0 |  |
| [`data20`](#f-data20) | int(10) |  | NO | 0 |  |
| [`data21`](#f-data21) | int(10) |  | NO | 0 |  |
| [`data22`](#f-data22) | int(10) |  | NO | 0 |  |
| [`data23`](#f-data23) | int(10) |  | NO | 0 |  |
| [`mingold`](#f-mingold) | mediumint(8) unsigned |  | NO | 0 |  |
| [`maxgold`](#f-maxgold) | mediumint(8) unsigned |  | NO | 0 |  |
| [`script_name`](#f-script_name) | varchar(64) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Unique gameobject template ID.
- <a id="f-patch"></a>**`patch`** - Content patch ([progression](../Progression-System.md)) this row applies to.
- <a id="f-type"></a>**`type`** - Object type; see [Data Fields by Type](#data-fields-by-type).
- <a id="f-displayId"></a>**`displayId`** - Display model row from `GameObjectDisplayInfo.dbc`.
- <a id="f-name"></a>**`name`** - Object name shown on interact/tooltip contexts.
- <a id="f-icon"></a>**`icon`** - Icon name (DBC passthrough, mostly empty in vanilla).
- <a id="f-faction"></a>**`faction`** - Faction template id ([`faction_template`](faction_template.md).id).
- <a id="f-flags"></a>**`flags`** - Behaviour bitmask; see the [Flags](#flags-go_flag_) table below.
- <a id="f-size"></a>**`size`** - Display scale multiplier.
- <a id="f-mingold"></a>**`mingold`** - Minimum coin dropped when looted (chest-type objects).
- <a id="f-maxgold"></a>**`maxgold`** - Maximum coin dropped when looted.
- <a id="f-script_name"></a>**`script_name`** - C++ script binding ([Scripts Library](../Scripts-Library.md)).

### Flags (`GO_FLAG_*`) {#flags-go_flag_}

| Flag | Name | Effect |
| ---: | :--- | :--- |
| 0x01 | IN_USE | interaction disabled while animating |
| 0x02 | LOCKED | needs key/spell/event; shows "Locked" |
| 0x04 | INTERACT_COND | cannot interact until condition met |
| 0x08 | TRANSPORT | object can carry units |
| 0x10 | NO_INTERACT | players cannot use it |
| 0x20 | NODESPAWN | never despawns (doors toggle state) |
| 0x40 | TRIGGERED | summoned/temporary object |

Source: `src/game/Objects/GameObjectDefines.h`.

---

## Data Fields by Type

<a id="f-data0"></a><a id="f-data1"></a><a id="f-data2"></a><a id="f-data3"></a><a id="f-data4"></a><a id="f-data5"></a><a id="f-data6"></a><a id="f-data7"></a><a id="f-data8"></a><a id="f-data9"></a><a id="f-data10"></a><a id="f-data11"></a><a id="f-data12"></a><a id="f-data13"></a><a id="f-data14"></a><a id="f-data15"></a><a id="f-data16"></a><a id="f-data17"></a><a id="f-data18"></a><a id="f-data19"></a><a id="f-data20"></a><a id="f-data21"></a><a id="f-data22"></a><a id="f-data23"></a>`data0..data23` meaning depends entirely on `type`; column numbers below = `dataN` index.
Source of truth: the `GameObjectInfo` union in `src/game/Objects/GameObjectDefines.h`.

> Types **4** BINDER, **14** MAP_OBJECT, **16** DUEL_ARBITER, **19** MAILBOX and
**28** LOTTERY_KIOSK carry no `data*` payload; their behaviour is
hard-coded.

### Type Index

| Type | Name | Purpose |
| :---: | :--- | :--- |
| 0 | DOOR | doors/gates, openable or scripted |
| 1 | BUTTON | buttons/levers |
| 2 | QUESTGIVER | object-based quest givers |
| 3 | CHEST | lootable chests |
| 4 | BINDER | spirit binder (set home) |
| 5 | GENERIC | misc props |
| 6 | TRAP | area traps casting spells |
| 7 | CHAIR | sittable benches |
| 8 | SPELL_FOCUS | spell focus requirement objects |
| 9 | TEXT | readable book pages |
| 10 | GOOBER | generic usable ("goober") objects |
| 11 | TRANSPORT | elevator-style transports (fixed path) |
| 12 | AREADAMAGE | damaging areas |
| 13 | CAMERA | plays a cinematic |
| 14 | MAP_OBJECT | reserved |
| 15 | MO_TRANSPORT | boats/zeppelins; see [Transports](../Transports.md) |
| 16 | DUEL_ARBITER | duel arbiter flag |
| 17 | FISHINGNODE | fishing bobber |
| 18 | SUMMONING_RITUAL | ritual summoning circles |
| 19 | MAILBOX | mailbox |
| 20 | AUCTIONHOUSE | auction house object |
| 21 | GUARDPOST | summons guards when used |
| 22 | SPELLCASTER | casts a spell on users |
| 23 | MEETINGSTONE | meeting stones |
| 24 | FLAGSTAND | BG flag stand (WSG) |
| 25 | FISHINGHOLE | fishing pools |
| 26 | FLAGDROP | dropped BG flag |
| 27 | MINI_GAME | client mini-games |
| 28 | LOTTERY_KIOSK | lottery kiosk |
| 29 | CAPTURE_POINT | capture points |
| 30 | AURA_GENERATOR | persistent aura emitters |

### Per-Type Data Fields

#### 0 - DOOR

data0 startOpen · data1 lockId -> Lock.dbc · data2 autoCloseTime (seconds x 65536) ·
data3 noDamageImmune · data4 openTextID · data5 closeTextID

#### 1 - BUTTON

Same as door for data0-2; plus data3 linkedTrap, data4 noDamageImmune, data5 large,
data6 openTextID, data7 closeTextID, data8 losOK.

#### 2 - QUESTGIVER

data0 lockId · data1 questList · data2 pageMaterial · data3 gossipID · data4 customAnim ·
data5 noDamageImmune · data6 openTextID · data7 losOK · data8 allowMounted · data9 large

#### 3 - CHEST

data0 lockId (Lock.dbc) · data1 lootId ->
[`gameobject_loot_template`](gameobject_loot_template.md).entry · data2 chestRestockTime ·
data3 consumable · data4/data5 min/max successful opens · data6 lootedEvent ·
data7 linkedTrap · data8 quest required to open · data9 level · data10 losOK ·
data11 leaveLoot · data12 notInCombat · data13 logLoot · data14 openTextID ·
data15 groupLootRules

#### 4 - BINDER

Spirit binder; sets home bind. No data payload.

#### 5 - GENERIC

data0 floatingTooltip · data1 highlight · data2 serverOnly · data3 large ·
data4 floatOnWater · data5 questID

#### 6 - TRAP

data0 lockId · data1 level · data2 radius · data3 spellId · data4 charges ·
data5 cooldown · data6 autoCloseTime · data7 startDelay · data8 serverOnly ·
data9 stealthed · data10 large · data11 stealthAffected · data12 openTextID ·
data13 closeTextID

#### 7 - CHAIR

data0 slots · data1 height · data2 onlyCreatorUse

#### 8 - SPELL_FOCUS

data0 focusId (SpellFocusObject.dbc) · data1 radius · data2 linkedTrap ·
data3 serverOnly · data4 questID · data5 large

#### 9 - TEXT

data0 pageID ([`page_text`](page_text.md).entry) · data1 language · data2 pageMaterial ·
data3 allowMounted

#### 10 - GOOBER

data0 lockId · data1 questId · data2 eventId · data3 autoCloseTime · data4 customAnim ·
data5 consumable · data6 cooldown · data7 pageId · data8 language · data9 pageMaterial ·
data10 spellId · data11 noDamageImmune · data12 linkedTrap · data13 large ·
data14 openTextID · data15 closeTextID · data16 losOK · data17 allowMounted ·
data18 floatingTooltip · data19 gossipID

#### 11 - TRANSPORT

Elevator-style transport on a fixed path.

data0 pause · data1 startOpen · data2 autoCloseTime (seconds x 65536)

#### 12 - AREADAMAGE

data0 lockId · data1 radius · data2 damageMin · data3 damageMax · data4 damageSchool ·
data5 autoCloseTime · data6 openTextID · data7 closeTextID

#### 13 - CAMERA

data0 lockId · data1 cinematicId · data2 eventID · data3 openTextID

#### 14 - MAP_OBJECT

Reserved; no data payload.

#### 15 - MO_TRANSPORT

Boats/zeppelins; see [Transports](../Transports.md).

data0 taxiPathId · data1 moveSpeed · data2 accelRate · data3/data4 start/stop events ·
data5 transportPhysics · data6 mapID

#### 16 - DUEL_ARBITER

Duel arbiter flag object; single spawn in game data.

#### 17 - FISHINGNODE

Fishing bobber. data0 unused · data1 lootId (defined in the union but not read by the core;
bobber loot comes from [`fishing_loot_template`](fishing_loot_template.md) keyed by zone/area id).

#### 18 - SUMMONING_RITUAL

data0 required casters · data1 spellId · data2 animSpell · data3 ritualPersistent ·
data4 casterTargetSpell · data5 casterTargetSpellTargets · data6 castersGrouped ·
data7 ritualNoTargetCheck

#### 19 - MAILBOX

Mailbox; no data payload.

#### 20 - AUCTIONHOUSE

data0 auctionHouseID (Alliance / Horde / neutral house id)

#### 21 - GUARDPOST

data0 creatureId of the guard summoned · data1 charges

#### 22 - SPELLCASTER

data0 spellId cast on the user · data1 charges · data2 partyOnly · data3 allowMounted ·
data4 large · data5 conditionID1 ([`conditions`](conditions.md))

#### 23 - MEETINGSTONE

data0 minLevel · data1 maxLevel · data2 areaID

#### 24 - FLAGSTAND

data0 lockId · data1 pickupSpell · data2 radius · data3 returnAura · data4 returnSpell ·
data5 noDamageImmune · data6 openTextID · data7 losOK

#### 25 - FISHINGHOLE

data0 radius · data1 lootId ([`gameobject_loot_template`](gameobject_loot_template.md).entry) ·
data2 minSuccessfulOpens · data3 maxSuccessfulOpens · data4 lockId

#### 26 - FLAGDROP

data0 lockId · data1 eventID · data2 pickupSpell · data3 noDamageImmune ·
data4 openTextID

#### 27 - MINI_GAME

Client mini-game object; unused in vanilla content.

data0 gameType

#### 28 - LOTTERY_KIOSK

Lottery kiosk; unused in vanilla content.

#### 29 - CAPTURE_POINT

Capture-point object (TBC-era mechanics; unused in vanilla content).

data0 radius · data1 spell · data2+ worldState / event ids per slot

#### 30 - AURA_GENERATOR

Emits an aura to players inside its radius.

data0 startOpen · data1 radius · data2+ aura/spell ids and conditions per slot
