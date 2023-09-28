---
description: >-
  This endpoint enables you to retrieve a user's pending account transfer
  requests.
---

# Get User's Pending Account Transfer Requests

{% swagger summary="Get User's Pending Account Transfer Requests" path="/v{version}/users/{userId}/account-transfer-requests" method="get" baseUrl="baseURL" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter name="userId" in="path" required="true" type="Integer" %}
Internal ETNA Trader ID of the user.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request, JSON data containing the user's pending account requests is returned." %}
```javascript
[
  {
    "Id": "00000000-0000-0000-0000-000000000000",
    "CreatedAt": "2023-08-01T10:56:20.742Z",
    "AccountProvider": "None",
    "FromAccount": "string",
    "ToAccount": "string",
    "InitiatedBy": "string",
    "AcceptedBy": "string",
    "Type": "UNDEFINED",
    "TifId": "00000000-0000-0000-0000-000000000000",
    "AcatsControlNumber": 0,
    "FormDataReference": "string",
    "Status": "NEW",
    "History": [
      {
        "RequestId": "00000000-0000-0000-0000-000000000000",
        "CreatedAt": "2023-08-01T10:56:20.742Z",
        "Status": "NEW",
        "ChangedBy": "string",
        "Comment": "string"
      }
    ],
    "ParticipantImageURL": "string",
    "TransferInitiator": {
      "FirstName": "string",
      "Middle": "string",
      "LastName": "string",
      "Login": "string"
    },
    "PartialTransferProperties": {
      "cash": {
        "amount": 0,
        "isoCurrencyCode": "string",
        "type": "DEBIT"
      },
      "assets": [
        {
          "assetType": "CUSIP",
          "identifier": "string",
          "isoCurrencyCode": "string",
          "amount": 0,
          "isShort": true
        }
      ],
      "options": [
        {
          "symbol": "string",
          "contractDate": "2023-08-01T10:56:20.742Z",
          "optionType": "PUT",
          "strikePrice": 0,
          "isShort": true,
          "amount": 0
        }
      ]
    }
  }
]
```
{% endswagger-response %}
{% endswagger %}
