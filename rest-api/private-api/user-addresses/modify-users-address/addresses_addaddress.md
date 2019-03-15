# Syntax

## Change address

```text
PUT /v{version}/users/{userId}/addresses
```

### Description

Change user address

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **userId**   _required_ | User identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Body** | **body**   _required_ | User address | [UserAddress](addresses_addaddress.md#useraddress) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | User address | [UserAddress](addresses_addaddress.md#useraddress) |
| **204** | Address for specified user was not found | &lt; string &gt; array |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`

