# Syntax

## Get users

```text
GET /v{version}/users
```

### Description

Provides sorted users collection

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Query** | **filter**   _optional_ |  | string \(String\) |  |
| **Query** | **isDesc**   _required_ |  | boolean |  |
| **Query** | **pageNumber**   _required_ |  | integer \(int32\) |  |
| **Query** | **pageSize**   _required_ |  | integer \(int32\) |  |
| **Query** | **sortBy**   _required_ |  | string |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Users collection | [PagingResult\[IList\[UserModel\]\]](internalusers_getusers.md#pagingresult-ilist-usermodel) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

