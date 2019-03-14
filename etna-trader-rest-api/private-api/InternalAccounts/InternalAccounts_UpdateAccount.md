
<a name="internalaccounts_updateaccount"></a>
#### Update account
```
PUT /v{version}/accounts/{accountId}
```


##### Description
Update specified account.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*|Account identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1.0"`|
|**Body**|**body**  <br>*required*|Account update model|[AccountEditableModel](#accounteditablemodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Updated account model|[AccountModel](#accountmodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



