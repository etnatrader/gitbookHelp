
<a name="watchlists_addsecurtiy"></a>
#### Add security.
```
PUT /v{version}/users/{userId}/watchlists/{watchlistId}/securities
```


##### Description
Adds security to watchlist by security symbol and exchange.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**userId**  <br>*required*|User identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Path**|**watchlistId**  <br>*required*|Watchlist identifier|integer (int32)||
|**Body**|**body**  <br>*required*|Security symbol and exchange|[SecuritySignature](#securitysignature)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Changed watchlist with securities|[WatchlistModel](#watchlistmodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|Security was not found|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



