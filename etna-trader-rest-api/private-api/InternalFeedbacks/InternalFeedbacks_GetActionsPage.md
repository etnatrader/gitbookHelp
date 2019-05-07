
<a name="internalfeedbacks_getactionspage"></a>
#### Get feedbacks page
```
GET /v{version}/feedbacks
```


##### Description
Provides feedbacks paged result


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**filter**  <br>*optional*|Filter query|string (String)||
|**Query**|**isDesc**  <br>*required*|Sorting direction. Desc if true, otherwise is asc|boolean||
|**Query**|**pageNumber**  <br>*required*|Page number|integer (int32)||
|**Query**|**pageSize**  <br>*required*|Page size|integer (int32)||
|**Query**|**sortBy**  <br>*required*|Sorting field|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Feedbacks paging result|[PagingResult[FeedbackModel]](#pagingresult-feedbackmodel)|
|**400**|Filter query is invalid or contains unsupported operations|No Content|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



