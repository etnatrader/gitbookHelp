
<a name="get_token"></a>
#### Get token
```
POST /token
```


##### Description
This API endpoint returns the authentication token that is used in all other API requests.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*optional*|This is the authorization token that must be provided in the header of all requests except this one.|string|`""`|
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Header**|**Password**  <br>*optional*|The password of the user on whose behalf the authentication is being performed.|string|`"testpassword"`|
|**Header**|**PinCode**  <br>*optional*|This is the user’s pincode.|string|`""`|
|**Header**|**Username**  <br>*optional*|This is the name of the user on whose behalf the authentication is being performed.|string|`"testusername"`|
|**Header**|**VerificationCode**  <br>*optional*|This is the verification code sent by email or SMS (the second step of 2-FA).|string|`""`|


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|The authentication is complete and the provided token can be used in other API requests.|No Content|
|**202**|Several authentication steps have been taken, but the server is expecting additional parameters (like the verification code). Use the token from the response and provide the required additional parameters to complete the authentication procedure.|No Content|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|


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



