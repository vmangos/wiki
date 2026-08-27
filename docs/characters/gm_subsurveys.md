# gm_subsurveys Table

Optional follow-up survey answers attached to GM tickets.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`survey_id`](#f-survey_id) | int(10) unsigned | PRI | NO |  | auto_increment |
| [`subsurvey_id`](#f-subsurvey_id) | int(10) unsigned | PRI | NO | 0 |  |
| [`rank`](#f-rank) | int(10) unsigned |  | NO | 0 |  |
| [`comment`](#f-comment) | text |  | NO |  |  |

---

## Field Breakdown

- <a id="f-survey_id"></a>**`survey_id`** - Primary Key. Parent survey.
- <a id="f-subsurvey_id"></a>**`subsurvey_id`** - Primary Key. Individual question index.
- <a id="f-rank"></a>**`rank`** - Answer rating.
- <a id="f-comment"></a>**`comment`** - Per-question comment.
