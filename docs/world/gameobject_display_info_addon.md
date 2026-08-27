# gameobject_display_info_addon Table

Addon data for game object display info - bounding box dimensions.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`display_id`](#f-display_id) | int(11) | PRI | NO | 0 |  |
| [`min_x`](#f-min_x) | float |  | NO | 0 |  |
| [`min_y`](#f-min_y) | float |  | NO | 0 |  |
| [`min_z`](#f-min_z) | float |  | NO | 0 |  |
| [`max_x`](#f-max_x) | float |  | NO | 0 |  |
| [`max_y`](#f-max_y) | float |  | NO | 0 |  |
| [`max_z`](#f-max_z) | float |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-display_id"></a>**`display_id`** - Primary Key. GO display id (GameObjectDisplayInfo.dbc).
- <a id="f-min_x"></a>**`min_x`** - Custom bounding box extents used for collision/LOS sizing.
- <a id="f-min_y"></a>**`min_y`** - Custom bounding box extents used for collision/LOS sizing.
- <a id="f-min_z"></a>**`min_z`** - Custom bounding box extents used for collision/LOS sizing.
- <a id="f-max_x"></a>**`max_x`** - Custom bounding box extents used for collision/LOS sizing.
- <a id="f-max_y"></a>**`max_y`** - Custom bounding box extents used for collision/LOS sizing.
- <a id="f-max_z"></a>**`max_z`** - Custom bounding box extents used for collision/LOS sizing.
