# Syntax

## Get account by Id

```text
GET /v{version}/accounts/{accountId}
```

### Description

Provides account items with specified identifier

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **accountId**   _required_ | Account identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Account model | &lt; [AccountModel](../../definitions/#accountmodel) &gt; array |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **404** | Specified account was not found | &lt; [AccountModel](../../definitions/#accountmodel) &gt; array |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

