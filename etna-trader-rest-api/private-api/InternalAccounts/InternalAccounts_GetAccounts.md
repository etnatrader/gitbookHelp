
<a name="internalaccounts_getaccounts"></a>
#### Get all accounts
```
GET /v{version}/accounts
```


##### Description
This API endpoint enables you to retrieve the list of all trading accounts that have been created by the users of your company.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Query**|**filter**  <br>*optional*|This is a filter query used to retrieve only those trading accounts that satisfy the conditions of the query.|string (String)||
|**Query**|**isAscending**  <br>*required*|This is a boolean field that indicates if the returned trading accounts should be sorted in ascending (true) or descending (false) order.|boolean||
|**Query**|**pageNumber**  <br>*required*|This is the page number (all trading accounts are split into pages).|integer (int32)||
|**Query**|**pageSize**  <br>*required*|This is the number of trading accounts that should be retrieved from the specified page.|integer (int32)||
|**Query**|**propertyName**  <br>*required*|This is the field by which the retrieved trading accounts should be sorted. For example, if the value of this parameter is set to Cash, the retrieved trading accounts will be sorted by the accounts' cash balance.|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data is returned, containing the list of trading accounts.|[PagingResult[AccountModel]](#pagingresult-accountmodel)|
|**400**|Filter query is invalid or contains unsupported operations|No Content|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



