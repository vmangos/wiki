# Creature AI System

This page explains how VMaNGOS decides which AI controls a creature, and how the
`ai_name` and `script_name` columns of [`creature_template`](world/creature_template.md) interact with the built-in AI classes.

The selection logic is implemented in `FactorySelector::selectAI`
(`src/game/AI/CreatureAISelector.cpp`) and runs once when a creature spawns.

---

## Built-in AI Types

Registered in `AIRegistry::Initialize()` (`src/game/AI/CreatureAIRegistry.cpp`):

| `ai_name` value | Class | Purpose |
| :--- | :--- | :--- |
| *(empty)* | *see selection order below* | Let the core decide automatically |
| `EventAI` | `CreatureEventAI` | Table-driven AI using [`creature_ai_events`](world/creature_ai_events.md) / [`creature_ai_scripts`](world/creature_ai_scripts.md). The most common choice for custom content. |
| `BasicAI` | `BasicAI` | Generic combat AI without scripted behaviour. |
| `CritterAI` | `CritterAI` | Passive critters (rats, birds); flees when attacked. |
| `GuardAI` | `GuardAI` | City guards: attack players with negative reputation/flagged status. |
| `PetAI` | `PetAI` | Controlled pets (hunter/warlock pets). |
| `TotemAI` | `TotemAI` | Totems: cast a single spell on spawn. |
| `NullAI` | `NullCreatureAI` | Does nothing at all (also used for mind-controlled creatures). |
| `PetEventAI` | `PetEventAI` | EventAI variant for pets/guardians - same tables, pet-safe actions. |
| `GuardEventAI` | `GuardEventAI` | EventAI variant for guards - same tables, guard behaviour. |

> **Note:** `ScriptedAI`, escort/follower AI and instance scripts are **C++ scripts**, not
> `ai_name` values. They are selected through the `script_name` column instead.

---

## Selection Order

When a creature spawns, the first matching rule wins:

1. **Player-possessed creature** (mind control) → `NullCreatureAI`. The player drives the body; no AI interference.
2. **`script_name` match** - For normal creatures (not controlled pets, not charmed), if [`creature_template`](world/creature_template.md).script_name matches a C++ script registered by the script library, that AI is used. This overrides everything below.
3. **Controlled pet or charmed creature** → `PetAI`.
4. **Totem** → `TotemAI`.
5. **`ai_name = "EventAI"` on a pet** → `PetEventAI`; **on a guard** → `GuardEventAI`. (Prevents table-driven AI from breaking pet/guard behaviour.)
6. **`ai_name` lookup** - any other non-empty `ai_name` is looked up in the registry above.
7. **Guard flag** → `GuardAI`.
8. **Creature type = critter** → `CritterAI`.
9. **Permit-based pick** - remaining AIs are asked how well they suit the creature (`Permissible`): generic AIs answer `PERMIT_BASE_NORMAL` (100), special-purpose ones `PERMIT_BASE_SPECIAL` (200), unsuitable ones `PERMIT_BASE_NO` (-1). Highest score wins.
10. **Fallback** → `NullCreatureAI`.

---

## Practical Guidelines

- **Custom scripted NPCs**: prefer `EventAI` + [`creature_ai_events`](world/creature_ai_events.md).
  Use `script_name` only for behaviour that exists as a C++ script in `src/scripts`.
- **Pets with EventAI events**: set `ai_name = "EventAI"` and let rule 5 upgrade it to `PetEventAI`;
  setting it explicitly to `PetEventAI` also works.
- **Completely static NPCs** (decorations, props): leave `ai_name` empty or use `NullAI` to save CPU.
  An empty `ai_name` resolves to `BasicAI` via permit scoring.

---

## Related Pages

- [creature_ai_events](world/creature_ai_events.md) - event triggers for EventAI
- [creature_ai_scripts](world/creature_ai_scripts.md) - actions executed by EventAI events
- [DB Script Tables](DB-Script-Tables.md) - the command set available to EventAI actions
- [creature_template](world/creature_template.md) - `ai_name` / `script_name` columns
