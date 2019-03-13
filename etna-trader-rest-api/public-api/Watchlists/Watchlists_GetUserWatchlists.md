
<a name="watchlists_getuserwatchlists"></a>
#### Get user watchlists
```
GET /v{version}/users/{userId}/watchlists
```


##### Description
Retrieves all watchlists belongs to specified user. If parameter includeSecurities set to true watchlists all securities will be included.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**userId**  <br>*required*|User identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1.0"`|
|**Query**|**includeSecurities**  <br>*required*|Include list of wathlist securities in result model|boolean||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|User watchlists collection|< [WatchlistModel](#watchlistmodel) > array|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



