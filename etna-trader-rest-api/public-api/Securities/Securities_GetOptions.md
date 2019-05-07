
<a name="securities_getoptions"></a>
#### Get options
```
GET /v{version}/options
```


##### Description
This API endpoint enables you to retrieve retrieve a collection of options filtered by a specific query.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Query**|**desc**  <br>*required*|This is a boolean field that indicates if the returned options should be sorted in descending (true) or ascending (false) order.|boolean||
|**Query**|**filter**  <br>*optional*|This is a filter query used to retrieve only those options that satisfy the conditions of the query.|string (String)||
|**Query**|**pageNumber**  <br>*required*|This is the page number (all options are split into pages).|integer (int32)||
|**Query**|**pageSize**  <br>*required*|This is the number of options that should be retrieved from the specified page.|integer (int32)||
|**Query**|**sortField**  <br>*required*|This is the field by which all retrieved options should be sorted.|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data is returned, containing the collection of filtered options.|< [OptionResource](#optionresource) > array|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



