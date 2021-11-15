# Syntax

## Get token

```
POST /token
```

### Description

This API endpoint returns the authentication token that is used in all other API requests.

### Parameters

| Type       | Name                                                            | Description                                                                                          | Schema | Default          |
| ---------- | --------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ------ | ---------------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>optional</em></p>    | This is the authorization token that must be provided in the header of all requests except this one. | string | `""`             |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>       | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.     | string |                  |
| **Header** | <p><strong>Password</strong>  <br><em>optional</em></p>         | The password of the user on whose behalf the authentication is being performed.                      | string | `"testpassword"` |
| **Header** | <p><strong>PinCode</strong>  <br><em>optional</em></p>          | This is the user’s pincode.                                                                          | string | `""`             |
| **Header** | <p><strong>Username</strong>  <br><em>optional</em></p>         | This is the name of the user on whose behalf the authentication is being performed.                  | string | `"testusername"` |
| **Header** | <p><strong>VerificationCode</strong>  <br><em>optional</em></p> | This is the verification code sent by email or SMS (the second step of 2-FA).                        | string | `""`             |

### Responses

| HTTP Code | Description                                                                                                                                                                                                                                            | Schema     |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- |
| **200**   | The authentication is complete and the provided token can be used in other API requests.                                                                                                                                                               | No Content |
| **202**   | Several authentication steps have been taken, but the server is expecting additional parameters (like the verification code). Use the token from the response and provide the required additional parameters to complete the authentication procedure. | No Content |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation.                                                                                                                                                      | No Content |

### Produces

* `State`
* `Step`
* `Reason`
* `Token`

### Example HTTP response

#### Response 200

```javascript
{
  "State" : "Succeeded",
  "Token" : "VGhpcyBpcyBleGFtcGxlIHRva2Vu..."
}
```

#### Response 202

```javascript
{
  "Step" : "SecutityPin",
  "Reason" : "Invalid pin",
  "State" : "Expecting",
  "Token" : "VGhpcyBpcyBleGFtcGxlIHRva2Vu...."
}
```

#### Response 401

```javascript
{
  "State" : "Failed",
  "Step" : "SecutityPin",
  "Reason" : "Invalid pin"
}
```
