---
description: Retrieve settings for ETNA Trader for iOS and Android
---

# Get Mobile App Settings

## Overview

This GET endpoint enables you to retrieve the mobile settings for ETNA Trader for iOS and Android. These settings can and should be used to determine how the mobile apps function and whether or not they should function in the first place \(perhaps the mobile app's version is obsolete and must be updated before working\).

{% hint style="info" %}
The selection of available settings can always be extended or contracted. If you would like to add extra settings that can be leveraged in your mobile app, contact our [support team](mailto:support@etnatrader.com) and they will add them for you.
{% endhint %}

There are two required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **API version** \(path\). Unless necessary, leave it at "1.0".

The user information request must be sent to the following URL:

```text
GET apiURL/v1.0/applications/mobile/settings
```

### Response

In response to this request, you will receive a JSON object containing the current mobile settings:

```javascript
{
  "Settings": {
    "accountOpeningHTML": "<!DOCTYPE html>\r\n<html lang=\"en\">\r\n<head>\r\n    <meta charset=\"UTF-8\">\r\n    <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\">\r\n    <title>Parent Page</title>\r\n    <style>\r\n        body {\r\n            height: 100vh;\r\n            width: 100vw;\r\n            box-sizing: border-box;\r\n            overflow: hidden;\r\n            margin: 0;\r\n        }\r\n        #accountOpenning {\r\n            height: 100vh;\r\n            width: 100vw;\r\n        }\r\n    </style>\r\n    <script type=\"text/javascript\" src=\"https://ao-et-demo-prod.etnasoft.us/assets/account.opening.client.js\"></script>\r\n</head>\r\n<body>\r\n    <iframe\r\n        id=\"accountOpenning\"\r\n        src=\"https://ao-et-demo-prod.etnasoft.us/\"\r\n        frameborder=\"0\"\r\n        name=\"accountOpenning\"\r\n        scrolling='auto',\r\n        allowfullscreen=true\r\n        allow=\"geolocation;\"\r\n        token='%token%'\r\n    ></iframe>\r\n    <script>\r\n        const\r\n            frame = document.getElementById('accountOpenning'),\r\n            accounOpeningClient = new ETNA.AccounOpeningClient(frame),\r\n            logger = accounOpeningClient.setLogger(data => {\r\n                if (data.action === 'submit') {\r\n                    window.location.replace(\"http://accountSubmitted\");\r\n                    logger.remove();\r\n                    return;\r\n                    //Make custom actions here\r\n                }\r\n                if (data.type === 'info'){\r\n                    console.log(data);\r\n                    window.location.replace(\"http://accountSubmitted\");\r\n                    return;\r\n                }\r\n                if (data.type === 'error') return console.error(data);\r\n            }, true);\r\n            var accountId = '%AccountID%';\r\n            var clearingFirm = '%ClearingFirm%';\r\n            console.log(accountId);\r\n            if(accountId === 'null'){\r\n                //For create account\r\n                accounOpeningClient.createAccount();\r\n            } else {\r\n                //For create update\r\n                accounOpeningClient.updateAccount(accountId, clearingFirm);\r\n            }\r\n    </script>\r\n</body>\r\n</html>",
    "compatibleAndroidVersionCode": "59",
    "compatibleIOSVersion": "2.33.3",
    "defaultLoginMode": "1",
    "defaultOrdersPageSize": "15",
    "enableAddAccountButton": "1",
    "enableFundAccountButton": "0",
    "enablePaperTradingBanner": "1",
    "enableSeparateOptionTradeButton": "0",
    "enableSignUpButton": "1",
    "enableTouchID": "1",
    "enableTrailingOrders": "1",
    "recoverButtonSettings": "{\"environments\":[1,1]}",
    "securitySubscriptionType": "0",
    "signUpButtonSettings": "{\"environments\":[1,1]}",
    "tradeButtonAppearanceType": "1",
    "tryDemoButtonSettings": "{\"environments\":[0,1]}",
    "PinEnabled": false,
    "maxNumberOrderLegs": "4"
  }
}
```

where:

| Parameter | Description |
| :--- | :--- |
| accountOpeningHTML | The HTML that is prompted whenever a trader attempts to open a new trading account. |
| compatibleAndroidVersionCode | The minimum supported version of the Android app. |
| compatibleIOSVersion | The minimum supported version of the iOS app. |

### Common Mistakes

Here are some of the common mistakes that developers make when requesting mobile settings:

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

