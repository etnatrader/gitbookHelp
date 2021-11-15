---
description: Perform two-factor authentication in ETNA Trader
---

# Two-Factor Authentication

### Overview

All API requests in ETNA Trader require a unique authentication token that must be provided in the request header. Without this token, it's impossible to place orders, retrieve charts, create users, etc. To get the token, use the following API endpoint:

```
POST APIBaseURL + /token
```

{% hint style="info" %}
API base URL is unique for every environment; if you're testing the API on our demo environment, the final endpoint URL will be as follows:\
[`https://pub-api-et-demo-prod.etnasoft.us/api/token`](https://pub-api-et-demo-prod.etnasoft.us/api/token)&#x20;
{% endhint %}

If the user's account has two-factor authentication enabled, the authentication process involves two separate requests:

1. First request: retrieval of the interim token;
2. Second request: retrieval of the authentication token.

#### First Request

The header of the first request must contain the following three parameters:

1. **Et-App-Key**. This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Username**. This is the username of the user on whose behalf all future requests will be made.
3. **Password**. This is the password of the user on whose behalf all future requests will be made.

#### Second Request

The header of the second request must contain the following three parameters:

1. **Et-App-Key**. This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Username**. This is the username of the user on whose behalf all future requests will be made.
3. **Password**. This is the password of the user on whose behalf all future requests will be made.
4. **VerificationCode** (header). This is the verification code that's sent by email or as an SMS message (depending on the the user's settings).
5. **Authorization** (header). This is the authorization token that will be returned in response to the initial request.

### CURL

The following are sample CURLs for performing two-factor authentication:

#### First Request

```
curl -X POST "https://pub-api-et-demo-prod.etnasoft.us/api/token" \
	-H "Username: yourUsername" \
	-H "Password: yourPassword" \
	-H "Et-App-Key: yourEttAppKey" \
	-H "Content-Length: 0" 
```

#### Second Request

```
curl -X POST "https://pub-api-et-demo-prod.etnasoft.us/api/token" \
	-H "Username: yourUsername" \
	-H "Password: yourPassword" \
	-H "Authorization: Bearer {tokenFromTheFirstRequest}" \
	-H "VerificationCode: {codeFromEmailOrSMS}" \
	-H "Et-App-Key: yourEttAppKey" \
	-H "Content-Length: 0"
```

### Response

In response to the first API request, you'll receive a JSON file that contains the interim token. Here's an example of such response:

```javascript
{
    'Step': 'VerificationCode', 
    'Reason': 'Expecting confirmation code', 
    'State': 'Expecting', 
    'Token': 'someToken+zrIbQGZl8sBT1LWQEY38SQ=='
}
```

Also notice that the response contains the **Token** parameter that must be used in the subsequent request as a header parameter in the following format:

* `"Authorization" : "Bearer + tokenFromTheFirstRequest"`

In total, the header of the second request must contain five parameters:

1. **Username **(identical to the first request);
2. **Password **(identical to the first request);
3. **Et-App-Key **(identical to the first request);
4. **Authorization** (Bearer + token);
5. **VerificationCode** (the code received by email or SMS).

In response to the second request, you'll receive the following JSON dictionary:

```javascript
{
  "State": "Succeeded",
  "Token": "someToken"
}
```

The token parameter from the second request must be provided as the `Authorization` parameter in all future requests like placing orders, retrieving user's positions, etc.

{% hint style="info" %}
The authorization token lifetime is 24 hours.
{% endhint %}

### Common Mistakes

Here are some of the common mistakes that developers make when requesting an authorization token:

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Incorrect or Missing User Credentials

If you specify the wrong user credentials or fail to include them in the request header, you'll get the following error:

```javascript
{
    "State": "Failed",
    "Step": "BaseAuthentication",
    "Reason": "Invalid credentials"
}
```

In the following article we outline in detail all of the required and optional header parameters, the range of response status codes, as well as a comprehensive list of all possible responses.

#### Failure to Provide the Authorization Token with Two-Factor Authentication

Another common mistake that developers make during authentication is failure to provide the authorization token that is retrieved during the first request of a two-factor authentication. If the token is not provided in the request header, the entire authentication process will be rendered corrupt:

```javascript
{'State': 'Failed', 'Step': 'VerificationCode', 'Reason': 'Corrupted ticket'}
```

### Sample Code

To see how two-factor authentication can be performed in code, feel free to examine our [sample requests](../../code-samples/two-factor-autentication.md) in a dedicated article.

In the following article we provide in-depth coverage of the syntax for this API request.
