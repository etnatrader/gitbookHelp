---
description: Create a new price alert
---

# Create Price Alert

### Overview

This POST endpoint enables you to create a new price alert for the user whose ID is provided in the request's body. Price alerts are essentially notifications that are sent to the user when the alert's conditions are satisfied by the market. For example, a user may have a price alert that will notify them when the price of the Apple stock exceeds $200.

{% hint style="warning" %}
In order to create a new price alert, you must use an [authorization token](../../authentication/requesting-tokens/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the ID of the user to whose account a new price alert should be added.
5. **model** \(body\). This is a JSON dictionary that contains information about the new price alert.

#### Body Syntax

Here's an example of the request body with the information about the new price alert:

```javascript
{
    "State": "New",
    "Operator": "GTEQ",
    "SecurityId": 4,
    "Field": "Bid",
    "Argument": 200,
    "ExpirationDate": 1550674384
}
```

{% hint style="warning" %}
All six parameters must be indicated in the body JSON; otherwise the price alerts will be improperly interpreted by the system.
{% endhint %}

Here's the final template for this API request:

```text
POST apiURL/v1.0/users/{userID}/pricealerts
```

### Response

In response to this API request, you'll receive a JSON file with a more detailed information about the newly created price alert.

```javascript
{
    "Id": 871,
    "State": "New",
    "CreatedDate": 1550588008,
    "Operator": "GTEQ",
    "SecurityId": 2829,
    "Field": "Bid",
    "Argument": 170,
    "ExpirationDate": 1550674384
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal identifier of the price alert. |
| State | This is the state of the price alert. Possible values: New, Expired, Completed, Stopped. |
| CreatedDate | This is the date on which the price alert was created \(in ticks\). |
| Operator | This is the condition of the price alert. Possible values: GTEQ \(greater or equal to\), LTEQ \(less than or equal to\). |
| SecurityId | This is the ID of the security for which the price alert is configured. |
| Field | This is the referent price for the price alert. Possible values: Ask, Bid, Last. |
| Argument | This is the price point at which the price alert will be triggered and the user will be notified. |
| ExpirationDate | This is the expiration date of the price alert \(in ticks\). |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to create a new price alert.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for creating new price alerts, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

So be sure to use the authorization token generated with an administrator's credentials.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

The following article covers the syntax for this API request in detail.

