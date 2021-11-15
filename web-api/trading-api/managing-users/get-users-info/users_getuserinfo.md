# Syntax

## Get user info by Id

```
GET /v{version}/users/{userId}/info
```

### Description

This API endpoint returns detailed information about the user.

### Parameters

| Type       | Name                                                         | Description                                                                                                                                                                                                             | Schema          | Default |
| ---------- | ------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                                                                                                    | string          |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                                                                                                        | string          |         |
| **Path**   | <p><strong>userId</strong>  <br><em>required</em></p>        | This is the unique identifier of the user in ETNA Trader. If the information is requested about the user whose Authorization token is provided in the request, simply use the ‘@me’ directive instead of the user’s ID. | integer (int32) |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.                                                                                   | string          | `"1"`   |

### Responses

| HTTP Code | Description                                                                                       | Schema                                               |
| --------- | ------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **200**   | The request is successful, JSON data with the user’s information is returned.                     | [UserInfoModel](users\_getuserinfo.md#userinfomodel) |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation. | No Content                                           |
| **403**   | The provided Et-App-Key is incorrect.                                                             | No Content                                           |
| **422**   | A validation error occurred while processing the request.                                         | No Content                                           |
| **500**   | Internal server error                                                                             | No Content                                           |

### Produces

* `application/json`
* `text/json`
