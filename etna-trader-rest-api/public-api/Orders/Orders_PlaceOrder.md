
<a name="orders_placeorder"></a>
#### Place order
```
POST /v{version}/accounts/{accountId}/orders
```


##### Description
Place or verify order


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*|Account identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**dryRun**  <br>*optional*|Preview order place results without sending it to the market|boolean|`"false"`|
|**Body**|**body**  <br>*required*|Place order parameters|[CreateOrderModel](#createordermodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Placed order model|[OrderModel](#ordermodel)|
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



