# Modify User's Address

### Overview

This GET endpoint enables you to modify the address of the user whose ID is provided in the request's path.

{% hint style="warning" %}
In order to modify the address of a particular user, you must use an [authorization token](../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the internal identifier of the user whose address is to be modified. User IDs can be listed with [this method](../managing-users/get-users-info/).
5. **user** \(body\). This is the new address of the user.

Here's the final template for this API request:

```text
PUT apiURL/v1.0/users/{userID}/addresses
```

#### Request Body Sample

```javascript
{
  "StreetAddress1": "Downing Street 10",
  "City": "London",
  "State": 0,
  "CountryId": 1
}
```

### Response

In response to this API request, you'll receive a JSON file with with the updated user's address.

```javascript
{
  "StreetAddress1": "Downing Street 10",
  "City": "London",
  "State": 0,
  "CountryId": 1
}
```

where:

| Parameter | Description |
| :--- | :--- |
| StreetAddress | This is the street address of the user. |
| City | This is the city is which the user is residing. |
| State | This is the state in which the user is residing \(if applicable\). |
| CountryId | This is the user's country's internal identifier in ETNA Trader. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to modify a user's address.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for modifying user addresses, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

