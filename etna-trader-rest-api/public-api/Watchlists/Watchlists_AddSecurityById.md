
<a name="watchlists_addsecuritybyid"></a>
#### Add security by Id.
```
PUT /v{version}/users/{userId}/watchlists/{watchlistId}/securities/{securityId}
```


##### Description
Adds security to watchlist by security Id.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**securityId**  <br>*required*|Security identifier|integer (int32)||
|**Path**|**userId**  <br>*required*|User identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1.0"`|
|**Path**|**watchlistId**  <br>*required*|Watchlist identifier|integer (int32)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Changed watchlist with securities|[WatchlistModel](#watchlistmodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|Conflict|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



