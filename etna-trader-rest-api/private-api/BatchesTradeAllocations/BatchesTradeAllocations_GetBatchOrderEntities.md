
<a name="batchestradeallocations_getbatchorderentities"></a>
#### Get order entities from batch
```
GET /v{version}/batches/{batchId}/allocations
```


##### Description
Get order entities from batch by internal batch Id


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**batchId**  <br>*required*|Order batch identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**filter**  <br>*optional*|Order filter query|string (String)||
|**Query**|**isDesc**  <br>*required*|Descending sort if true|boolean||
|**Query**|**pageNumber**  <br>*required*|Page number|integer (int32)||
|**Query**|**pageSize**  <br>*required*|Page size|integer (int32)||
|**Query**|**sortBy**  <br>*required*|Sort field name|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Requested batch order entities|< [BatchTradeAllocationMapModel](#batchtradeallocationmapmodel) > array|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



