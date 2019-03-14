
<a name="systemactions_executeclearingaction"></a>
#### Executes specified system action
```
PUT /v{version}/systemactions/clearing
```


##### Description
System actions list result


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1.0"`|
|**Body**|**body**  <br>*required*|List with handlers to be executed|[ClearingAction](#clearingaction)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Action were successfully executed|[ClearingAction](#clearingaction)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|An error occurred while executing the action|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



