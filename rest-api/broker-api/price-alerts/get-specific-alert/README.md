---
description: Fetch information about a specific price alert
---

# Get Specific Alert

### Overview

This GET endpoint enables you to retrieve information about a particular price alert of the user whose ID is provided in the request. Price alerts are essentially notifications that are sent to the user when the alert's conditions are satisfied by the market. For example, a user may have a price alert that will notify them when the price of the Apple stock exceeds $200.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the ID of the user whose particular price alert's information needs to be retrieved.
5. **alertID** \(query\). This is the ID of the price alert whose information needs to be retrieved.

Here's the final template for this API request:

```text
GET apiURL/v1.0/users/{userID}/pricealerts/{alertID}
```

### Response

In response to this API request, you'll receive a JSON file with the detailed information about the price alert.

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

Here are some of the common mistakes that developers make when attempting to retrieve information about a particular price alert.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

The following article covers the syntax for this API request in detail.

