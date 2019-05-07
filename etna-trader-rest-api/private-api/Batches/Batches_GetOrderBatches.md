
<a name="batches_getorderbatches"></a>
#### Get order batches
```
GET /v{version}/batches
```


##### Description
Get orders batches page


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**filter**  <br>*optional*|Order filter query|string (String)||
|**Query**|**isDesc**  <br>*required*|Descending sort if true|boolean||
|**Query**|**pageNumber**  <br>*required*|Page number|integer (int32)||
|**Query**|**pageSize**  <br>*required*|Page size|integer (int32)||
|**Query**|**showArchived**  <br>*required*|Load archived batches too if true|boolean||
|**Query**|**sortBy**  <br>*required*|Sort field name|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Collection of order batches models|< [BatchMapModel](#batchmapmodel) > array|
|**400**|Filter query is invalid or contains unsupported operations|No Content|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



