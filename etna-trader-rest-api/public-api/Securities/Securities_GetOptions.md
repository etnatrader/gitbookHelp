
<a name="securities_getoptions"></a>
#### Get options
```
GET /v{version}/options
```


##### Description
Get options with filtering


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**desc**  <br>*required*|Is descendant order|boolean||
|**Query**|**filter**  <br>*optional*|Options filter query|string (String)||
|**Query**|**pageNumber**  <br>*required*|Target page number|integer (int32)||
|**Query**|**pageSize**  <br>*required*|Target page size|integer (int32)||
|**Query**|**sortField**  <br>*required*|Sort by field|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Options collection|< [OptionResource](#optionresource) > array|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



