# gm_surveys Table

Player satisfaction surveys submitted after a GM ticket was resolved.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`survey_id`](#f-survey_id) | int(10) unsigned | PRI | NO |  | auto_increment |
| [`guid`](#f-guid) | int(10) unsigned |  | NO | 0 |  |
| [`main_survey`](#f-main_survey) | int(10) unsigned |  | NO | 0 |  |
| [`overall_comment`](#f-overall_comment) | longtext |  | NO |  |  |
| [`create_time`](#f-create_time) | int(10) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-survey_id"></a>**`survey_id`** - Primary Key. Survey id.
- <a id="f-guid"></a>**`guid`** - Responding player.
- <a id="f-main_survey"></a>**`main_survey`** - Overall rating answer.
- <a id="f-overall_comment"></a>**`overall_comment`** - Free-text comment.
- <a id="f-create_time"></a>**`create_time`** - Submission time.
