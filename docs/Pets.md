# Pet System

How hunter/warlock pets and guardians are stored and powered. Sources:
`src/game/Objects/Pet.cpp`, `src/game/Objects/Pet.h`.

---

## Definition Tables (world DB)

| Table | Purpose |
| :--- | :--- |
| [`creature_template`](world/creature_template.md) | Pets are creatures: `type = CREATURE_TYPE_BEAST`, `pet_family` selects the pet family, `spell_list_id` / `pet_spell_list_id` define autocast pools. |
| [`pet_levelstats`](world/pet_levelstats.md) | Base HP/mana/armor/damage per creature entry and level. |
| [`pet_spell_data`](world/pet_spell_data.md) | Autocast spell pool per pet (referenced by `pet_spell_list_id`). |
| [`petcreateinfo_spell`](world/petcreateinfo_spell.md) | Spells a pet of a given entry knows from birth (patch-filtered). |
| [`pet_name_generation`](world/pet_name_generation.md) | Random name pools for wild/tameable pets. |

---

## Character-Side State

| Table ([characters DB](Characters-Database.md)) | Contents |
| :--- | :--- |
| [`character_pet`](characters/character_pet.md) | The stable: current pet + stabled pets, stats, rename state. |
| [`pet_aura`](characters/pet_aura.md) | Auras persisting across logout. |
| [`pet_spell`](characters/pet_spell.md) | Learned spells. |
| [`pet_spell_cooldown`](characters/pet_spell_cooldown.md) | Cooldowns. |

---

## Behaviour

- Controlled pets run `PetAI`; EventAI-marked pets are upgraded to `PetEventAI`
  (see [Creature AI System](AI-System.md)).
- Happiness/diet feed the loyalty system; growth uses [`pet_levelstats`](world/pet_levelstats.md).
- Charmed *creatures* (mind control) use the charm spell pool from
  [`creature_charm_spells`](world/creature_charm_spells.md).

---

## Related Pages

- [character_pet](characters/character_pet.md)
- [AI System](AI-System.md)
