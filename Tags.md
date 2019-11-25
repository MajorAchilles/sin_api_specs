# Tags

##  Gets the list of tags
### `GET api/v1/tags`

Gets the current list of tags
**Supported Query Parameters:** 

|Parameter| Values|Default Value|Multi-value| Description |Example|
| --- | --- | --- | :---: | --- | --- |
| `startsWith` | `string` |  |  :x: |Filters tags with the given starting string.|   `?startsWith="soc"`|


**Returns:** 
```
data: [
    {
        tagId: "tid1",
        title: "games"
    }, {
        tagId: "tid2",
        title: "movies"
    }, {
        tagId: "tid3",
        title: "news"
    }, {
        tagId: "tid4",
        title: "politics"
    }
]
```

## Create a new vote
### `POST api/v1/tags`

Creates a new tag

**Request Body**

|      Key     |      Type     |    Required      |    Default Value    | Description |    Example      | 
|     ---      |     ---       |      :---:       |         ---         |     ---     |      ---        |
| `title`      |    `string`   |:white_check_mark:|                     | The title of the new tag. |`literature`|


**Example**
```
{
    title: "literature"
}
```

**Returns:** 
```
data: {
    tagId: "tid9",
    title: "literature"
},
```
