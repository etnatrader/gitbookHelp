
<a name="orders_cancelorder"></a>
#### Cancel order
```
DELETE /v{version}/accounts/{accountId}/orders/{orderId}
```


##### Description
This API endpoint enables you to cancel an existing order.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**accountId**  <br>*required*|This is the unique identifier of the trading account whose order needs to be cancelled.|integer (int32)||
|**Path**|**orderId**  <br>*required*|This is the ID of the order that needs to be cancelled.|integer (int32)||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|OK|object|
|**204**|The order was successfully cancelled|No Content|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**409**|A conflict has occurred when attempting to cancel the order.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



