---
description: Explore the parameters of transactions
---

# Transactions

### Introduction

In ETNA Trader, a transaction is any operation that involves movement of cash is considered a transaction. Purchasing and selling securities, charging commissions are all considered to be transactions. To list all transactions carried out on a specific trading account, use the following endpoint of ETNA Trader:

{% page-ref page="../../rest-api/trading-api/managing-transactions/get-transactions/" %}

### Transaction Parameters

The following table outlines all of the parameters of a transaction in ETNA Trader:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal identifier of the transaction. |
| SecurityId | This is the internal identifier of the underlying security that was traded in this transaction. |
| OrderStateId | This is the internal identifier of the order in ETNA Trader. In most cases this information should not be used. |
| AccountId | This is the internal identifier of the trading account on which the transaction was made. |
| Date | This is the date on which the transaction was made. |
| Value | This is the amount of funds that were subtracted from or added to the trading account. |
| Quantity | This is the number of securities that were traded in this transaction. |
| LeavesQuantity | This is the number of securities that are yet to be purchased in this transaction. This field is applicable for partial orders. |
| FeeId | This is a dictionary that contains information about the fees applied to this transaction. |
| Id | This is the internal identifier of the fee in ETNA Trader. |
| CommissionId | This is the identifier of the fee in the string format. |
| Value | This is the numeric value of the fee \(the amount that was subtracted from the trading account\). |
| Seizure | This field indicates when the fee will be applied to the trading account. |
| Leverage | This field indicates the amount of leverage used in this transaction. For example, if the value is set to 3, it means that the transaction's leverage equates to 3:1. |
| ValueType | This field indicates if the fee is applied on an absolute basis \(fixed amount for the transaction\) or on a relative basis \(as a percentage of the transaction\). |
| IsDayTrade | This field indicates if the transaction is a day trade. As per FINRA, a day trade is the purchasing and selling of the same security during on the same trading day. |

