---
description: Retrieve trading data for charts in the Excel format
---

# Get Chart Data in the Excel Format

### Overview

This POST endpoint enables you to retrieve chart data for a particular security in the Microsoft Excel \(.xlsx\) format.

{% hint style="warning" %}
In order to retrieve chart date for a particular security in the Microsoft Excel format, you must use an [authorization token](../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **settings** \(body\). This is a JSON dictionary that contains information about the enquired security.

#### Enquired Security Syntax

Here's an example of the request body with the information about the enquired security.

```javascript
{
    "Securities":[4],
    "Indicators":[
        {"name":"Volume",
         "args":[],
         "type":"Volume",
         "text":"Vol"}],
     "TimeFrame":{
         "startDate":1520226000,
         "endDate":1551797512,
         "candlesCount":-1,
         "period":"4h",
         "includeNonMarketData":false},
     "DefaultFileName":"AAPL_4%20hours_From_03.05.2018_To_03.05.2019.xlsx"
 }
```

where:

| Parameter | Description |
| :--- | :--- |
| Securities | This is an array that contains securities which chart data needs to be retrieved. |
| Indicators | This is an array with the required indicators. |
| TimeFrame | This is the timeframe for which the chart data needs to be retrieved. |
| DefaultFileName | This is the filename of the Excel file that will be returned. |
| StartDate | This is the beginning of the period for which the data will be retrieved. |
| EndDate | This is the end of the period for which the data will be retrieved. |
| CandlesCount | This is the number of candles that will be retrieved for the specified time period. |
| Interval | This is the trading data interval for the specified time period.  |

{% hint style="warning" %}
All parameters must be provided in the body JSON; otherwise the chart data will not be retrieved.
{% endhint %}

Here's the final template for this API request:

```text
POST apiURL/v1.0/history/export
```

### Response

In response to this API request, you should expect a .xlsx file that contains chart data for the enquired security. Following is a sample of such file:

{% file src="../../../.gitbook/assets/aapl\_4-hours\_from\_03.05.2018\_to\_03.05.2019.xlsx" caption="Chart Data in .XLSX" %}

![](../../../.gitbook/assets/screenshot-2019-03-05-at-18.11.37.png)

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve chart data for a security in the Excel format.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for retrieving chart data for a security in the Excel format, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

#### Incorrectly Specifying the Request Body 

Another common mistake when attempting to retrieve the chart data for a security is incorrectly structuring the request body. It's critical that you follow the template provided above and specify all of the required parameters. Otherwise you'll receive the 500 status code and the following error message: 

```javascript
{
    "message": "An error occurred while processing your request",
    "error": "Unexpected server error"
}
```

