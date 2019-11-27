# POLLS

##  Get List of Locations
### `GET api/v1/locations`

Gets you the list of countries and their codes.

**Supported Query Parameters:** 

|Parameter| Values|Default Value|Multi-value| Description |Example|
| --- | --- | --- | :---: | --- | --- |
| `startsWith` | `:name` |  |  :x: |Uses the given starting character to filter country names.|   `?topic=label`|

**Returns:** 
```
data: [
    {"code":"id","name":"Indonesia"},
    {"code":"ie","name":"Ireland"},
    {"code":"il","name":"Israel"},
    {"code":"im","name":"Isle of Man"},
    {"code":"in","name":"India"},
    {"code":"iq","name":"Iraq"},
    {"code":"ir","name":"Iran, Islamic Republic of"},
    {"code":"is","name":"Iceland"},
    {"code":"it","name":"Italy"}
]
```
