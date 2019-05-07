
<a name="securities_getoptionbysymbol"></a>
#### Get option by symbol
```
GET /v{version}/options/{symbol}
```


##### Description
This API endpoint enables you to retrieve detailed information about a particular option by providing the ticker symbol under which it’s listed on the exchange.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**symbol**  <br>*required*|This is the ticker symbol of the option under which it’s listed on the exchange.|string||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Query**|**currency**  <br>*optional*|This is the currency in which the option is denominated (use it if you have two options with the same ticker but denominated in two different currencies).|string||
|**Query**|**exchange**  <br>*optional*|This is the exchange on which the option is listed (use it if you have two options with the same ticker but listed on two different exchanges).|string||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data containing detailed information about the enquired option is returned.|[OptionResource](#optionresource)|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**404**|Enquired option is non-existent in ETNA Trader.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Produces

* `application/json`
* `text/json`



