---
description: Approve an ACH relationship based on micro deposits
---

# Approve an ACH Relationship

### Overview

This POST endpoint enables you to approve a new ACH relationship that are based on micro deposits \(as opposed to Plaid-based ACH relationships\). When you attempt to create such relationship, you will see two values in your banking account statement \(e.g., `0.34` and `0.21`\). These two values will have to provided in this endpoint to confirm the creation of the ACH relationship.

{% hint style="warning" %}
This endpoint cannot be used for approving Plaid-based ACH relationships, as they are automatically approved.
{% endhint %}

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountId** \(path\). This is the [internal identifier](../user-accounts/list-users-accounts/) of the trading account in ETNA Trader to which the ACH relationship is bound.
5. **id** \(path\). This is the ID of the to-be-approved ACH relationship in ETNA Trader.
6. **model** \(body\). This is a JSON dictionary containing two values from the banking statement.

#### Request Body

The body of this request represents the two values from the banking statement. They can be provided in any order.

| Parameter | Description |
| :--- | :--- |
| Amount1 | This is one of the two values from the banking statement. |
| Amount2 | This is the other value from the banking statement. |

For example:

```javascript
{
  "Amount1": 0.32,
  "Amount2": 0.19
}
```

Here's the final template for this API request:

```text
POST apiURL/v1.0/accounts/{accountId}/ach-relationships/{id}/approve
```

### Response

In response to this API request, you will receive the 200 status code and no error message.

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to send a request to approve an ACH relationship.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

