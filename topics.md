# TOPICS
##  Get List of Topics
### `GET api/v1/topics`

Gets you the list of topics currently in use.

**Supported Query Parameters:** 

|Parameter| Values|Default Value|Multi-value| Description |Example|
| --- | --- | --- | :---: | --- | --- |
| `status` | `active`, `inactive` | `active`  | :x: | Filters the list of topics by their status. `active` topics are in use. `inactive` topics have been retired.|   `?status=inactive`|
| `owner` | `sin`, `{user-id}` | `sin`  | :x: | Filters the list of topics by their owner. As of now, only topics created by SIN are available.|   `?owner={some-user-id}`|
| `sortBy` | `label`, `weightage` | `label`  |  :x: |Sorts the list of query parameters by given key. Weightage is decided by product team to enforce a topic precedence bias.|   `?sortBy=label`|
| `location` | [ISO 3166 2 Letter Country Codes](https://www.iban.com/country-codes)| `in`|:white_check_mark: | The country codes used to localize topics. |`?location=uk`, `?location=in,us,fr,uk`|
| `language` | [ISO 639-2 2 Letter Language Codes](https://www.iban.com/country-codes)| `en`|:white_check_mark: | The language codes used to localize topics. |`?location=de`, `?location=en,hi,de,as`|
| `ageRange` | `10-14`, `14-18`,`18-25`, `25-35`, `35-60`, `60+` | |:white_check_mark: | The age range to filter topics.  |`?ageRange=10-14`,`?ageRange=10-14,14-18`|

**Returns:** 
```
data: [
	{
		id: xxxxxxx,
		label: "Destiny",
		i18n: {
			"en": "Destiny",
			"hi": "भाग्य",
			"es": "Destino",
			"jp": "宿命"
		},
		locations: ["in", "mx", "pr", "ag", "uk", "us", "jp"],
		ageRange: ["10-14", "14-18", "18-25", "25-35"],
		weightage: 100,
		status: "active",
		owner: "sin",
		creationDate: "2019-11-16T09:59:26.901Z",
		createdBy: "ulwyqpojfvefn8p5",
		updationDate: "2019-11-16T09:59:26.901Z",
		updatedBy: "ulwyqpojfvefn8p5"
	},
	{
		id: yyyyyyy,
		label: "Science",
		i18n: {
			"en": "Science",
			"de": "Wissenschaft",
			"it": "Scienza",
			"hb": "מדע"
		},
		locations: ["in", "is", "it", "ag", "uk", "us", "jp"],
		ageRange: ["10-14", "14-18", "18-25", "25-35, "35-60", "60+"],
		weightage: 90,
		status: "inactive",
		owner: "sin",
		creationDate: "2019-11-16T09:59:26.901Z",
		createdBy: "2r926m11dmwfrg5t",
		updationDate: "2019-11-17T10:19:26.901Z",
		updatedBy: "ulwyqpojfvefn8p5"
	}
]
```

## Create Topic : `POST api/v1/topics`

### `POST api/v1/topics`

Create a new topic.

**Request Body**

|      Key     |      Type     |    Required      |    Default Value    | Description |    Example      | 
|     ---      |     ---       |      :---:       |         ---         |     ---     |      ---        |
| `label`      |    `string`   |:white_check_mark:|                     | The label of the topic. This should be in english and is automatically included in the translation list. |`Movies`|
| `i18n`       |    `object`   |       :x:        |  `{ en: <Label> }`  | The list of translations against languages keys. |`{ "zh": "电影" }`|
| `locations`  |`array<string>`|       :x:        |                     | The list of countries to localize to. Leave empty for global context. |`["in", "uk", "us"]`|
| `ageRange`   |`array<string>`|       :x:        |                     | The age groups to target. Leave empty to target all. |`["in", "uk", "us"]`|
| `weightage`  |   `number`    |       :x:        |        `50`         | Weightage to be used to set precedence bias. |`40`|

**Example**
```
{
	label: "Movies",
	i18n: {
		"pr": "Filmes",
		"ru": "Фильмы",
		"zh": "电影"
	}, // List of alternative language codes and translations. English translations are ignored and label is picked.
	locations: [], // ISO Country codes or empty for global
	ageRange: [], // Valid age ranges or empty for all ranges
	weightage: 0, // Weightage value as per product team's requirement.
}
```

### `PATCH api/v1/topics`

Updates an existing topic.

**Request Body**

|      Key     |      Type     |    Required      | Description |
|     ---      |     ---       |      :---:       |     ---     |
| `id`         |    `string`   |:white_check_mark:| Id of topic to be updated |
| `label`      |    `string`   |       :x:        | Filters the list of topics by their status. `active` topics are in use. `inactive` topics have been retired. |
| `i18n`       |    `object`   |       :x:        | The list of translations against languages keys. |
| `locations`  |`array<string>`|       :x:        | The list of countries to localize to. Leave empty for global context. |
| `ageRange`   |`array<string>`|       :x:        | The age groups to target. Leave empty to target all. |
| `weightage`  |   `number`    |       :x:        | Weightage to be used to set precedence bias. |

**Example**
```
{
	id: "5g6pestjzkuwrnpu",
	label: "Movies",
	i18n: {
		"pr": "Filmes",
		"ru": "Фильмы",
		"zh": "电影"
	}, // List of alternative language codes and translations. English translations are ignored and label is picked.
	locations: [], // ISO Country codes or empty for global
	ageRange: [], // Valid age ranges or empty for all ranges
	weightage: 70, // Weightage value as per product team's requirement.
}
```
