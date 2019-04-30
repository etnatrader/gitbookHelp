---
description: Remove an existing price alert
---

# Delete Price Alert

### Overview

This DELETE endpoint enables you to remove a particular price alert of the user whose ID is provided in the request. Price alerts are essentially notifications that are sent to the user when the alert's conditions are satisfied by the market. For example, a user may have a price alert that will notify them when the price of the Apple stock exceeds $200.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the ID of the user whose particular price alert's must be deleted.
5. **alertId** \(path\). This is the ID of the price alert that must be deleted.

Here's the final template for this API request:

```text
DELETE apiURL/v1.0/users/{userID}/pricealerts/{alertID}
```

### Response

In response to this API request, you'll receive an empty message and the 204 status code in case the alert was successfully deleted.

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to remove a particular price alert.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

The following article covers the syntax for this API request in detail.

