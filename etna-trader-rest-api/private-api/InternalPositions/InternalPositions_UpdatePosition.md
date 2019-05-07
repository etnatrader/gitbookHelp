
<a name="internalpositions_updateposition"></a>
#### Update position manually
```
PUT /v{version}/positions/{positionId}
```


##### Description
Update position without sending order request


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**positionId**  <br>*required*|Position identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Body**|**body**  <br>*required*|Position to update|[InternalUpdatePosition](#internalupdateposition)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Updated position|[InternalPositionModel](#internalpositionmodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|Update position failed|[InternalPositionModel](#internalpositionmodel)|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



