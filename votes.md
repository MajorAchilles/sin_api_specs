# VOTES

##  Get Vote Count for a given poll
### `GET api/v1/polls/{pollID}/votes`

Gets you the metadata of the votes for the given poll.

**Supported Query Parameters:** 
_N/A_

**Returns:** 
```
data: {
    pollID: pidxxxxx,
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
    ]
}
```


##  Get List of Votes 
### `GET api/v1/votes`

Gets you the the votes casted.

**Supported Query Parameters:** 

|Parameter| Values|Default Value|Multi-value| Description |Example|
| --- | --- | --- | :---: | --- | --- |
| `pollID` | `:pollId` |  |  :x: |Gets the votes related to a given poll.|   `?pollID=:pollId`|
| `caster` | `:user-id` | `*`  | :x: | Filters the list of votes by their caster. |   `?caster=:user-id`|

**Returns:** 
```
data: [
    {
        id: xxxxxxx,
        pollID: tpxxxxx,
        optionKey: 1,
        creationDate: "2019-11-16T09:59:26.901Z",
        createdBy: "udxxxxx"
    }
]
```


## Submit a new vote
### `POST api/v1/polls/:pollId/votes`

Submits a vote. Returns the updated vote metadata for the given poll.

**Request Body**

|      Key     |      Type     |    Required      |    Default Value    | Description |    Example      | 
|     ---      |     ---       |      :---:       |         ---         |     ---     |      ---        |
| `optionKey`      |    `string`   |:white_check_mark:|                     | The unique key of the option selected by the user. |`1`|
| `optionKeys`      |    `string`   |:construction:|                     | [In Progress] To be used for multi option voting. |N/A|


**Example**
```
{
    optionKey: 2
}
```

**Returns:** 
```
data: {
    pollID: pidxxxxx,
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
    ]
}
```
