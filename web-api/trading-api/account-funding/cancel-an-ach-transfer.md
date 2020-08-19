---
description: Cancel an outstanding ACH Transfer
---

# Cancel an ACH Transfer

### Overview

This DELETE endpoint enables you to cancel an outstanding ACH deposit or withdrawal.

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountId** \(path\). This is the [internal identifier](../user-accounts/list-users-accounts/) of the trading account in ETNA Trader.
5. **transferId** \(path\). This is the ID of the transfer which is intended to be cancelled. 
6. **comment** \(query\). This is a string containing the reason for canceling the deposit or withdrawal.

Here's the final template for this API request:

```text
DELETE apiURL/v1.0/accounts/{accountId}/transfers/{transferId}?comment=Accidental%20transfer
```

### Response

In response to this API request, if the transfer was successfully canceled, you will receive the 204 status code and no response body.

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to cancel an outstanding funds transfer.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

