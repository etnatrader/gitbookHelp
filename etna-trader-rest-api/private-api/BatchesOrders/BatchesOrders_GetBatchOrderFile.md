
<a name="batchesorders_getbatchorderfile"></a>
#### Export batch orders entities to CSV
```
GET /v{version}/batches/{batchId}/orders/export
```


##### Description
Export batch orders entities to CSV by batch ID


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**batchId**  <br>*required*|Batch identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**filter**  <br>*optional*|Orders batch filter query|string (String)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Requested CSV file with orders data|object|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



