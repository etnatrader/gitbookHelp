# Syntax

## Modify price alert

```text
PUT /v{version}/users/{userId}/pricealerts/{alertId}
```

### Description

Modify price alert. Model properties "State",

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **alertId**   _required_ | Alert identifier | integer \(int32\) |  |
| **Path** | **userId**   _required_ | User identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Body** | **body**   _required_ | Price alert model | [PriceAlertEditableModel](../../definitions/#pricealerteditablemodel) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Updated price alert | [PriceAlertInfoModel](../../definitions/#pricealertinfomodel) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **409** | Conflict | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`

