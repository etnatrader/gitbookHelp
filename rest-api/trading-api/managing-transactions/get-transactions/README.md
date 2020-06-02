---
description: List transactions of a particular user
---

# Get Transactions

## Overview

This GET endpoint enables you to retrieve a list of transactions that the have been made on a particular trading account. The number of retrieved transactions can be specified in the request header.

There are eight required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountId** \(query\). This is the ID of the trading account whose transactions need to be retrieved.
5. **pageSize** \(query\). This field indicates the number of transactions that needs to be retrieved per page.
6. **pageNumber** \(query\). This field indicates the number of the page that needs to be retrieved \(all transactions are split into a set of pages that can be loaded one by one\).
7. **sortBy** \(query\). This is the field by which the retrieved transactions ought to be sorted. For example, if you the value of this parameter is set to **Quantity**, the retrieved alerts will be sorted by the number of shares involved in the transaction.
8. **isDesc** \(query\). This field indicates if the list of retrieved transactions should be sorted in the descending order \(true\) or ascending order \(false\).

There's also one optional parameter worth examining:

* filter \(request query\). This is an SQL query used to retrieve only those transactions that satisfy the conditions of the query. 

### Filter Syntax

The syntax for filter queries is rather simple: each parameter of a transaction can serve as a filter. The conditions that a parameter needs to satisfy can be expressed in the following ways:

1. **Parameter** \(=, &lt;, &gt;, &lt;=, &gt;=\) **value**. For example: `SecurityId = 4`
2. **Parameter** \(=, contains, startsWith, endsWith\) **string**. For example: `Date >= #2019-03-18T11:10:14.036Z#`
3. **Parameter** in \(**value1**, **value2**, etc.\). In this case the parameter has to be contained in the set of values in the parentheses to satisfy the filter condition. For example: `Id in (7420, 7630, 9870)`
4. **Parameter** between **Value1** and **Value2**. In this case the parameter has to be in the specified range between Value1 and Value2 to satisfy the filter condition. For example: `Quantity between 0 and 1000`.

Boolean values are provided in the following format: `true` and `false`.

Numeric values are provided in the regular format: `2500`.

Strings must be highlighted with quotation marks: `'USD'`.

Dates must be highlighted with the pound sign: `#2019-08-09T18:31:42#`.

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
          <li>SecurityId = 4</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all transactions with the Apple stock.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Date &gt;= #2019-03-18T11:10:14.036Z#</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all transactions that were carried out prior to the specified
            date.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Quantity between 0 and 1000</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all transactions in which the number of transacted securities
            lies in the range between 0 and 1000.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

{% hint style="info" %}
Note that you can combine different queries to create more complex requests:

* SecurityId = 4 and Quantity between 0 and 1000
{% endhint %}

Here's the final template for this API request:

```text
GET apiURL/v1.0/accounts/6303/transactions/?pageNumber=0&pageSize=10&sortBy=Quantity&isDesc=true
```

## Response

In response to this API request, you'll receive a JSON file with the list of transactions that have been made on the specified trading account.

```javascript
{
    "Result": [
        {
            "Id": 2390187,
            "SecurityId": 4,
            "OrderStateId": 168831,
            "AccountId": 6303,
            "Date": "2019-01-22T14:30:03.7328576Z",
            "Value": -23485.5,
            "Quantity": 150,
            "LeavesQuantity": 150,
            "Fee": {
                "Id": 156823,
                "Value": 23355,
                "Seizure": "Order",
                "Leverage": 1,
                "ValueType": "Absolute"
            },
            "Type": "OrderExecution",
            "IsDayTrade": false
        },
        {
            "Id": 2387057,
            "SecurityId": -1,
            "OrderStateId": 0,
            "AccountId": 6303,
            "Date": "2019-01-14T12:29:14.3203481Z",
            "Value": 1000000,
            "Quantity": 0,
            "LeavesQuantity": 0,
            "Type": "Payment",
            "IsDayTrade": false,
            "Description": "Initial deposit"
        },
        {
            "Id": 2390186,
            "SecurityId": 4,
            "OrderStateId": 168831,
            "AccountId": 6303,
            "Date": "2019-01-22T14:30:03.7328576Z",
            "Value": -3.75,
            "Quantity": 0,
            "LeavesQuantity": 0,
            "Fee": {
                "Id": 156822,
                "CommissionId": "Per Trade Commission",
                "Value": 3.75,
                "Seizure": "Execution",
                "Leverage": 1,
                "ValueType": "Absolute"
            },
            "Type": "Commission",
            "IsDayTrade": false
        }
    ],
    "NextPageLink": "",
    "PreviousPageLink": "",
    "TotalCount": 3
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Result | This is a dictionary that contains the requested transactions. |
| Id | This is the internal identifier of a given transaction. |
| SecurityId | This is the internal identifier of the underlying security that was traded in this transaction. |
| OrderStateId | This is the internal identifier of the order in ETNA Trader. In most cases this information should not be used. |
| AccountId | This is the internal identifier of the trading account on which the transaction was made. |
| Date | This is the date on which the transaction was made. |
| Value | This is the amount of funds that were subtracted from or added to the trading account. |
| Quantity | This is the number of securities that were traded in this transaction. |
| LeavesQuantity | This is the number of securities that are yet to be purchased in this transaction. This field is applicable for partial orders. |
| Fee | This is a dictionary that contains information about the fees applied to this transaction. |
| Id | This is the internal identifier of the fee in ETNA Trader. |
| CommissionId | This is the identifier of the fee in the string format. |
| Value | This is the numeric value of the fee \(the amount that was subtracted from the trading account\). |
| Seizure | This field indicates when the fee will be applied to the trading account. |
| Leverage | This field indicates the amount of leverage used in this transaction. For example, if the value is set to 3, it means that the transaction's leverage equates to 3:1. |
| ValueType | This field indicates if the fee is applied on an absolute basis \(fixed amount for the transaction\) or on a relative basis \(as a percentage of the transaction\). |
| IsDayTrade | This field indicates if the transaction is a day trade. As per FINRA, a day trade is the purchasing and selling of the same security during on the same trading day. |
| NextPageLink | This is the next page with the subsequent transactions. |
| PreviousPageLink | This is the previous page with older transactions. |
| TotalCount | This is the total number of transactions that have been made on this trading account. |

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve the list of transactions made on a particular trading account.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Failing to Specify the Query Parameters

It's crucial to understand that the _**pageSize, pageNumber, isDesc, and sortBy**_ parameters must be provided in the request; otherwise you'll receive the 404 status code and the following message:

```javascript
{
    "Error": {
        "Code": "UnsupportedApiVersion",
        "Message": "The requested resource with API version '1.0' does not support HTTP method 'GET'."
    }
}
```

The following article covers the syntax for this API request in detail.

