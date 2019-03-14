
<a name="internalaccounts_createdepositpayment"></a>
#### Add withdrowal payment to account
```
POST /v{version}/accounts/{accountId}/deposit
```


##### Description
Add withdrowal payment to specified account


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**accountId**  <br>*required*|Account identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1.0"`|
|**Query**|**depositValue**  <br>*required*|Withdrowal|number (double)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Current amount|[PaymentInfoModel](#paymentinfomodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



