# Delete Watchlist

### Overview

This DELETE endpoint enables you to delete a specific watchlist of the user whose id is provided in the request's header.

{% hint style="warning" %}
In order to delete a particular watchlist of a particular user, you must use an [authorization token](../../authentication/requesting-tokens/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

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

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for deleting a specific watchlist, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

### 

