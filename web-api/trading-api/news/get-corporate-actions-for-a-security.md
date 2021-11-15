---
description: Fetch all impending corporate actions for a specific security
---

# Get Corporate Actions for a Security

### Introduction

This GET endpoint enables you to fetch the list of all impending corporate actions of a specific security by providing its ticker symbol.&#x20;

There are four required parameters that must be provided in the request:

1. **Et-App-Key** (header). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** (header). This is the authorization token from the very first [token request](../authentication/requesting-tokens/). The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
3. **API version** (path). Unless necessary, leave it at "1.0".
4. **symbol **(query). This is the ticker symbol of the security for which corporate actions must be fetched.

Here's the final template for this API request:

```
GET apiURL/v1.0/news/corporate-actions?symbol=T
```

### Response

In response to this API request, you'll receive a JSON file containing the list of the recent and impending corporate actions of the specified security.

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve the corporate actions of a specific security.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Failing to Specify the Query Parameters

It's crucial to understand that the _**security**_ parameter must be provided in the request; otherwise you'll receive the 404 status code.
