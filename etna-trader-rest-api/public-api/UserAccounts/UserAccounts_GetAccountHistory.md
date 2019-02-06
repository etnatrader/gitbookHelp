
<a name="useraccounts_getaccounthistory"></a>
#### Get account history
```
GET /v{version}/accounts/{accountId}/history
```


##### Description
Provides account history items specified by query string


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*|Account identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**endDate**  <br>*required*|End date in utc ticks|string (date-time)||
|**Query**|**startDate**  <br>*required*|Start date in utc ticks|string (date-time)||
|**Query**|**step**  <br>*required*|Account value items count per request|integer (int32)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Array of account history items|< [AccountValueItem](#accountvalueitem) > array|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



