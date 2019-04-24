# Create Batch Multi-Leg Allocation Requests

## Create Batch Multi-Leg Allocation Requests

#### Overview

This POST endpoint enables you to create and send multiple allocation requests for multi-leg orders. Multi-leg orders are orders that consist of multiple legs — separate orders that are part of a particular strategy. For example, you can employ the covered call strategy in which you sell call options against the stocks you intend to purchase. In this case, selling call options would be the first leg of the order and purchasing stocks would be the second leg of the order.

Allocation requests are used to purchase securities in bulk for multiple users to reduce the exchange commission applied to the order \(the higher the volume — the lower the commission\). Usually, there's a separate trading account on which securities are purchased. Afterward, the purchased securities are transferred to users' trading accounts proportionally to the amount of funds they have contributed.

For example, if one user has contributed 20% of the funds, another user — 30%, and the third — 50%, they will each receive a corresponding number of shares on their trading accounts: the first user will get 20% of the purchased securities, the seconds one will receive 30% of the purchased securities, and the third one will get 50% of the purchased securities. Such securities transfers can be performed with this API request where you specify the trading account on which the securities were purchased, the trading account of the target user, and also the number of securities to be transferred \(along with a few other parameters\).

From a technical standpoint, transference of securities from one account to another during allocation is executed like a regular sale — the source account is selling securities to the target account. You specify the price at which the securities must be transferred, indicate the applicable commission, and at the end of the trading session this transaction is registered with the clearing firm.

Please bear in mind that there are certain regulations that apply to allocations like prohibition of selling securities to users at a premium. Therefore, please ensure that your allocations comply with the regulator's requirements.

Batch multi-leg allocation requests combine the functionality of allocation requests and multi-leg orders and enable you to allocate multi-leg orders to your users proportionally to the amount of funds they have contributed.

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **requestInfos** \(body\). This is a JSON dictionary that contains information about the new batch multi-leg allocation.

**Multi-leg Allocation Request Sample**

Each multi-leg batch allocation request must be provided in the JSON format as an element of the request array:

```javascript
[ 
  {
    "FromAccount": "6688",
    "ToAccount": "6687",
    "AccountType": "Cash",
    "Comment": "Sample transfer",
    "Commission": 1.39,
    "Legs": [
      {
        "Symbol": "VAT",
        "Price": 60,
        "Quantity": 100,
        "Action": "Buy"
      },
      {
        "Symbol": "VAT Jan 2025 45.00 Call",
        "Price": 148,
        "Quantity": -1, //indicates that the option is being sold
        "Action": "Buy"
      }
    ],
    "Instructions": {}
  }
]
```

where:

| Parameter | Description |
| :--- | :--- |
| FromAccount | This is the source trading account from which the securities will be transferred. |
| ToAccount | This is the target trading account to which the securities will be transferred from the source trading account. |
| AccountType | This is the type of the account. Possible values: **Cash**, **Margin**, **DayTrader**. |
| Comment | This is the comment for this allocation. |
| Commission | This is the commission that will be charged on the user's trading account for this allocation. You may set this value to 0 if you charge your users monthly for allocations. |
| Legs | These are the legs of the orders. |
| Symbol | This is the ticker symbol of the securities that are to be transferred. |
| Quantity | This is the number of shares that are to be transferred. |
| Price | This is the price at which the securities are to be transferred. |
| Action | This is the side of the trade. Possible values: **Buy**, **Sell**. If the value is set to Sell, the leg will be transferred from the users' trading accounts to the joint trading account from which they will be sold on the market. |
| Instructions | These are ancillary instructions for this multi-leg allocation. You can leave it empty. |

Here's the final template for this API request:

```text
POST apiURL/v1.0/allocations/multileg
```

#### Response

In response to this API request, you'll receive a JSON file with the multi-leg allocation request details along with one extra parameter — **IsSucceed** — which indicates if the multi-leg allocation has been successfully carried out.

```javascript
[
  {
    "Request" : {
      "FromAccount": "6688",
      "ToAccount": "6687",
      "AccountType": "Cash",
      "Comment": "Sample transfer",
      "Commission": 1.39,
      "Legs": [
        {
          "Symbol": "VAT",
          "Price": 60,
          "Quantity": 100,
          "Action": "Buy"
        },
        {
          "Symbol": "VAT Jan 2025 45.00 Call",
          "Price": 148,
          "Quantity": -1, //indicates that the option is being sold
          "Action": "Buy"
        }
      ],
      "Instructions": {}
      },
      "IsSucceed" : true,
      "Description" : "description"
  }
]
```

#### Common Mistakes

Here are some of the common mistakes that developers make when attempting to create batch multi-leg allocation requests.

**Failing to Specify the Et-App-Key Parameter**

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

**Specifying User Accounts instead of Trading Accounts**

Another common mistake is either specifying user accounts instead of trading accounts when creating a batch multi-leg allocation request. Doing so will lead to the 409 status code. The IsSucceed parameter in this case would be set to false.

