# Syntax

## Get token

```text
POST /token
```

### Description

Authentication method that provides token to access API.

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _optional_ | Authorization token, required on every step except first | string | `""` |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Header** | **Password**   _optional_ | User password, required | string | `"testpassword"` |
| **Header** | **PinCode**   _optional_ | User pin code, on demand | string | `""` |
| **Header** | **Username**   _optional_ | User login, required | string | `"testusername"` |
| **Header** | **VerificationCode**   _optional_ | User verification code, on demand | string | `""` |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Authentication complete and token is ready to use. | No Content |
| **202** | Several authentication steps are passed, but server is expecting additional parameters. Use a token from response and provide correct additional data to complete authentication procedure. | No Content |
| **401** | Authentication parameters determined as incorrect. | No Content |

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

