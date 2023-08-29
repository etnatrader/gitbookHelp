# Recover a Streamer Session

### Overview

This PUT endpoint enables you to retrieve information that might be required to initiate a streaming session.

There are four required parameters that must be provided in the request:

1. **Et-App-Key** (header). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key (it could be a key for the web terminal, the mobile app, or a custom key).
2. **Authorization** (header). This is the authorization token from the very first [token request](broken-reference). The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
3. **API version** (path). Unless necessary, leave it at "1.0".
4. **sessionType** (query). The type of the session that must be recovered. Possible values:
   * `0`. Recovers the data session
   * `1`. Recovers the quote session

Here's the final template for this API request:

```
PUT publicApiURL/v1.0/streamers/session/recover?sessionType=0
```

### Response

In response to this API request, you will receive a JSON dictionary containing the ID of the recovered session:

```javascript
{
  "Id": "f495411a-a3a1-47aa-a8cd-42e18365f444"
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to recover a streaming session.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```
