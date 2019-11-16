# Say It Now 
## VERSION 1
### All `{METHOD} {domain}/api/v{versionNumber}/{resourcePath}`


#### All API endpoints return data in the modified [jsend](https://github.com/omniti-labs/jsend) format: 
```
{
	status: {
		type: ""
		
		// Success: as is.
		// Error: Critical resource/logic/db failure.
		// Fail: "validation failures"
		// Other operation specific messages can be added here if required. eg: code: 404.
	},
	data: {
		// Application specific data goes here. Should be present only if status is success. Omit otherwise.
	},
	message: {
		title: "", // Relevant and mandatory messages,
		description: "" // If further explanations are required, empty otherwise. Key must be present.
		// Other operation specific messages can be added here if required. eg: stack, lineNo etc
	},
}
```


#### Examples: 

**Success** 
```
{
	status: {
		type: "success",
		code: 200
	},
	data: {
		pets: [ "dogs", "dogs", "fish" ]
	},
	message: {
		title: "3 resources found",
		description: ""
	}
}
```


**Fail** 
```
{
	status: {
		type: "fail"
	},
	message: {
		title: "Validation failed",
		description: "Gazorpazorp is not a pet for humans!",
		validationType: "Civilizational"
	}
}
```


**Error** 
```
{
	status: {
		type: "error",
		code: 404
	},
	message: {
		title: "Planet not found.",
		description: "The queried planet - Alderaan - is marked as destroyed by a death-star blast."
	}
}
```

### Get List of Topics :  `GET api/v1/topics`

Gets you the list of topics currently in use.

**Supported Query Parameters:** 

|Parameter| Values|Default Value|Multi-value| Description |Example|
 | --- | --- | --- | :---: | --- | --- |
| `status` | `active`, `inactive` | `active`  | :x: | Filters the list of topics by their status. `active` topics are in use. `inactive` topics have been retired.|   `?sortBy=label`|
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
			 "as": "भाग्य",
			 "es": "Destino",
			 "jp": "宿命"
		 },
		 locations: ["in", "mx", "pr", "ag", "uk", "us", "jp"],
		 ageRange: ["10-14", "14-18", "18-25", "25-35"],
		 weightage: 100,
		 status: "active"
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
		 "inactive"
	 }
]
```

### Create Topic : `POST api/v1/topics`


### Create Poll : `api/v1/polls/create`


### Get Polls

Endpoint:  `api/v1/polls/<topic>`

### Submit Vote
Endpoint:  `api/v1/votes/submit`



### Future endpoints
* **Get a single poll** `api/v1/polls/{pollId}`. This endpoint is an alias for  `api/v1/polls/{topic}/{pollId}`
* **Get All Votes**: `api/v1/votes/`
