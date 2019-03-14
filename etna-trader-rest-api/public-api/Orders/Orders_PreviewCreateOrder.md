
<a name="orders_previewcreateorder"></a>
#### Verify placing order
```
POST /v{version}/accounts/{accountId}/preview/orders
```


##### Description
Preview order place results without sending it to the market


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*|Account identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1.0"`|
|**Query**|**currency**  <br>*optional*|target currency, optional|string||
|**Query**|**exchange**  <br>*optional*|target exchange, optional|string||
|**Body**|**body**  <br>*required*|Place order parameters|[CreateOrderResource](#createorderresource)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Placing order preview result|[VerifyOrderModel](#verifyordermodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



