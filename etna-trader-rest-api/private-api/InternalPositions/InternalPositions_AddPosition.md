
<a name="internalpositions_addposition"></a>
#### Add position manually
```
POST /v{version}/positions
```


##### Description
Add position without sending order request


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1.0"`|
|**Query**|**recalculate**  <br>*required*|Recalculate account cash|boolean||
|**Body**|**body**  <br>*required*|Position to add|[InternalPositionModel](#internalpositionmodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Created position|[InternalPositionModel](#internalpositionmodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|Add position failed|[InternalPositionModel](#internalpositionmodel)|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



