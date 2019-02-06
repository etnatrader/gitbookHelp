
<a name="orders_replaceorder"></a>
#### Replace order
```
PUT /v{version}/accounts/{accountId}/orders/{orderId}
```


##### Description
Replace or verify order


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*||integer (int32)||
|**Path**|**orderId**  <br>*required*|Order internal identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**dryRun**  <br>*optional*|Preview order replace results without sending it to the market|boolean|`"false"`|
|**Body**|**body**  <br>*required*|Order modify params|[ModifyOrderModel](#modifyordermodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Replaced order model|[OrderModel](#ordermodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|Conflict|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



