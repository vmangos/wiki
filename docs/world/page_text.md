# page_text Table

Defines book/page text content with links to next pages.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`text`](#f-text) | longtext |  | NO |  |  |
| [`next_page`](#f-next_page) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Page text ID (referenced by [`item_template`](item_template.md).page_text).
- <a id="f-text"></a>**`text`** - Text content.
- <a id="f-next_page"></a>**`next_page`** - Next page ID for multi-page books. (see [`page_text`](page_text.md).entry (if > 0))
