---
description: Delete an existing watchlist
---

# Delete Watchlist

### Overview

This DELETE endpoint enables you to delete a specific watchlist of the user whose id is provided in the request's path.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the ID of the user whose particular watchlist needs to be deleted.
5. **watchlistID** \(path\). This is the internal identifier of the watchlist that needs to be deleted.

Here's the final template for this API request:

```text
DELETE apiURL/v1.0/users/{userID}/watchlists/{watchlistID}
```

### Response

This API request does not return any messages from the server. In case of successful deletion, the status code of the request should be 204.

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to delete a specific watchlist. 

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

The following article covers the syntax for this API request in detail.

### 

