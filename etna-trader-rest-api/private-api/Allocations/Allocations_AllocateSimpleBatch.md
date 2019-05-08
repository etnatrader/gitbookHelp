
<a name="allocations_allocatesimplebatch"></a>
#### Create batch allocation request
```
POST /v{version}/allocations/simple
```


##### Description
This API endpoint enables you to create and send multiple allocation requests with one API call.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Body**|**body**  <br>*required*|This is a JSON dictionary that contains information about the new allocations.|< [SimpleAllocationRequest](#simpleallocationrequest) > array||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data is returned, containing an array of allocation requests’ details along with one extra parameter — IsSucceed — which indicates if the allocations have been successfully carried out.|< [AllocationResultInfo[SimpleAllocationRequest]](#allocationresultinfo-simpleallocationrequest) > array|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**409**|Failed allocation request result|< [AllocationResultInfo[SimpleAllocationRequest]](#allocationresultinfo-simpleallocationrequest) > array|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



