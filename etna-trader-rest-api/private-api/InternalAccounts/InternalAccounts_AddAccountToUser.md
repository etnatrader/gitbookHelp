
<a name="internalaccounts_addaccounttouser"></a>
#### Add account to user
```
PUT /v{version}/accounts/{accountId}/users/{userId}
```


##### Description
Ads account with specified identifier to user with specified identifier


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*|Account identifier|integer (int32)||
|**Path**|**userId**  <br>*required*|User identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**accessType**  <br>*required*|Account access type|enum (Full, ReadOnly, ClosePositionsOnly)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|User models and account access types|[UserToAccountRelationModel](#usertoaccountrelationmodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



