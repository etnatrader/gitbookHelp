
<a name="batchestradeallocations_createbatchorderentitiesfromfiles"></a>
#### Upload files to create new batch entities
```
POST /v{version}/batches/{batchId}/allocations
```


##### Description
Upload files to create new batch entities


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**batchId**  <br>*required*|Order batch identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Entities successfully added to batch|No Content|
|**400**|One or more files are empty or broken|No Content|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|One or more files has incorrect format|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



