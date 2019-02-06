
<a name="transactions_getactionspage"></a>
#### Get transactions page
```
GET /v{version}/accounts/{accountId}/transactions
```


##### Description
Provides transactions Paged result


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*|ID of specified account|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**filter**  <br>*optional*|Filter query|string (String)||
|**Query**|**isDesc**  <br>*required*|Sorting direction. Desc if true, otherwise is asc|boolean||
|**Query**|**pageNumber**  <br>*required*|Page number|integer (int32)||
|**Query**|**pageSize**  <br>*required*|Page size|integer (int32)||
|**Query**|**sortBy**  <br>*required*|Sorting field|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Transactions paging result|[PagingResult[TransactionMapModel]](#pagingresult-transactionmapmodel)|
|**400**|Filter query is invalid or contains unsupported operations|No Content|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



