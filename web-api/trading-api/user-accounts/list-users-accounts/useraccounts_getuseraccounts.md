# Syntax

## Get user accounts

```
GET /v{version}/users/{userId}/accounts
```

### Description

This API endpoint returns the list of trading accounts bound to a particular user.

### Parameters

| Type       | Name                                                         | Description                                                                                                                           | Schema          | Default |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                  | string          |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                      | string          |         |
| **Path**   | <p><strong>userId</strong>  <br><em>required</em></p>        | This is the unique identifier of the user in ETNA Trader.                                                                             | integer (int32) |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string          | `"1"`   |

### Responses

| HTTP Code | Description                                                                                                            | Schema                                                                          |
| --------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **200**   | Successful request, returns the list of trading accounts bound to the user whose ID was specified in the request path. | < [UserAccountModel](useraccounts\_getuseraccounts.md#useraccountmodel) > array |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation.                      | No Content                                                                      |
| **403**   | The provided Et-App-Key is incorrect.                                                                                  | No Content                                                                      |
| **422**   | A validation error occurred while processing the request.                                                              | No Content                                                                      |
| **500**   | Internal server error                                                                                                  | No Content                                                                      |

### Produces

* `application/json`
* `text/json`
