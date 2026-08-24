# Scripts Library

The C++ script library lives in `src/scripts/` and is bound to the database through the
`ScriptName` columns ([`creature_template`](world/creature_template.md), [`gameobject_template`](world/gameobject_template.md), [`map_template`](world/map_template.md),
[`quest_template`](world/quest_template.md), …). This page maps the layout.

---

## Layout

| Directory | Contents |
| :--- | :--- |
| `src/scripts/eastern_kingdoms/` | Zone & dungeon scripts for EK (one folder per zone: `elwynn_forest`, `eastern_plaguelands`, …). |
| `src/scripts/kalimdor/` | Zone & dungeon scripts for Kalimdor. |
| `src/scripts/battlegrounds/` | BG hooks beyond the core implementations. |
| `src/scripts/spells/` | Spell-affect scripts registered by [`spell_template`](world/spell_template.md).ScriptName. |
| `src/scripts/world/` | World-wide scripts: special NPCs (`npcs_special.cpp`), generic GO scripts (`go_scripts.cpp`), event helpers (`elemental_invasions.cpp`, `fireworks_show.cpp`…). |
| `src/scripts/custom/` | Community additions. |

---

## Binding Rules

1. The DB row carries the script name, e.g.
   `UPDATE creature_template SET ScriptName='npc_flame_ring' WHERE entry=12345;`
2. At startup `ScriptLoader.cpp` registers all `AddSC…` functions; each script object adds
   itself to lookup maps keyed by that name.
3. At spawn, `FactorySelector::selectAI` consults the script map **before** any built-in AI -
   a matching `script_name` always wins ([AI System](AI-System.md)).

The same name must exist in exactly one script; duplicates are reported at load.

---

## When to Use C++ vs EventAI

| Use C++ scripts when… | Use [EventAI](AI-System.md) when… |
| :--- | :--- |
| custom boss mechanics with phases/timers | standard combat events |
| new spell behaviours | say/emote/summon/cast sequences |
| special gossip handling beyond tables | simple event-driven content |

DB-only content keeps the fork small and is editable with tools like
[ScriptEditor](https://github.com/brotalnia/scripteditor).

---

## Related Pages

- [AI System](AI-System.md)
- [Spell System](Spell-System.md)
