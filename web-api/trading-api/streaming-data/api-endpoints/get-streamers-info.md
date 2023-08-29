# Get Streamers' Info

### Overview

This GET endpoint enables you to retrieve information that might be required to initiate a streaming session.

There are three required parameters that must be provided in the request:

1. **Et-App-Key** (header). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key (it could be a key for the web terminal, the mobile app, or a custom key).
2. **Authorization** (header). This is the authorization token from the very first [token request](broken-reference). The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
3. **API version** (path). Unless necessary, leave it at "1.0".

Here's the final template for this API request:

```
GET publicApiURL/v1.0/streamers
```

### Response

In response to this API request, you will receive a JSON dictionary containing the URLs, session IDs, and other pertinent information that might be required to initiate a streaming session.

```javascript
{
  "QuoteAddresses": [
    {
      "Url": "wss://trader-demo-test.etnasoft.us:9995",
      "Type": "Delayed",
      "SessionId": "fda7be71-1d29-48e5-abe3-35c68bf9b3fd"
    }
  ],
  "DataAddresses": [
    {
      "Url": "wss://trader-demo-test.etnasoft.us:9999",
      "Type": "delayed"
    }
  ]
}
```

where:

| Parameter | Description                             |
| --------- | --------------------------------------- |
| URL       | This is the URL of the streamer.        |
| Type      | This is the type of the retrieve data.  |
| SessionId | This is the ID of the session.          |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve streamer data.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```
