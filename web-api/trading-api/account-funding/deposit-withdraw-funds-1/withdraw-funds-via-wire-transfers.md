---
description: Withdraw funds from a trading account via a domestic or foreign wire transfer
---

# Withdraw Funds via Wire Transfers

### Introduction <a href="#withdrawing-funds-with-checks" id="withdrawing-funds-with-checks"></a>

This POST endpoint enables you to withdraw funds from your trading account by means of a domestic or foreign wire transfer.

{% hint style="warning" %}
Wire transfers are available only for withdrawing funds.
{% endhint %}

There are five required parameters that must be provided in the request:

1. **Et-App-Key** (header). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** (header). This is the authorization token from the very first [token request](../../authentication/). The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
3. **API version** (path). Unless necessary, leave it at "1.0".
4. **accountId** (path). This is the [internal identifier](../../user-accounts/list-users-accounts.md) of the trading account in ETNA Trader.
5. **model** (body). This is a JSON file containing detailed information about the wire transfer.

#### Body Syntax

The body of the request represents a JSON file containing all required parameters for performing the withdrawal.

{% tabs %}
{% tab title="Domestic Wire" %}
| Parameter                 | Required                                    | Description                                                                                                                                             |
| ------------------------- | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Amount                    | True                                        | This is the amount of funds to be withdrawn. The value must be provided in US dollars. Set this parameter to `null` if `CloseAccount` is set to `true`. |
| CloseAccount              | True                                        | This boolean value indicates if the trading account must be closed after the withdrawal is performed.                                                   |
| IsDomesticWire            | True                                        | Indicates if this is a domestic wire transfer. If you're performing a domestic wire transfer, set this parameter to `true`.                             |
| RoutingNumber             | True                                        | This is the ABA Routing Number.                                                                                                                         |
| AccountNumber             | True                                        | This is the target banking account number.                                                                                                              |
| ForFurtherCredit          | False                                       | Set it to `true` if the wire is meant to be sent further to a different bank.                                                                           |
| IntermediaryName          | True if `ForFurtherCredit` is set to `true` | The name of the intermediary bank.                                                                                                                      |
| IntermediaryAccountNumber | True if `ForFurtherCredit` is set to `true` | The number of the account at the intermediary bank.                                                                                                     |
| IntermediaryAddress1      | True if `ForFurtherCredit` is set to `true` | The address of the intermediary bank (line 1).                                                                                                          |
| IntermediaryAddress2      | False                                       | The address of the intermediary bank (line 2).                                                                                                          |
| IntermediaryCity          | True if `ForFurtherCredit` is set to `true` | The city in which the intermediary bank is located.                                                                                                     |
| IntermediaryCountry       | True if `ForFurtherCredit` is set to `true` | The country in which the intermediary bank is located.                                                                                                  |
| IntermediaryPostalCode    | True if `ForFurtherCredit` is set to `true` | The postal code of the intermediary bank.                                                                                                               |
| IntermediaryState         | True if `ForFurtherCredit` is set to `true` | The state of the intermediary bank.                                                                                                                     |
| IraDistribution           | True if the account type is IRA.            | Contains parameters related to the IRA withdrawal.                                                                                                      |

For example:

```javascript
{
    "Amount":100,
    "CloseAccount":false,
    "IsDomesticWire":true,
    "RoutingNumber":"23894829384",
    "AccountNumber":"2348902384098",
    "ForFurtherCredit":true,
    "IntermediaryName":"Citi Bank",
    "IntermediaryAccountNumber":"48484848484848",
    "IntermediaryAddress1":"Baker Street 15",
    "IntermediaryAddress2":"",
    "IntermediaryCity":"New York",
    "IntermediaryCountry":"US",
    "IntermediaryPostalCode":"10036",
    "IntermediaryState":"NY",
    "IraDistribution": { \
     "Reason": "string", \
     "FederalTaxType": "string", \
     "StateTaxType": "string", \
     "FederalTaxAmount": 0, \
     "StateTaxAmount": 0 \
   } \
}
```
{% endtab %}

{% tab title="Foreign Wire" %}
| Parameter        | Required | Description                                                                                                                                             |
| ---------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Amount           | True     | This is the amount of funds to be withdrawn. The value must be provided in US dollars. Set this parameter to `null` if `CloseAccount` is set to `true`. |
| CloseAccount     | True     | This boolean value indicates if the trading account must be closed after the withdrawal is performed.                                                   |
| IsDomesticWire   | True     | Indicates if this is a domestic wire transfer. If you're performing a foreign wire transfer, set this parameter to `false`.                             |
| RoutingNumber    | True     | This is the account's number in SWIFT.                                                                                                                  |
| AccountNumber    | True     | This is the target banking account number.                                                                                                              |
| ForFurtherCredit | False    | Set it to `true` if the wire is meant to be sent further to a different bank.                                                                           |
| BankName         | True     | The name of the target bank.                                                                                                                            |
| BankCity         | True     | The city in which the bank is located.                                                                                                                  |
| BankCountry      | True     | The target country.                                                                                                                                     |

For example:

```javascript
{
    "Amount":100,
    "CloseAccount":false,
    "IsDomesticWire":false,
    "RoutingNumber":"23894829384",
    "AccountNumber":"2348902384098",
    "ForFurtherCredit":false,
    "BankName":"Citi Bank",
    "BankCity":"New York",
    "BankCountry":"US"
}
```
{% endtab %}
{% endtabs %}

Here's the final template for this API request:

```
POST apiURL/v1.0/accounts/{accountId}/transfers/wire
```

### Response

In response to this API request, you will receive a JSON dictionary containing detailed information about the withdrawal:

```javascript
{
    "Id":"0c5def88-bec6-4ea6-b10c-08d8dcc6185a",
    "AccountId":0,
    "Mechanism":"Wire",
    "IsDeposit":false,
    "Status":"Submitted",
    "Amount":100.0,
    "TotalAmount":0.0,
    "CreatedAt":"2021-03-01T17:06:15.39Z",
    "ClearingAccountNumber":"5DP05506"
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to send a request to withdraw funds via wire transfers.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```
