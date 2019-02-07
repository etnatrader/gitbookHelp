# Syntax

## Get securities by mask

```text
GET /v{version}/securities
```

### Description

Provides securities collection by specified mask

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1"` |
| **Query** | **mask**   _required_ | Mask to search by | string |  |
| **Query** | **maxCount**   _required_ | Maximum securities count | integer \(int32\) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Securities models collection | &lt; [SecurityModel](securities_getsecurities.md#securitymodel) &gt; array |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

