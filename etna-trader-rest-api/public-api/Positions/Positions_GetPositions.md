
<a name="positions_getpositions"></a>
#### Get positions collection
```
GET /v{version}/accounts/{accountId}/positions
```


##### Description
Retrieve positions with filtering for specified account


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*|Account identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**desc**  <br>*required*|Is descendant|boolean||
|**Query**|**filter**  <br>*optional*|Positions filter query|string (String)||
|**Query**|**pageNumber**  <br>*required*|Page number|integer (int32)||
|**Query**|**pageSize**  <br>*required*|Page size|integer (int32)||
|**Query**|**sortField**  <br>*required*|Sort collection by field|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Collection of positions|[PagingResult[PositionResource]](#pagingresult-positionresource)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



