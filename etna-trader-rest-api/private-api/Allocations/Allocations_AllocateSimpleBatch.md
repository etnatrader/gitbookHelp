
<a name="allocations_allocatesimplebatch"></a>
#### Create batch allocation request
```
POST /v{version}/allocations/simple
```


##### Description
Executes several trade allocations requests


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Body**|**body**  <br>*required*|Allocation request models collection|< [SimpleAllocationRequest](#simpleallocationrequest) > array||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Succeeded allocation request result|< [AllocationResultInfo[SimpleAllocationRequest]](#allocationresultinfo-simpleallocationrequest) > array|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|Failed allocation request result|< [AllocationResultInfo[SimpleAllocationRequest]](#allocationresultinfo-simpleallocationrequest) > array|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



