
<a name="securities_getsecurities"></a>
#### Get securities by mask
```
GET /v{version}/securities
```


##### Description
Provides securities collection by specified mask


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**mask**  <br>*required*|Mask to search by|string||
|**Query**|**maxCount**  <br>*required*|Maximum securities count|integer (int32)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Securities models collection|< [SecurityModel](#securitymodel) > array|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



