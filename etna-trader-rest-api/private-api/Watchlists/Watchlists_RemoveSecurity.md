
<a name="watchlists_removesecurity"></a>
#### Removes security.
```
DELETE /v{version}/users/{userId}/watchlists/{watchlistId}/securities
```


##### Description
This API endpoint enables you to remove a security from an existing watchlist by providing the security’s ticker symbol, currency, and the exchange on which it’s listed.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**userId**  <br>*required*|This is the internal identifier of the user whose watchlist needs to be modified.|integer (int32)||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Path**|**watchlistId**  <br>*required*|This is the internal identifier of the watchlist from which the security will be removed.|integer (int32)||
|**Body**|**body**  <br>*required*|This is JSON data that contains information about the security that must be removed (ticker symbol, exchange, and currency).|[SecuritySignature](#securitysignature)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data containing the updated watchlist is returned.|[WatchlistModel](#watchlistmodel)|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**409**|The security couldn’t be removed from the watchlist due to some conflict.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



