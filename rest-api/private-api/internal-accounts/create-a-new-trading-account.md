---
description: Create a new trading account
---

# Create a New Trading Account

### Overview

This POST endpoint enables you to create a new trading account. After the trading account is created, it should be bound to a user, and afterward it can be used for trading \(if the clearing firm approves the new trading account\).

{% hint style="warning" %}
In order to create a new trading account, you must use an [authorization token](../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountModel** \(body\). This is a JSON file with the information about the new created trading account.

#### Request Body Sample

Following is a sample JSON file that contains information about the new trading account:

```javascript
{
  "SubscriptionPlanId": 0,
  "ClearingAccount": "string",
  "CreatedDate": "2019-03-11T10:37:02.671Z",
  "ModifiedDate": "2019-03-11T10:37:02.671Z",
  "Enabled": true,
  "IsChanged": true,
  "Cash": 0,
  "Currency": "string",
  "Status": "UnSpecified",
  "CommissionPlan": "string",
  "RepCode": "string",
  "MarginInterestRate": 0,
  "CashInterestRate": 0,
  "CloseEquity": 0,
  "OpenExcess": 0,
  "OptionLevel": 0,
  "MarginType": "Empty",
  "Permissions": "Empty",
  "BaseCash": 0,
  "Sweep": 0,
  "OwnerType": "IndividualCustomer",
  "DayTradingBuyingPower": 0,
  "DayTrades": 0,
  "SmaBalance": 0,
  "HouseCall": 0,
  "MaintenanceCall": 0,
  "EquityCall": 0,
  "InitialCall": 0,
  "DayTradeCall": 0,
  "TradeDayBalance": 0,
  "MoneyMarket": 0,
  "Cip": 0,
  "IsAverageAccount": true,
  "MarginEquity": 0,
  "ClearingFirm": "string",
  "ExcessEquity": 0
}
```

where:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Parameter</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Result</td>
      <td style="text-align:left">This is an array that contains the requested trading accounts.</td>
    </tr>
    <tr>
      <td style="text-align:left">Id</td>
      <td style="text-align:left">This is the internal identifier of the trading account that was provided
        in the request path.</td>
    </tr>
    <tr>
      <td style="text-align:left">SubscriptionPlanId</td>
      <td style="text-align:left">This is an internal field in ETNA Trader and it shouldn&apos;t be used
        by third-party developers.</td>
    </tr>
    <tr>
      <td style="text-align:left">ClearingAccount</td>
      <td style="text-align:left">This is the id of this account at the clearing firm.</td>
    </tr>
    <tr>
      <td style="text-align:left">CreatedDate</td>
      <td style="text-align:left">This is the date on which the trading account was created.</td>
    </tr>
    <tr>
      <td style="text-align:left">ModifiedDate</td>
      <td style="text-align:left">This is the date on which the trading account was last modified.</td>
    </tr>
    <tr>
      <td style="text-align:left">Enabled</td>
      <td style="text-align:left">This field indicates if the trading account is enabled.</td>
    </tr>
    <tr>
      <td style="text-align:left">IsChanged</td>
      <td style="text-align:left">This is an internal field in ETNA Trader and it shouldn&apos;t be used
        by third-party developers.</td>
    </tr>
    <tr>
      <td style="text-align:left">Cash</td>
      <td style="text-align:left">This is the amount of funds on the trading account that the user can expend
        on new positions.</td>
    </tr>
    <tr>
      <td style="text-align:left">Currency</td>
      <td style="text-align:left">This is the currency of the trading account. At the moment only US dollars
        are supported.</td>
    </tr>
    <tr>
      <td style="text-align:left">Status</td>
      <td style="text-align:left">
        <p>This is the status of the trading account. Possible values:</p>
        <ul>
          <li>New &#x2014; the trading account has been created;</li>
          <li>SentToClearing &#x2014; the trading account has been sent to the clearing
            firm;</li>
          <li>Approved &#x2014; the trading account has been approved by the clearing
            firm;</li>
          <li>Rejected &#x2014; the trading account has been rejected by the clearing
            firm.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">CommissionPlan</td>
      <td style="text-align:left">This is the commission plan (as provided by the clearing firm).</td>
    </tr>
    <tr>
      <td style="text-align:left">RepCode</td>
      <td style="text-align:left">This is a commission-related field (as provided by the clearing firm).</td>
    </tr>
    <tr>
      <td style="text-align:left">MarginInterestRate</td>
      <td style="text-align:left">This is the interest rate applied to the funds borrowed to finance margin
        positions.</td>
    </tr>
    <tr>
      <td style="text-align:left">CashInterestRate</td>
      <td style="text-align:left">This is an obsolete field and it shouldn&apos;t be used by third-party
        developers.</td>
    </tr>
    <tr>
      <td style="text-align:left">CloseEquity</td>
      <td style="text-align:left">This is the trading account&apos;s equity before the start of a new trading
        session (calculated based on the closing price of the previous trading
        session).</td>
    </tr>
    <tr>
      <td style="text-align:left">OpenExcess</td>
      <td style="text-align:left">This field indicates the account&apos;s excess funds calculated at the
        opening of the trading session.</td>
    </tr>
    <tr>
      <td style="text-align:left">OptionLevel</td>
      <td style="text-align:left">This field indicates which operations with options are permitted on this
        account.</td>
    </tr>
    <tr>
      <td style="text-align:left">MarginType</td>
      <td style="text-align:left">This is the account type. Read more about it <a href="../../../administrator-guide/administrators-widgets/managing-users/#trading-accounts">here</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left">Permissions</td>
      <td style="text-align:left">
        <p>This field lists the operations permitted on this trading account. Possible
          values:</p>
        <ul>
          <li>LongStock &#x2014; opening long positions in stocks is permitted;</li>
          <li>ShortStock &#x2014; opening short positions in stocks is permitted;</li>
          <li>LongOption &#x2014; opening long positions in options is permitted;</li>
          <li>ShortOption &#x2014; opening short positions in options is permitted;</li>
          <li>AllowTrade &#x2014; trading is permitted;</li>
          <li>AllowMargin &#x2014; trading on margin is permitted;</li>
          <li>AllowOpen &#x2014; opening positions on this account is permitted.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">BaseCash</td>
      <td style="text-align:left">This is the trading account&apos;s excessive funds that are used for calculating
        DayTradingBuyingPower.</td>
    </tr>
    <tr>
      <td style="text-align:left">Sweep</td>
      <td style="text-align:left">This is an internal field and it shouldn&apos;t be used by third-party
        developers.</td>
    </tr>
    <tr>
      <td style="text-align:left">OwnerType</td>
      <td style="text-align:left">
        <p>This is the type of the trading account&apos;s owner. Possible values:</p>
        <ul>
          <li>IndividualCustomer = 0</li>
          <li>InstitutionalCustomer = 1,</li>
          <li>Combined = 2,</li>
          <li>EmployeeAccount = 3,</li>
          <li>MarketMaking = 4,</li>
          <li>OtherProprietary = 5,</li>
          <li>Unknown = 6,</li>
          <li>ErrorAccount = 7</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DayTradingBuyingPower</td>
      <td style="text-align:left">This is the amount of funds that can be employed to make trades on day
        trading accounts. Usually the value of this field is equal to <em>BaseCash</em> multiplied
        by four.</td>
    </tr>
    <tr>
      <td style="text-align:left">DayTrades</td>
      <td style="text-align:left">This is the number of active day trades on the account.</td>
    </tr>
    <tr>
      <td style="text-align:left">SmaBalance</td>
      <td style="text-align:left">This is the amount of funds in a special memorandum account.</td>
    </tr>
    <tr>
      <td style="text-align:left">HouseCall</td>
      <td style="text-align:left">This field indicates the amount of funds that need to be deposited into
        the account in order to prevent a house call.</td>
    </tr>
    <tr>
      <td style="text-align:left">MaintenanceCall</td>
      <td style="text-align:left">This field indicates the amount of funds that need to be deposited into
        the account in order to prevent a maintenance call.</td>
    </tr>
    <tr>
      <td style="text-align:left">EquityCall</td>
      <td style="text-align:left">This field indicates the amount of funds that need to be deposited into
        the account in order to prevent a minimum equity call.</td>
    </tr>
    <tr>
      <td style="text-align:left">InitialCall</td>
      <td style="text-align:left">This field indicates the amount of funds that need to be deposited into
        the account in order to prevent an initial call.</td>
    </tr>
    <tr>
      <td style="text-align:left">DayTradeCall</td>
      <td style="text-align:left">This field indicates the amount of funds that need to be deposited into
        the account in order to prevent a day trade call.</td>
    </tr>
    <tr>
      <td style="text-align:left">TradeDayBalance</td>
      <td style="text-align:left">This is the amount of funds that the trading account owes to the broker.</td>
    </tr>
    <tr>
      <td style="text-align:left">MoneyMarket</td>
      <td style="text-align:left">These are the money market funds on the trading account.</td>
    </tr>
    <tr>
      <td style="text-align:left">Cip</td>
      <td style="text-align:left">This is the Carriage and Insurance Paid To (CIP).</td>
    </tr>
    <tr>
      <td style="text-align:left">IsAverageAccount</td>
      <td style="text-align:left">This field indicates if this trading account is used to allocate shares
        to other trading accounts.</td>
    </tr>
    <tr>
      <td style="text-align:left">MarginEquity</td>
      <td style="text-align:left">This is the portion of the account&apos;s equity that was purchased on
        margin.</td>
    </tr>
    <tr>
      <td style="text-align:left">ClearingFirm</td>
      <td style="text-align:left">This is the clearing firm that handles this trading account.</td>
    </tr>
    <tr>
      <td style="text-align:left">ExcessEquity</td>
      <td style="text-align:left">This is the withdrawable portion of the equity.</td>
    </tr>
  </tbody>
</table>Here's the final template for this API request:

```text
POST apiURL/v1.0/accounts
```

### Response

In response to this API request, you'll receive a JSON file with detailed information about the newly created trading account. In addition to all parameters specified in the request body, the response will also contain the ID of the trading account in ETNA Trader.

```javascript
{
  "Id": 6689,
  "SubscriptionPlanId": 0,
  "ClearingAccount": "string",
  "CreatedDate": "2019-03-11T10:37:02.671Z",
  "ModifiedDate": "2019-03-11T13:16:12.2006606Z",
  "Enabled": true,
  "IsChanged": true,
  "Cash": 0,
  "Currency": "str",
  "Status": "UnSpecified",
  "CommissionPlan": "string",
  "RepCode": "string",
  "MarginInterestRate": 0,
  "CashInterestRate": 0,
  "CloseEquity": 0,
  "OpenExcess": 0,
  "OptionLevel": 0,
  "MarginType": "Empty",
  "Permissions": "Empty",
  "BaseCash": 0,
  "Sweep": 0,
  "OwnerType": "IndividualCustomer",
  "DayTradingBuyingPower": 0,
  "DayTrades": 0,
  "SmaBalance": 0,
  "HouseCall": 0,
  "MaintenanceCall": 0,
  "EquityCall": 0,
  "InitialCall": 0,
  "DayTradeCall": 0,
  "TradeDayBalance": 0,
  "MoneyMarket": 0,
  "Cip": 0,
  "IsAverageAccount": true,
  "MarginEquity": 0,
  "ClearingFirm": "string",
  "ExcessEquity": 0
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to create a new trading account.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for creating trading accounts, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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



