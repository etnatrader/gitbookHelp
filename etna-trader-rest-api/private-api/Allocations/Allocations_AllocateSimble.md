
<a name="allocations_allocatesimble"></a>
#### Create allocation request
```
PUT /v{version}/allocations/simple
```


##### Description
Executes single trade allocation request


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Body**|**body**  <br>*required*|Allocation request model|[SimpleAllocationRequest](#simpleallocationrequest)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Succeeded allocation request result|[AllocationResultInfo[SimpleAllocationRequest]](#allocationresultinfo-simpleallocationrequest)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|Failed allocation request result|[AllocationResultInfo[SimpleAllocationRequest]](#allocationresultinfo-simpleallocationrequest)|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`


