
<a name="internalsecurities_addsecurity"></a>
#### Add new security
```
POST /v{version}/internalsecurities
```


##### Description
Create new security


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1.0"`|
|**Body**|**body**  <br>*required*|Internal security model|[InternalSecurityResource](#internalsecurityresource)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Created internal security model|[InternalSecurityResource](#internalsecurityresource)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|Security already exists|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



