
<a name="internalaccounts_getaccountsbyid"></a>
#### Get account by Id
```
GET /v{version}/accounts/{accountId}
```


##### Description
Provides account items with specified identifier


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*|Account identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Account model|< [AccountModel](#accountmodel) > array|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**404**|Specified account was not found|< [AccountModel](#accountmodel) > array|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



