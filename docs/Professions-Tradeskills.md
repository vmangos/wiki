# Professions & Tradeskills

How crafting/gathering professions behave server-side. Sources:
`src/game/Handlers/SkillHandler.cpp`, craft skill-up handling (`Player::UpdateCraftSkill` in
`src/game/Objects/Player.cpp`), config keys in `mangosd.conf`.

---

## Learning & Caps

- Trainers teach professions; see the [Trainer & Vendor Guide](Trainer-Vendor-Guide.md).
  Tradeskill trainers use `trainer_type = 2`; `trainer_spell` identifies the profession.
- `MaxPrimaryTradeSkill` caps primary professions (vanilla = 2).
- Current/max values per player live in [`character_skills`](characters/character_skills.md);
  unlearned skills are remembered in [`character_forgotten_skills`](characters/character_forgotten_skills.md).

## Skill-Up Chances

Crafting/gathering a yellow-or-better recipe rolls for a skill point using the colour of the
craft (`SkillChance.*`, defaults shown):

| Recipe difficulty | Chance |
| :--- | :---: |
| Orange | 100 % |
| Yellow | 75 % |
| Green | 25 % |
| Gray | 0 % |

Per-system gain multipliers: `SkillGain.Crafting`, `SkillGain.Gathering`,
`SkillGain.Defense`, `SkillGain.Weapon`.

Gathering extras:

- `SkillChance.MiningSteps` / `SkillChance.SkinningSteps` - for mining/skinning, the skill-up
  chance is halved every N skill points (`0` = no decrease).
- Fishing failure/success tuning: `SkillFail.Loot.Fishing`, `SkillFail.Gain.Fishing`,
  `SkillFail.Possible.FishingPool`; zone base levels come from
  [`skill_fishing_base_level`](world/skill_fishing_base_level.md).

## Recipes & Bonuses

- Recipe lists per trainer: [`npc_trainer`](world/npc_trainer.md) /
  [`npc_trainer_template`](world/npc_trainer_template.md); rank chains follow
  [`spell_chain`](world/spell_chain.md).
- Bonus effects while crafting (e.g. extra items from tools/talent-like spells) are handled by
  spell-affect scripts bound through the [`spell_template`](world/spell_template.md)
  `script_name` column.
- Specialisations (Gnomish/Goblin engineering etc.) are plain spells: learning the spec spell
  gates its recipes via normal requirements.

## Discovery Systems

Vanilla-era random recipe *discovery* is not database-driven in this codebase; scripted cases
are implemented as spell/script effects. Do not expect a discovery table.

---

## Related Pages

- [skill_line_ability](world/skill_line_ability.md)
- [Trainer & Vendor Guide](Trainer-Vendor-Guide.md)
- [XP & Leveling Formulas](XP-and-Leveling.md)
