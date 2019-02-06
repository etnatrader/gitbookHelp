
<a name="addresses_addaddress"></a>
#### Change address
```
PUT /v{version}/users/{userId}/addresses
```


##### Description
Change user address


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**userId**  <br>*required*|User identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Body**|**body**  <br>*required*|User address|[UserAddress](#useraddress)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|User address|[UserAddress](#useraddress)|
|**204**|Address for specified user was not found|< string > array|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



