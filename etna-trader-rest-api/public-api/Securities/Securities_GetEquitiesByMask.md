
<a name="securities_getequitiesbymask"></a>
#### Get equity by mask
```
GET /v{version}/equities/lookup
```


##### Description
Get equity by mask


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**count**  <br>*required*|Response collection length|integer (int32)||
|**Query**|**mask**  <br>*required*|Mask to search for|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Equities collection|< [EquityResource](#equityresource) > array|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



