
<a name="orders_getorders"></a>
#### Get orders
```
GET /v{version}/accounts/{accountId}/orders
```


##### Description
This API endpoint enables you to retrieve a selection of orders filtered by a specific query.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**accountId**  <br>*required*|This is the unique identifier of the trading account whose filtered orders need to be retrieved.|integer (int32)||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Query**|**filter**  <br>*optional*|This is a filter query used to retrieve only those orders that satisfy the conditions of the query.|string (String)||
|**Query**|**pageNumber**  <br>*required*|This is the number of the page (all orders are split into pages).|integer (int32)||
|**Query**|**pageSize**  <br>*required*|This parameter indicates the number of orders from a particular page that must be returned in the response.|integer (int32)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data containing filtered orders is returned|< [OrderResource](#orderresource) > array|
|**400**|The filter query is invalid or contains unsupported operations|No Content|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



