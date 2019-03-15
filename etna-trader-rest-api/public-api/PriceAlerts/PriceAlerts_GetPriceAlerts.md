
<a name="pricealerts_getpricealerts"></a>
#### Get price alerts
```
GET /v{version}/users/{userId}/pricealerts
```


##### Description
Provides price alerts collection related to specified user


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**userId**  <br>*required*|User identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1.0"`|
|**Query**|**isDesc**  <br>*required*|Sorting direction. Desc if true, otherwise is asc|boolean||
|**Query**|**pageNumber**  <br>*required*|Page number|integer (int32)||
|**Query**|**pageSize**  <br>*required*|Page size|integer (int32)||
|**Query**|**sortBy**  <br>*required*|Sorting field|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Price alerts collection|[PagingResult[PriceAlertInfoModel]](#pagingresult-pricealertinfomodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



