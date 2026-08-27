# taxi_nodes Table

Defines taxi (flight master) nodes - location and mount creature IDs.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | smallint(3) unsigned | PRI | NO |  |  |
| [`build`](#f-build) | smallint(4) unsigned | PRI | NO |  |  |
| [`map_id`](#f-map_id) | mediumint(6) unsigned |  | NO | 0 |  |
| [`x`](#f-x) | float |  | NO | 0 |  |
| [`y`](#f-y) | float |  | NO | 0 |  |
| [`z`](#f-z) | float |  | NO | 0 |  |
| [`name`](#f-name) | varchar(256) |  | NO | '' |  |
| [`mount_creature_id1`](#f-mount_creature_id1) | smallint(5) unsigned |  | NO | 0 |  |
| [`mount_creature_id2`](#f-mount_creature_id2) | smallint(5) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Node ID.
- <a id="f-build"></a>**`build`** - Primary Key. Client build.
- <a id="f-map_id"></a>**`map_id`** - Map ID.
- <a id="f-x"></a>**`x`** - Node position in world space.
- <a id="f-y"></a>**`y`** - Node position in world space.
- <a id="f-z"></a>**`z`** - Node position in world space.
- <a id="f-name"></a>**`name`** - Node name.
- <a id="f-mount_creature_id1"></a>**`mount_creature_id1`** - Creature template entry of the flying mount display used at this node (Horde variant). (see [`creature_template`](creature_template.md).entry)
- <a id="f-mount_creature_id2"></a>**`mount_creature_id2`** - Alliance variant mount creature for the node.
