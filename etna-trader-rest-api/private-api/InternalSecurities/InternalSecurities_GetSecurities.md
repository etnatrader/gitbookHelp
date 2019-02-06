
<a name="internalsecurities_getsecurities"></a>
#### Get securities by symbol
```
GET /v{version}/internalsecurities
```


##### Description
Provides securities collection by specified symbol


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**pageNumber**  <br>*required*|Page number|integer (int32)||
|**Query**|**pageSize**  <br>*required*|Page size|integer (int32)||
|**Query**|**symbol**  <br>*required*|Symbol to search by|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Internal securities models collection|[PagingResult[InternalSecurityModel]](#pagingresult-internalsecuritymodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



