
<a name="securities_getequitybyid"></a>
#### Get equity by id
```
GET /v{version}/equities/{id}
```


##### Description
This API endpoint enables you to retrieve detailed information about a specific equity by providing its internal identifier in ETNA Trader.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**id**  <br>*required*|This is the internal identifier of the enquired equity in ETNA Trader.|integer (int32)||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data containing detailed information about the enquired security is returned.|[EquityResource](#equityresource)|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**404**|Enquired security is non-existent in ETNA Trader.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



