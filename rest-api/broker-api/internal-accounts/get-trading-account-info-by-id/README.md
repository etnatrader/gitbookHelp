---
description: Get information about a particular trading account
---

# Get Trading Account Info by ID

## Overview

This GET endpoint enables you to retrieve information about a particular trading account by providing its internal identifier in ETNA Trader in the request path. This internal identifier can be retrieved with [this method](../list-all-accounts/) that lists all trading accounts in your company. You can also view the trading accounts of a users in ETNA Trader's header:

![](../../../../.gitbook/assets/screenshot-2019-03-07-at-14.59.29.png)

{% hint style="warning" %}
In order to retrieve information about a particular trading account, you must use an [authorization token]() of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request]().
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountID** \(path\). This is the internal identifier of the trading account whose information needs to be retrieved.

Here's the final template for this API request:

```text
GET apiURL/v1.0/accounts/{accountID}
```

## Response

In response to this API request, you'll receive a JSON file with detailed information about the trading account:

```javascript
{
  "Id": 6688,
  "SubscriptionPlanId": 0,
  "ClearingAccount": "6688",
  "CreatedDate": "2019-02-27T16:02:08.3584933Z",
  "ModifiedDate": "2019-03-06T14:15:08.4511659Z",
  "Enabled": true,
  "IsChanged": false,
  "Cash": 953573.99,
  "Currency": "USD",
  "Status": "Approved",
  "MarginInterestRate": 0,
  "CashInterestRate": 0,
  "CloseEquity": 1157969.29,
  "OpenExcess": 1122667.16,
  "OptionLevel": 4,
  "MarginType": "Cash",
  "Permissions": "LongStock, ShortStock, LongOption, ShortOption, AllowTrade, AllowMargin, AllowOpen",
  "BaseCash": 1122667.16,
  "Sweep": 0,
  "OwnerType": "IndividualCustomer",
  "DayTradingBuyingPower": 4490668.64,
  "DayTrades": 0,
  "SmaBalance": 0,
  "HouseCall": 0,
  "MaintenanceCall": 0,
  "EquityCall": 0,
  "InitialCall": 0,
  "DayTradeCall": 0,
  "TradeDayBalance": 953573.99,
  "MoneyMarket": 0,
  "Cip": 0,
  "IsAverageAccount": false,
  "MarginEquity": 1157969.29,
  "ExcessEquity": 0
}
```

where:

| Parameter | Description |
| :--- | :--- |


| Id | This is the internal identifier of the trading account that was provided in the request path. |
| :--- | :--- |


| SubscriptionPlanId | This is an internal field in ETNA Trader and it shouldn't be used by third-party developers. |
| :--- | :--- |


| ClearingAccount | This is the id of this account at the clearing firm. |
| :--- | :--- |


| CreatedDate | This is the date on which the trading account was created. |
| :--- | :--- |


| ModifiedDate | This is the date on which the trading account was last modified. |
| :--- | :--- |


| Enabled | This field indicates if the trading account is enabled. |
| :--- | :--- |


| IsChanged | This is an internal field in ETNA Trader and it shouldn't be used by third-party developers. |
| :--- | :--- |


| Cash | This is the amount of funds on the trading account that the user can expend on new positions. |
| :--- | :--- |


| Currency | This is the currency of the trading account. At the moment only US dollars are supported. |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">Status</th>
      <th style="text-align:left">
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
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| MarginInterestRate | This is the interest rate applied to the funds borrowed to finance margin positions. |
| :--- | :--- |


| CashInterestRate | This is an obsolete field and it shouldn't be used by third-party developers. |
| :--- | :--- |


| CloseEquity | This is the trading account's equity before the start of a new trading session \(calculated based on the closing price of the previous trading session\). |
| :--- | :--- |


| OpenExcess | This field indicates the account's excess funds calculated at the opening of the trading session. |
| :--- | :--- |


| OptionLevel | This field indicates which operations with options are permitted on this account. |
| :--- | :--- |


| MarginType | This is the account type. Read more about it [here](). |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">Permissions</th>
      <th style="text-align:left">
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
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| BaseCash | This is the trading account's excessive funds that are used for calculating DayTradingBuyingPower. |
| :--- | :--- |


| Sweep | This is an internal field and it shouldn't be used by third-party developers. |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">OwnerType</th>
      <th style="text-align:left">
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
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| DayTradingBuyingPower | This is the amount of funds that can be employed to make trades on day trading accounts. Usually the value of this field is equal to _BaseCash_ multiplied by four. |
| :--- | :--- |


| DayTrades | This is the number of active day trades on the account. |
| :--- | :--- |


| SmaBalance | This is the amount of funds in a special memorandum account. |
| :--- | :--- |


| HouseCall | This field indicates the amount of funds that need to be deposited into the account in order to prevent a house call. |
| :--- | :--- |


| MaintenanceCall | This field indicates the amount of funds that need to be deposited into the account in order to prevent a maintenance call. |
| :--- | :--- |


| EquityCall | This field indicates the amount of funds that need to be deposited into the account in order to prevent a minimum equity call. |
| :--- | :--- |


| InitialCall | This field indicates the amount of funds that need to be deposited into the account in order to prevent an initial call. |
| :--- | :--- |


| DayTradeCall | This field indicates the amount of funds that need to be deposited into the account in order to prevent a day trade call. |
| :--- | :--- |


| TradeDayBalance | This is the amount of funds that the trading account owes to the broker. |
| :--- | :--- |


| MoneyMarket | These are the money market funds on the trading account. |
| :--- | :--- |


| Cip | This is the Carriage and Insurance Paid To \(CIP\). |
| :--- | :--- |


| IsAverageAccount | This field indicates if this trading account is used to allocate shares to other trading accounts. |
| :--- | :--- |


| MarginEquity | This is the portion of the account's equity that was purchased on margin. |
| :--- | :--- |


| ExcessEquity | This is the withdrawable portion of the equity. |
| :--- | :--- |


Here are some of the common mistakes that developers make when attempting to retrieve information about a trading account.

### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for retrieving information about a trading account, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

So be sure to use the authorization token generated with an administrator's credentials.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

