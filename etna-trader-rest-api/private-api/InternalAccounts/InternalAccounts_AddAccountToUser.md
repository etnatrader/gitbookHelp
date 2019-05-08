
<a name="internalaccounts_addaccounttouser"></a>
#### Add account to user
```
PUT /v{version}/accounts/{accountId}/users/{userId}
```


##### Description
This API endpoint enables you to bind a new or an existing trading account to an existing user.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**accountId**  <br>*required*|This is the internal identifier of the trading account which is to be bound to an existing user.|integer (int32)||
|**Path**|**userId**  <br>*required*|This is the internal identifier of the user to whom an existing trading account must be bound.|integer (int32)||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Query**|**accessType**  <br>*required*|This is the access level the user should have to this trading account.|enum (Full, ReadOnly, ClosePositionsOnly)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data is returned, containing the information about the user and their trading accounts.|[UserToAccountRelationModel](#usertoaccountrelationmodel)|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



