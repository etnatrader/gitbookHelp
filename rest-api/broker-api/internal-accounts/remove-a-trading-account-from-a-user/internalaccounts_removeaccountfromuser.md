# Syntax

## Remove account from user

```text
DELETE /v{version}/accounts/{accountId}/users/{userId}
```

### Description

This API endpoint enables you to unbind a particular trading account from an existing user.

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | This is the authorization token that you retrieved from the first endpoint \(/token\). | string |  |
| **Header** | **Et-App-Key**   _required_ | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader. | string |  |
| **Path** | **accountId**   _required_ | This is the internal identifier of the trading account which is to be unbound from an existing user. | integer \(int32\) |  |
| **Path** | **userId**   _required_ | This is the internal identifier of the user from whom an existing trading account must be unbound. | integer \(int32\) |  |
| **Path** | **version**   _required_ | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string | `"1"` |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Successful request, JSON data is returned, containing updated information about the user and their trading accounts. | &lt; [UserToAccountRelationModel](internalaccounts_removeaccountfromuser.md#usertoaccountrelationmodel) &gt; array |
| **401** | The access level of the provided authorization token is not sufficient to perform this operation. | No Content |
| **403** | The provided Et-App-Key is incorrect. | No Content |
| **422** | A validation error occurred while processing the request. | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

