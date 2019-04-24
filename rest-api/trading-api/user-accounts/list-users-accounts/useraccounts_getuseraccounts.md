# Syntax

## Get user accounts

```text
GET /v{version}/users/{userId}/accounts
```

### Description

Provides collection of accounts bound to user

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **userId**   _required_ |  | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Collection of user account items | &lt; [UserAccountModel](../../definitions.md#useraccountmodel) &gt; array |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

