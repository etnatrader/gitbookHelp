
<a name="orders_previewmodifyorder"></a>
#### Verify replacing order
```
PUT /v{version}/accounts/{accountId}/preview/orders/{orderId}
```


##### Description
This API endpoint enables you to validate updated information about an order that needs to be modified.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**accountId**  <br>*required*|This is the unique identifier of the trading account on which a new order is to be modified.|integer (int32)||
|**Path**|**orderId**  <br>*required*|This is the ID of the order that needs to be modified.|integer (int32)||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Body**|**body**  <br>*required*|This is JSON data that contains updated information about the order.|[ModifyOrderResource](#modifyorderresource)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|JSON data with the updated order information is returned, indicating if the order modification JSON is properly constructed (examine the isSuccessful parameter in the JSON file).|[VerifyOrderModel](#verifyordermodel)|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



