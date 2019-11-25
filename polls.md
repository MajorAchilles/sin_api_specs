# POLLS

##  Get List of Polls
### `GET api/v1/polls`

Gets you the list of polls currently in use.

**Supported Query Parameters:** 

|Parameter| Values|Default Value|Multi-value| Description |Example|
| --- | --- | --- | :---: | --- | --- |
| `topic` | `{topicId}` |  |  :x: |Gets the polls related to the given topic.|   `?topic=label`|
| `owner` | `sin`, `{user-id}` | `sin`  | :x: | Filters the list of polls by their owner. As of now, only polls created by SIN are available.|   `?owner={some-user-id}`|

**Returns:** 
```
data: [
	{
		id: xxxxxxx,
		topicID: tpxxxxx,
		question: "Should Destiny 2 be free to play?",
		i18n: {
			"en": "Should Destiny 2 be free to play?",
			"hi": "क्या डेस्टिनी 2 को खेलने के लिए स्वतंत्र होना चाहिए?",
			"es": "¿Debería Destiny 2 jugar gratis?",
			"jp": "Destiny 2は無料でプレイできますか？"
		},
		options: [
			{
				id: 1,
				text: "Yes",
				i18n: {
					"en": "Yes",
					"hi": "हाँ",
					"es": "Si",
					"jp": "はい"
				}
			},
			{
				id: 2,
				text: "No",
				i18n: {
					"en": "Yes",
					"hi": "नहीं",
					"es": "No",
					"jp": "いや"
				}
			},
			{
				id: 3,
				text: "Maybe",
				i18n: {
					"en": "Yes",
					"hi": "शायद",
					"es": "Tal vez",
					"jp": "多分"
				}
			}
		],
		votes: [
			{
				optionKey: 1,
				voteCount: 2
			}, {
				optionKey: 2,
				voteCount: 0
			}, {
				optionKey: 3,
				voteCount: 4
			}, {
				optionKey: 4,
				voteCount: 9
			}
		],
		owner: "sin",
		creationDate: "2019-11-16T09:59:26.901Z",
		createdBy: "ulwyqpojfvefn8p5",
		updationDate: "2019-11-16T09:59:26.901Z",
		updatedBy: "ulwyqpojfvefn8p5"
	}
]
```

## Create a new poll

### `POST api/v1/polls`

Create a new poll.

**Request Body**

|      Key     |      Type     |    Required      |    Default Value    | Description |    Example      | 
|     ---      |     ---       |      :---:       |         ---         |     ---     |      ---        |
| `topicId`      |    `string`   |:white_check_mark:|                     | The topic this poll is part of. |`r1ks1r5y3wim66xw`|
| `question`      |    `string`   |:white_check_mark:|                     | Filters the list of polls by their status. `active` polls are in use. `inactive` polls have been retired. |`Did you go to the Katy Perry concert in Mumbai?`|
| `i18n`       |    `object`   |       :x:        |  `{ en: <Question> }`  | The list of translations against languages keys. |`{ "zh": "电影" }`|
| `options`  |`array<Objects>`|:white_check_mark:|                     | The list of options for this poll. Check details below. |`{ id: 1, text: "Yes" }, { id: 2, text: "No"}`|

**Example**
```
{
	topicID: tpxxxxx,
	question: "Should Destiny 2 be free to play?",
	i18n: {
		"en": "Should Destiny 2 be free to play?",
		"hi": "क्या डेस्टिनी 2 को खेलने के लिए स्वतंत्र होना चाहिए?",
		"es": "¿Debería Destiny 2 jugar gratis?",
		"jp": "Destiny 2は無料でプレイできますか？"
	},
	options: [
		{
			id: 1,
			text: "Yes",
			i18n: {
				"en": "Yes",
				"hi": "हाँ",
				"es": "Si",
				"jp": "はい"
			}
		},
		{
			id: 2,
			text: "No",
			i18n: {
				"en": "Yes",
				"hi": "नहीं",
				"es": "No",
				"jp": "いや"
			}
		},
		{
			id: 3,
			text: "Maybe",
			i18n: {
				"en": "Yes",
				"hi": "शायद",
				"es": "Tal vez",
				"jp": "多分"
			}
		}
	]
}
```

## Update an existing poll
### `PATCH api/v1/polls`

Updates an existing poll.

**Request Body**

|      Key     |      Type     |    Required      | Description |
|     ---      |     ---       |      :---:       |     ---     |
| `id`         |    `string`   |:white_check_mark:| Id of poll to be updated |
| `topicId`      |    `string`   |       :x:        |                     | The topic this poll is part of. |`r1ks1r5y3wim66xw`|
| `question`      |    `string`   |       :x:        |                     | Filters the list of polls by their status. `active` polls are in use. `inactive` polls have been retired. |`Did you go to the Katy Perry concert in Mumbai?`|
| `i18n`       |    `object`   |       :x:        |  `{ en: <Question> }`  | The list of translations against languages keys. |`{ "zh": "电影" }`|
| `options`  |`array<Objects>`|       :x:        |                     | The list of options for this poll. Check details below. |`{ id: 1, text: "Yes" }, { id: 2, text: "No"}`|

**Example**
```
{
	id: xxxxxxx,
	topicID: tpxxxxx,
	question: "Should Destiny 2 be free to play?",
	i18n: {
		"en": "Should Destiny 2 be free to play?",
		"hi": "क्या डेस्टिनी 2 को खेलने के लिए स्वतंत्र होना चाहिए?",
		"es": "¿Debería Destiny 2 jugar gratis?",
		"jp": "Destiny 2は無料でプレイできますか？"
	},
	options: [
		{
			id: 1,
			text: "Yes",
			i18n: {
				"en": "Yes",
				"hi": "हाँ",
				"es": "Si",
				"jp": "はい"
			}
		},
		{
			id: 2,
			text: "No",
			i18n: {
				"en": "Yes",
				"hi": "नहीं",
				"es": "No",
				"jp": "いや"
			}
		},
		{
			id: 3,
			text: "Not Sure",
			i18n: {
				"en": "Not Sure",
				"hi": "शायद",
				"es": "Tal vez",
				"jp": "多分"
			}
		}
	]
}
```

### `options` property

Options are the collection of responses available against a poll. There must be a minimum of two options in every poll, and can have a maximum of four.

**Structure of the options collection**
```
options: [
		{
			id: 1,
			text: "Yes",
			i18n: {
				"en": "Yes",
				"hi": "हाँ",
				"es": "Si",
				"jp": "はい"
			}
		},
		{
			id: 2,
			text: "No",
			i18n: {
				"en": "Yes",
				"hi": "नहीं",
				"es": "No",
				"jp": "いや"
			}
		}
	]
```
While create a poll, a minimum of two options must be passed. The `i18n` object is optional. The english translation (`en`) is auto-generated from the text. Any `en` translation string passed in the `i18n` object is ignored.
