
<a name="batches_createbatch"></a>
#### Modify existing order batch
```
PUT /v{version}/batches/{batchId}
```


##### Description
Modify existing order batch


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**batchId**  <br>*required*|Order batch identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Body**|**body**  <br>*required*|Modified order batch model|[BatchMapModel](#batchmapmodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Modified batch model|[BatchMapModel](#batchmapmodel)|
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



