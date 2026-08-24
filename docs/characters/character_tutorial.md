# character_tutorial Table

Tutorial flags shown to newly created accounts/characters.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`account`](#f-account) | bigint(20) unsigned | PRI | NO |  | auto_increment |
| [`tut0`](#f-tut0) | int(11) unsigned |  | NO | 0 |  |
| [`tut1`](#f-tut1) | int(11) unsigned |  | NO | 0 |  |
| [`tut2`](#f-tut2) | int(11) unsigned |  | NO | 0 |  |
| [`tut3`](#f-tut3) | int(11) unsigned |  | NO | 0 |  |
| [`tut4`](#f-tut4) | int(11) unsigned |  | NO | 0 |  |
| [`tut5`](#f-tut5) | int(11) unsigned |  | NO | 0 |  |
| [`tut6`](#f-tut6) | int(11) unsigned |  | NO | 0 |  |
| [`tut7`](#f-tut7) | int(11) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-account"></a>**`account`** - Part of the primary key. Account id from [`account`](../realmd/account.md).id; tutorial state is tracked per account.
- <a id="f-tut0"></a>**`tut0`** - Bitmask marking which tutorial windows were already shown.
- <a id="f-tut1"></a>**`tut1`** - Bitmask marking which tutorial windows were already shown.
- <a id="f-tut2"></a>**`tut2`** - Bitmask marking which tutorial windows were already shown.
- <a id="f-tut3"></a>**`tut3`** - Bitmask marking which tutorial windows were already shown.
- <a id="f-tut4"></a>**`tut4`** - Bitmask marking which tutorial windows were already shown.
- <a id="f-tut5"></a>**`tut5`** - Bitmask marking which tutorial windows were already shown.
- <a id="f-tut6"></a>**`tut6`** - Bitmask marking which tutorial windows were already shown.
- <a id="f-tut7"></a>**`tut7`** - Bitmask marking which tutorial windows were already shown.
