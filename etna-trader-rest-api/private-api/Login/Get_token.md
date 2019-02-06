
<a name="get_token"></a>
#### Get token
```
POST /token
```


##### Description
Authentication method that provides token to access API.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*optional*|Authorization token, required on every step except first|string|`""`|
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Header**|**Password**  <br>*optional*|User password, required|string|`"testpassword"`|
|**Header**|**PinCode**  <br>*optional*|User pin code, on demand|string|`""`|
|**Header**|**Username**  <br>*optional*|User login, required|string|`"testusername"`|
|**Header**|**VerificationCode**  <br>*optional*|User verification code, on demand|string|`""`|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Authentication complete and token is ready to use.|No Content|
|**202**|Several authentication steps are passed, but server is expecting additional parameters. Use a token from response and provide correct additional data to complete authentication procedure.|No Content|
|**401**|Authentication parameters determined as incorrect.|No Content|


##### Produces

* `State`
* `Step`
* `Reason`
* `Token`


##### Example HTTP response

###### Response 200
```json
{
  "State" : "Succeeded",
  "Token" : "VGhpcyBpcyBleGFtcGxlIHRva2Vu..."
}
```


###### Response 202
```json
{
  "Step" : "SecutityPin",
  "Reason" : "Invalid pin",
  "State" : "Expecting",
  "Token" : "VGhpcyBpcyBleGFtcGxlIHRva2Vu...."
}
```


###### Response 401
```json
{
  "State" : "Failed",
  "Step" : "SecutityPin",
  "Reason" : "Invalid pin"
}
```



