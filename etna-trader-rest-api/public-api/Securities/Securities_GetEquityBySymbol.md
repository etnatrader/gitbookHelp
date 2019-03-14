
<a name="securities_getequitybysymbol"></a>
#### Get equity by symbol
```
GET /v{version}/equities/{symbol}
```


##### Description
Get equity by symbol


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**symbol**  <br>*required*|Symbol, required|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1.0"`|
|**Query**|**currency**  <br>*optional*|Target currency, optional|string||
|**Query**|**exchange**  <br>*optional*|Target exchange, optional|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Equity resource|[EquityResource](#equityresource)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**404**|Resource was not found|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



