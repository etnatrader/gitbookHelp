
<a name="webactions_getactionparameters"></a>
#### Get web action parameters
```
GET /v{version}/webactions/{actionId}/parameters
```


##### Description
Provides web action parameters list by action ID


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**actionId**  <br>*required*|Action ID|integer (int32)||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Action parameters collection|< [WebActionParameterMapModel](#webactionparametermapmodel) > array|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



