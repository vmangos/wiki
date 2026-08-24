# character_duplicate_account Table

Detection data for characters suspected of being duplicated between accounts.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`account`](#f-account) | int(11) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-account"></a>**`account`** - Account id from [`account`](../realmd/account.md).id; flagged by duplicate-detection tooling and reviewed manually.
