# rbac_account_permissions Table

Grants or revokes RBAC permissions per account (`granted = 0` revokes an inherited permission).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`account_id`](#f-account_id) | int(11) | PRI | NO |  |  |
| [`permission_id`](#f-permission_id) | int(11) | PRI | NO |  |  |
| [`granted`](#f-granted) | tinyint(3) unsigned |  | NO | 1 |  |

---

## Field Breakdown

- <a id="f-account_id"></a>**`account_id`** - Part of the primary key. Account id (from [`account`](../realmd/account.md).id).
- <a id="f-permission_id"></a>**`permission_id`** - Part of the primary key. [`rbac_permissions`](rbac_permissions.md).id.
- <a id="f-granted"></a>**`granted`** - 1 grants, 0 explicitly revokes an inherited permission.

*References [`rbac_permissions`](rbac_permissions.md).*
