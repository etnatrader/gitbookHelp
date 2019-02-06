
<a name="orders_getorders"></a>
#### Get orders
```
GET /v{version}/accounts/{accountId}/orders
```


##### Description
Get orders by type and statuses


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*|Account internal identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**filter**  <br>*optional*|Order filter query|string (String)||
|**Query**|**pageNumber**  <br>*required*|Page number|integer (int32)||
|**Query**|**pageSize**  <br>*required*|Page size|integer (int32)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Collection of order models|< [OrderModel](#ordermodel) > array|
|**400**|Filter query is invalid or contains unsupported operations|No Content|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



