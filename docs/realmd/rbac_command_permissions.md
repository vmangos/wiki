# rbac_command_permissions Table

Binds chat/console commands to the RBAC permission required to execute them.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`command`](#f-command) | varchar(128) | PRI | NO |  |  |
| [`permission_id`](#f-permission_id) | int(10) unsigned | PRI | NO |  |  |

---

## Field Breakdown

- <a id="f-command"></a>**`command`** - Part of the primary key. Chat/console command the binding applies to.
- <a id="f-permission_id"></a>**`permission_id`** - Part of the primary key. Permission required to execute this command.

*References [`rbac_permissions`](rbac_permissions.md); see [GM Commands](../GM-Commands.md).*
