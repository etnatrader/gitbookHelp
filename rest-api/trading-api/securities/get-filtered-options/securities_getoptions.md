# Syntax

## Get options

```text
GET /v{version}/options
```

### Description

Get options with filtering

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Query** | **desc**   _required_ | Is descendant order | boolean |  |
| **Query** | **filter**   _optional_ | Options filter query | string \(String\) |  |
| **Query** | **pageNumber**   _required_ | Target page number | integer \(int32\) |  |
| **Query** | **pageSize**   _required_ | Target page size | integer \(int32\) |  |
| **Query** | **sortField**   _required_ | Sort by field | string |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Options collection | &lt; [OptionResource](../../definitions/#optionresource) &gt; array |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

