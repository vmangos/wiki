# gameobject_requirement Table

Gates *use* of a game object spawn behind world state: the linked creature must be **dead**, or
another game object must currently be **active**. Loaded by `ObjectMgr::LoadGameObjectRequirements`.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO |  | auto_increment |
| [`reqType`](#f-reqType) | int(3) unsigned |  | NO | 0 |  |
| [`reqGuid`](#f-reqGuid) | int(10) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. The [`gameobject`](gameobject.md) spawn being gated.
- <a id="f-reqType"></a>**`reqType`** - Requirement kind (`GameObjectUseRequireType`, `ObjectMgr.h`):

  | Value | Meaning | `reqGuid` refers to |
  | :---: | :--- | :--- |
  | 0 | `GOBJ_REQUIRE_DEAD_CREATURE` - usable only while the creature is dead | creature spawn guid |
  | 1 | `GOBJ_REQUIRE_ACTIVE_OBJECT` - usable only while the other object is spawned/active | gameobject spawn guid |

- <a id="f-reqGuid"></a>**`reqGuid`** - Creature or gameobject spawn guid satisfying the requirement (see
  `reqType`).

Invalid rows (unknown guids/types) are reported as DB errors at load and skipped.
