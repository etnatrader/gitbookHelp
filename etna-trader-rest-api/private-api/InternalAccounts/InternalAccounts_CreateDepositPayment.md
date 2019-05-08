
<a name="internalaccounts_createdepositpayment"></a>
#### Add withdrowal payment to account
```
POST /v{version}/accounts/{accountId}/deposit
```


##### Description
This API endpoint enables you to deposit funds into an existing trading account.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**accountId**  <br>*required*|This is the internal identifier of the trading account into which the funds are being deposited.|integer (int32)||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Query**|**depositValue**  <br>*required*|This is the amount of funds that need to be deposited into the trading account.|number (double)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data is returned, containing the deposited amount.|[PaymentInfoModel](#paymentinfomodel)|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



