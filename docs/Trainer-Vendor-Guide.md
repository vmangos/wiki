# Trainer & Vendor Setup Guide

Everything needed to build functional trainers and vendors. Sources:
`ObjectMgr::LoadNPC*` in `src/game/ObjectMgr.cpp`, tables
[`npc_trainer`](world/npc_trainer.md)/[`npc_vendor`](world/npc_vendor.md) and their templates.

---

## Trainers

### Requirements on the NPC

1. [`creature_template`](world/creature_template.md).npc_flags must include `TRAINER` (0x10).
2. `trainer_type` selects the trainer window (`enum TrainerType`,
   `src/game/Objects/CreatureDefines.h`):
   | Value | Type |
   | :---: | :--- |
   | 0 | Class trainer |
   | 1 | Mounts trainer |
   | 2 | Tradeskills (professions) |
   | 3 | Pets |
3. `trainer_class` (for class trainers) restricts which players may use the NPC.
4. `trainer_spell` - spell that identifies the profession taught (tradeskill trainers).
5. Optional greeting text via [`npc_trainer_greeting`](world/npc_trainer_greeting.md).

### Teaching Spells

```sql
INSERT INTO npc_trainer (entry, spell, spellcost, reqskill, reqskillvalue, reqlevel)
VALUES (90001, 133 /*Fireball*/, 120, 0, 0, 1);
```

- `spell`: the *learned* spell id; rank chains from [`spell_chain`](world/spell_chain.md)
  let you teach only the highest rank; the core offers all ranks automatically.
- `reqskill`/`reqskillvalue`: profession requirement (e.g. requires 150 Enchanting).
- `reqlevel`: character level gate.
- Row with `spell = 0` acts as a **header** (category label) when followed by spells sharing
  the next rows' grouping.

### Templates

Instead of repeating lists per NPC, bind many NPCs to one list:

```sql
UPDATE creature_template SET trainer_id = 42 WHERE entry IN (90001, 90002);
INSERT INTO npc_trainer_template (entry, spell, spellcost, reqlevel) VALUES
(42, 133, 120, 1), (42, 143, 240, 6);
```

A trainer uses either its own [`npc_trainer`](world/npc_trainer.md) rows or its `trainer_id` template, not both.

---

## Vendors

### Basic Setup

```sql
UPDATE creature_template SET npc_flags = npc_flags | 4 WHERE entry = 90003;

INSERT INTO npc_vendor (entry, item, maxcount, incrtime, item_template_flags_note)
VALUES (90003, 2589 /*Linen Cloth*/, 0, 0, NULL);
```

- `maxcount = 0` → unlimited stock.
- `maxcount > 0` + `incrtime` → restocking limited supply (items sold per interval).
- `condition_id` gates visibility per player ([conditions](world/conditions.md)).

### Extended Vendor Columns

Extended columns such as `extended_cost` (honour tokens) are TBC-era but tolerated;
in vanilla pricing comes solely from the item's `BuyPrice`.

### Templates

Same idea as trainers: set [`creature_template`](world/creature_template.md).vendor_id, fill
[`npc_vendor_template`](world/npc_vendor_template.md) with the shared stock.

---

## Common Mistakes

| Symptom | Cause |
| :--- | :--- |
| "I don't trade with you" | missing npc_flag, or faction hostility |
| Items invisible for some players | a `condition_id` filtering them out |
| Trainer window empty | wrong `trainer_type`/`trainer_class`, or spell not in `Items.dbc`/trainer list |
| Rank N+1 offered before rank N | broken [`spell_chain`](world/spell_chain.md) links |

---

## Related Pages

- [npc_trainer](world/npc_trainer.md) · [npc_vendor](world/npc_vendor.md)
- [Trainer greeting texts](world/npc_trainer_greeting.md)
