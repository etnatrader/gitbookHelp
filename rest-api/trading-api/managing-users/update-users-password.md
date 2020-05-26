---
description: Update the password of a user
---

# Update User's Password

### Overview

This PUT endpoint enables you to update the password of an existing user by providing the old and the new password. This operation is different from the [password reset process](../password-reset/) where the old password is unknown but can be reset via email.

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the internal ID of the user  whose password you'd like to updated. If the request is sent on behalf of the user whose authorization token is used to perform the request, set this parameter to `@me`.
5. **userPassword** \(body\). This is a JSON object containing the the old and the new password of the user.

#### Body Syntax

The body of the request represents a JSON object containing the old, the new, and the confirmation of the new password.

```javascript
{
  "OldPassword": "jqwejr09er9wcwek",
  "Password": "ekrf09238f9a9j88aj49f8jpa983hp89f",
  "PasswordConfirm": "ekrf09238f9a9j88aj49f8jpa983hp89f"
}
```

{% hint style="warning" %}
A user's password can only be updated by the user themselves. Even an administrator of the platform is not authorized to update traders' password.
{% endhint %}

The following is the final template for this request:

```text
PUT apiURL/v1.0/users/{userID}/password/change
```

### Response

In response to this request, if the user's password was successfully updated, you will receive the 200 status code and no error message.

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to update a user's trading settings:

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Failure to Provide the Old Password

If you fail to provide the old password in the body of the request, you will receive the following error:

```javascript
{
  "Message": "Validation error occured while processing entity",
  "ModelState": {
    "userPassword.OldPassword": [
      "Password is required"
    ]
  }
}
```

