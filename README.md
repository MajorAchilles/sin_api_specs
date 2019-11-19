
# Say It Now 
## Current Version:
`Version 1`

## General API structure:

`{METHOD} {domain}/api/v{versionNumber}/{resourcePath}`


### All API endpoints return data in the modified [jsend](https://github.com/omniti-labs/jsend) format: 
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

## Entities
* [Topics](./topics.md)
* [Polls](./polls.md)
* [Votes](./votes.md)
* [Users](./users.md) :construction:
* [User Created Polls](./userPolls.md) :construction:
* [Campaigns](./campaigns.md) :construction:

### Submit Vote

Endpoint:  `api/v1/votes`


### Create Poll : `api/v1/polls/create`


### Future endpoints
* **Get a single poll** `api/v1/polls/{pollId}`. This endpoint is an alias for  `api/v1/polls/{topic}/{pollId}`
* **Get All Votes**: `api/v1/votes/`
