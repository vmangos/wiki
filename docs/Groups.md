# Groups & Parties

Party/raid formation and their instance bindings.

---

## Tables

| Table ([characters DB](Characters-Database.md)) | Purpose |
| :--- | :--- |
| [`groups`](characters/groups.md) | Group header: leader, loot method/master, raid flag. |
| [`group_member`](characters/group_member.md) | Member list with assistant flags/subgroups for raids. |
| [`group_instance`](characters/group_instance.md) | Instance saves owned by the group (see [Instances](Instances.md)). |

Groups are persisted so a crash/restart can rebuild raid rosters; disbanding cleans the rows.

---

## Creature Groups vs Player Groups

Do not confuse with [creature groups](world/creature_groups.md) ([`creature_groups`](world/creature_groups.md) table):
those are NPC packs (formations, shared aggro) configured in the world database, while this
page covers *player* parties stored in the characters database.

Loot rules from [`groups`](characters/groups.md) interact with kill credit: quest kills use group sharing rules,
and EventAI events like `EVENT_T_GROUP_MEMBER_DIED` react to pack members via creature groups.

---

## Related Pages

- [Instances & Resets](Instances.md)
- [creature_groups](world/creature_groups.md)
