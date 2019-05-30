---
description: List all trading accounts registered within your company
---

# List All Accounts

## Overview

This GET endpoint enables you to retrieve the list of all trading accounts that have been created by the users of your company. All accounts are split into pages, each of which can be individually retrieved with the help of this endpoint.

{% hint style="warning" %}
In order to list all trading accounts of your company, you must use an [authorization token](../../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **pageSize** \(query\). This field indicates the number of trading accounts that need to be retrieved per page.
5. **pageNumber** \(query\). This field indicates the number of the page that needs to be retrieved \(all trading accounts are split into a set of pages that can be loaded one by one\).
6. **propertyName** \(query\). This is the field by which the retrieved trading accounts should be sorted. For example, if the value of this parameter is set to **Cash**, the retrieved trading accounts will be sorted by the accounts' cash balance.
7. **isAscending** \(query\). This field indicates if the list of retrieved trading accounts should be sorted in the descending \(false\) or ascending \(true\) order.

There's also one optional parameter worth examining:

* filter \(request query\). This is an SQL query used to retrieve only those accounts that satisfy the conditions of the query. 

### Filter Syntax

The syntax for filter queries is rather simple: each parameter of a trading account can serve as a filter. The conditions that a parameter needs to satisfy can be expressed in the following ways:

1. **Parameter** \(=, &lt;, &gt;, &lt;=, &gt;=\) **value**. For example: `Id = 7420`
2. **Parameter** \(=, contains, startsWith, endsWith\) **string**. For example: `Currency = 'USD'`
3. **Parameter** in \(**value1**, **value2**, etc.\). In this case the parameter has to be contained in the set of values in the parentheses to satisfy the filter condition. For example: `Id in (7420, 7630, 9870)`
4. **Parameter** between **Value1** and **Value2**. In this case the parameter has to be in the specified range between Value1 and Value2 to satisfy the filter condition. For example: `Cash between 0 and 2500`.

Boolean values are provided in the following format: `true` and `false`.

Numeric values are provided in the regular format: `2500`.

Strings must be highlighted with quotation marks: `'USD'`.

Dates must be highlighted with with the pound sign: `#2019-08-09T18:31:42#`.

The following table lists a set of sample queries:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Sample Query</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>CreatedDate between #2019-03-13T18:31:42# and #2019-03-17T18:31:42#</li>
          <li>CreatedDate &gt; #2019-03-15T18:00:00#</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves accounts whose creation date lies in the specified range.</li>
          <li>Retrieves accounts whose creation date is earlier than in the provided
            argument</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Cash = 0</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves accounts whose Cash parameter is equal to 0</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Enabled = false</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves disabled accounts</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>ClearingAccount = 6303</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves an account with a specific 6303</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Cash &gt; 0</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all accounts with a positive cash balance</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Currency = &apos;USD&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all accounts that are denominated is US dollars.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Status = &apos;Approved&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all accounts that have been approved by the clearing firm.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>MarginInterestRate = 0</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all accounts that are eligible to borrow broker&apos;s funds
            at no cost.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>MarginType = &apos;Margin&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all accounts of a particular type.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Permissions = 1</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all accounts who can open long positions in stock.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>OwnerType startsWith &apos;Individual&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all accounts whose owner type starts with the word <em>Individual</em>.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>IsAverageAccount = true</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all accounts that serve as the main account during allocations.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>{% hint style="info" %}

Here's the final template for this API request:

```text
GET apiURL/v1.0/accounts
```

## Response

In response to this API request, you'll receive a JSON file with the list of trading accounts sorted by the field that was specified in the **propertyName** parameter in the request query.

```javascript
{
  "Result": [
    {
      "Id": 1945,
      "SubscriptionPlanId": 0,
      "ClearingAccount": "1945",
      "CreatedDate": "2016-06-08T16:29:49.893Z",
      "ModifiedDate": "2019-03-10T11:01:22.5939919Z",
      "Enabled": true,
      "IsChanged": false,
      "Cash": -39784716,
      "Currency": "USD",
      "Status": "Approved",
      "MarginInterestRate": 0,
      "CashInterestRate": 0,
      "CloseEquity": -39784716,
      "OpenExcess": -39784716,
      "OptionLevel": 4,
      "MarginType": "Margin",
      "Permissions": "LongStock, ShortStock, LongOption, ShortOption, AllowTrade, AllowMargin, AllowOpen",
      "BaseCash": -39784716,
      "Sweep": 0,
      "OwnerType": "IndividualCustomer",
      "DayTradingBuyingPower": -159138864,
      "DayTrades": 0,
      "SmaBalance": 0,
      "HouseCall": 0,
      "MaintenanceCall": 0,
      "EquityCall": 0,
      "InitialCall": 0,
      "DayTradeCall": 0,
      "TradeDayBalance": -39397110,
      "MoneyMarket": 0,
      "Cip": 0,
      "IsAverageAccount": false,
      "MarginEquity": -39784716,
      "ExcessEquity": 0
    },
    {
      "Id": 4216,
      "SubscriptionPlanId": 0,
      "ClearingAccount": "4216",
      "CreatedDate": "2018-05-10T09:20:30.0711982Z",
      "ModifiedDate": "2019-02-04T12:03:56.1767255Z",
      "Enabled": true,
      "IsChanged": false,
      "Cash": -8999000.77433717,
      "Currency": "USD",
      "Status": "Approved",
      "MarginInterestRate": 0,
      "CashInterestRate": 0,
      "CloseEquity": -8285522.31067809,
      "OpenExcess": -8285522.31067809,
      "OptionLevel": 4,
      "MarginType": "Cash",
      "Permissions": "LongStock, ShortStock, LongOption, ShortOption, AllowTrade, AllowMargin, AllowOpen",
      "BaseCash": -8285522.31067809,
      "Sweep": 0,
      "OwnerType": "IndividualCustomer",
      "DayTradingBuyingPower": -33142089.24271235,
      "DayTrades": 0,
      "SmaBalance": 0,
      "HouseCall": 0,
      "MaintenanceCall": 0,
      "EquityCall": 0,
      "InitialCall": 0,
      "DayTradeCall": 0,
      "TradeDayBalance": -8999000.77433717,
      "MoneyMarket": 0,
      "Cip": 0,
      "IsAverageAccount": false,
      "MarginEquity": -8285522.31067809,
      "ExcessEquity": 0
    },
    {
      "Id": 3225,
      "SubscriptionPlanId": 0,
      "ClearingAccount": "3225",
      "CreatedDate": "2017-04-25T14:39:14.257Z",
      "ModifiedDate": "2019-03-10T11:03:04.9904706Z",
      "Enabled": true,
      "IsChanged": false,
      "Cash": -2923219,
      "Currency": "USD",
      "Status": "Approved",
      "MarginInterestRate": 0,
      "CashInterestRate": 0,
      "CloseEquity": -2923219,
      "OpenExcess": -11692876,
      "OptionLevel": 4,
      "MarginType": "DayTrader",
      "Permissions": "LongStock, ShortStock, LongOption, ShortOption, AllowTrade, AllowMargin, AllowOpen",
      "BaseCash": -2923219,
      "Sweep": 0,
      "OwnerType": "IndividualCustomer",
      "DayTradingBuyingPower": -11692876,
      "DayTrades": 0,
      "SmaBalance": 0,
      "HouseCall": 0,
      "MaintenanceCall": 0,
      "EquityCall": 0,
      "InitialCall": 0,
      "DayTradeCall": 0,
      "TradeDayBalance": -2923219,
      "MoneyMarket": 0,
      "Cip": 0,
      "IsAverageAccount": false,
      "MarginEquity": -2923219,
      "ExcessEquity": 0
    }
  ],
  "NextPageLink": "https://priv-api-etnatrader-dev.etnasoft.us/api/v1.0/accounts?pageNumber=1&pageSize=3&propertyName=Cash&isAscending=true",
  "PreviousPageLink": "",
  "TotalCount": 6671
}
```

where:

| Parameter | Description |
| :--- | :--- |


| Result | This is an array that contains the requested trading accounts. |
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


| NextPageLink | This is the next page of trading accounts. |
| :--- | :--- |


| PreviousPageLink | This is the previous page of trading accounts. |
| :--- | :--- |


| TotalCount | This is the total number of trading accounts within the company. |
| :--- | :--- |


Here are some of the common mistakes that developers make when attempting to list a company's trading accounts.

### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for listing a company's trading accounts, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

