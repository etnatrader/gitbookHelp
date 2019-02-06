
<a name="internalusers_getusers"></a>
#### Get users
```
GET /v{version}/users
```


##### Description
Provides sorted users collection


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**filter**  <br>*optional*||string (String)||
|**Query**|**isDesc**  <br>*required*||boolean||
|**Query**|**pageNumber**  <br>*required*||integer (int32)||
|**Query**|**pageSize**  <br>*required*||integer (int32)||
|**Query**|**sortBy**  <br>*required*||string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Users collection|[PagingResult[IList[UserModel]]](#pagingresult-ilist-usermodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



