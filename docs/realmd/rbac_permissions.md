# rbac_permissions Table

Definitions of RBAC permissions referenced by account grants and command bindings. Ids match `SEC_*` levels and extra fine-grained permissions used by the core.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(10) unsigned | PRI | NO |  |  |
| [`name`](#f-name) | varchar(64) |  | NO |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Permission id.
- <a id="f-name"></a>**`name`** - Human-readable permission label.

*Used together with [`rbac_account_permissions`](rbac_account_permissions.md) and [`rbac_command_permissions`](rbac_command_permissions.md).*
