
<a name="positions_getpositionbysymbol"></a>
#### Get positions by symbol
```
GET /v{version}/accounts/{accountId}/positions/{symbol}
```


##### Description
Retrieve all positions by specified symbol


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*|Account identifier|integer (int32)||
|**Path**|**symbol**  <br>*required*|Security symbol|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**currency**  <br>*optional*|Target currency, optional|string||
|**Query**|**exchange**  <br>*optional*|Target exchange, optional|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Target symbol positions|< [PositionResource](#positionresource) > array|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



