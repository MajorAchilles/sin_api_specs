# Say It Now 
## VERSION 1


### Get Polls

Endpoint:  `api/v1/polls/<topic>`

### Submit Vote
Endpoint:  `api/v1/votes/submit`



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

[TOPICS](./Topics.md)

### Create Poll : `api/v1/polls/create`


### Future endpoints
* **Get a single poll** `api/v1/polls/{pollId}`. This endpoint is an alias for  `api/v1/polls/{topic}/{pollId}`
* **Get All Votes**: `api/v1/votes/`
