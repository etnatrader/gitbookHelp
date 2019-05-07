
<a name="batches_archiveorderbatch"></a>
#### Archive existing order batch
```
POST /v{version}/batches/{batchId}/archive
```


##### Description
Archive existing order batch


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
|**200**|OK|object|
|**204**|Batch successfully archived|No Content|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|An error occured in attempt to archive batch|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



