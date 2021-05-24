---
description: Perform regular authentication in ETNA Trader
---

# Single-Factor Authentication

### Overview

All API requests in ETNA Trader require a unique authentication token that must be provided in the request header. Without this token, it's impossible to place orders, retrieve charts, create users, etc. To get the token, use the following API endpoint:

```text
POST APIBaseURL + /token
```

{% hint style="info" %}
API base URL is unique for every environment; if you're testing the API on our demo environment, the final endpoint URL will be as follows:  
[`https://pub-api-et-demo-prod.etnasoft.us/api/token`](https://pub-api-et-demo-prod.etnasoft.us/api/token) 
{% endhint %}

The header of the request must contain the following three parameters:

1. **Et-App-Key**. This is the API key of your company that can be found it in the BO Companies widget. When editing the company's settings, navigate to the WebApi tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Username**. This is the username of the user on whose behalf all future requests will be made.
3. **Password**. This is the password of the user on whose behalf all future requests will be made.

### CURL

The following is a sample CURL for performing single-factor authentication:

```text
curl -X POST "https://pub-api-et-demo-prod.etnasoft.us/api/token" \
	-H "Username: yourUsername" \
	-H "Password: yourPassword" \
	-H "Et-App-Key: yourEttAppKey" \
	-H "Content-Length: 0" 
```

### Response

In response to this API request, you'll receive a JSON file that contains the token. Here's an example of such response:

```javascript
{
    "State": "Succeeded",
    "Token": "FAKETokenAAKTQZR0F5K0OY5sfsWcd9rwAAAAACAAAAAAAQZgA/M8HtnoEJR0UxEDagAAAAAOgAAAAAIAACAAAACApaOit8LbBxTVxJXceMgzvN+"
}
```

where:

| Parameter | Description |
| :--- | :--- |
| State | This is the state of the request. Usually the value is set to `Succeeded`, meaning that the request has been successfully made. |
| Token | This is the token that must be provided in all subsequent API requests as the authentication bearer token. Ensure that this token is provided in the following format: The value of this header must have the following format: `Bearer BQ898r9fefi` \(`Bearer` + 1 space + the token\). |

{% hint style="info" %}
The authorization token lifetime is 24 hours.
{% endhint %}

### Common Mistakes

Here are some of the common mistakes that developers make when requesting a token:

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

### Sample Code

To see how initial authentication can be performed in code, feel free to examine our [sample requests](../../code-samples/) in a dedicated article.

In the following article we provide in-depth coverage of the syntax for this API request.

