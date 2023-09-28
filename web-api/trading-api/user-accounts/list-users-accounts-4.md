# Get All Accounts

## Overview

This endpoint, depending on your permissions, enables you to retrieve the list of all trading accounts that have been created by the users of your company or your own accounts that are bound to the user.

{% swagger method="get" path="/v{version}/accounts/all" baseUrl="baseURL" summary="Get All Accounts" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="pageNumber" type="Integer" required="true" %}
Retrieved accounts are split into pages.&#x20;



pageNumber allows you to navigate between different pages to access the desired information.
{% endswagger-parameter %}

{% swagger-parameter in="query" type="Integer" name="pageSize" required="true" %}
This field specifies the number of trading accounts to be displayed on a single page. It allows you to control the pagination and limit the number of results displayed per page.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="propertyName" type="String" %}
This field determines the sorting order for the retrieved trading accounts. When you set this parameter, the trading accounts will be sorted based on the specified criterion. For instance, if you set the value to "Cash," the accounts will be sorted by their cash balance in ascending or descending order, depending on the isAscending parameter.&#x20;
{% endswagger-parameter %}

{% swagger-parameter in="query" name="isAscending" type="Boolean" %}
A field that determines whether the returned trading accounts should be sorted in ascending (true) or descending (false) order.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="filter" type="Query" %}
This is a filter query used to retrieve trading accounts that meet the specified conditions. More detailed filter description is provided below the method description.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="mask" type="String" %}
Mask field refers to a pattern that can be used to find a specific account.\
\
It allows to search accounts by phone, email, account number, first and last name.\
\
To use the "mask" field, simply provide the value you are searching for. For example, if you are looking for an account with the email "johnsmith@gmail.com," you can provide that exact string as the argument. The API will then return any matching accounts based on the provided value.
{% endswagger-parameter %}

{% swagger-parameter in="query" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request, JSON data is returned, containing the list of trading accounts." %}
```javascript
{
  "Result": [
    {
      "Id": 0,
      "ClearingAccount": "string",
      "FirstName": "string",
      "LastName": "string",
      "Login": "string",
      "Email": "string",
      "Phone": "string",
      "CreatedDate": "2023-07-31T11:27:50.379Z",
      "ModifiedDate": "2023-07-31T11:27:50.379Z",
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
      "OwnerType": "IndividualCustomer",
      "DayTradingBuyingPower": 0,
      "DayTrades": 0,
      "SmaBalance": 0,
      "HouseCall": 0,
      "MaintenanceCall": 0,
      "EquityCall": 0,
      "InitialCall": 0,
      "DayTradeCall": 0,
      "CashCall": 0,
      "NewHouseCall": 0,
      "TradeDayBalance": 0,
      "MoneyMarket": 0,
      "Cip": 0,
      "IsAverageAccount": true,
      "MarginEquity": 0,
      "ClearingFirm": "string",
      "ExcessEquity": 0,
      "Fdid": "string",
      "DayTraderRate": 0,
      "AccountHolder": "string",
      "EquityTotal": 0,
      "FixedAccountType": true,
      "SkipClearing": true,
      "SSN": "string"
    }
  ],
  "NextPageLink": "string",
  "PreviousPageLink": "string",
  "TotalCount": 0
}
```
{% endswagger-response %}
{% endswagger %}

### Filter Syntax

Each parameter of a trading account can serve as a filter. The conditions that a parameter needs to satisfy can be expressed in the following ways:

1. **Parameter** (=, <, >, <=, >=) **value**. For example: `Id = 7420`
2. **Parameter** (=, contains, startsWith, endsWith) **string**. For example: `Currency = 'USD'`
3. **Parameter** in (**value1**, **value2**, etc.). In this case the parameter has to be contained in the set of values in the parentheses to satisfy the filter condition. For example: `Id in (7420, 7630, 9870)`
4. **Parameter** between **Value1** and **Value2**. In this case the parameter has to be in the specified range between Value1 and Value2 to satisfy the filter condition. For example: `Cash between 0 and 2500`.

Boolean values are provided in the following format: `true` and `false`.

Numeric values are provided in the regular format: `2500`.

Strings must be highlighted with quotation marks: `'USD'`.

Dates must be highlighted with with the pound sign: `#2019-08-09T18:31:42#`.

### Sample Queries

| Sample Query                                                                                                                      | Description                                                                                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li>CreatedDate between #2019-03-13T18:31:42# and #2019-03-17T18:31:42#</li><li>CreatedDate > #2019-03-15T18:00:00#</li></ul> | <ul><li>Retrieves accounts whose creation date lies in the specified range.</li><li>Retrieves accounts whose creation date is earlier than in the provided argument</li></ul> |
| <ul><li>Cash = 0</li></ul>                                                                                                        | <ul><li>Retrieves accounts whose Cash parameter is equal to 0</li></ul>                                                                                                       |
| <ul><li>Enabled = false</li></ul>                                                                                                 | <ul><li>Retrieves disabled accounts</li></ul>                                                                                                                                 |
| <ul><li>ClearingAccount = 6303</li></ul>                                                                                          | <ul><li>Retrieves an account with a specific 6303</li></ul>                                                                                                                   |
| <ul><li>Cash > 0</li></ul>                                                                                                        | <ul><li>Retrieves all accounts with a positive cash balance</li></ul>                                                                                                         |
| <ul><li>Currency = 'USD'</li></ul>                                                                                                | <ul><li>Retrieves all accounts that are denominated is US dollars.</li></ul>                                                                                                  |
| <ul><li>Status = 'Approved'</li></ul>                                                                                             | <ul><li>Retrieves all accounts that have been approved by the clearing firm.</li></ul>                                                                                        |
| <ul><li>MarginInterestRate = 0</li></ul>                                                                                          | <ul><li>Retrieves all accounts that are eligible to borrow broker's funds at no cost.</li></ul>                                                                               |
| <ul><li>MarginType = 'Margin'</li></ul>                                                                                           | <ul><li>Retrieves all accounts of a particular type.</li></ul>                                                                                                                |
| <ul><li>Permissions = 1</li></ul>                                                                                                 | <ul><li>Retrieves all accounts who can open long positions in stock.</li></ul>                                                                                                |
| <ul><li>OwnerType startsWith 'Individual'</li></ul>                                                                               | <ul><li>Retrieves all accounts whose owner type starts with the word <em>Individual</em>.</li></ul>                                                                           |
| <ul><li>IsAverageAccount = true</li></ul>                                                                                         | <ul><li>Retrieves all accounts that serve as the main account during allocations.</li></ul>                                                                                   |
