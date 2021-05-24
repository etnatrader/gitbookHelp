---
description: Retrieve all available access settings for a specific category
---

# Get Access Settings by Category

### Overview

This GET endpoint enables you to retrieve all access settings for a specific category. In ETNA Trader, both brokers and users can customize the appearance of the platform and its components. Furthermore, some of these components can have a different layout depending on the user \(e.g. some users have access to options trading while others do not\). And in order to properly display the UI for each user, it's necessary to retrieve the user's settings for different UI components. To do that, you need to first call this endpoint to determine which settings are actually available for the user.

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/requesting-tokens/). The value of this header must have the following format: `Bearer BQ898r9fefi` \(`Bearer` + 1 space + the token\).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **category** \(path\). The is the category for which the available settings must be retrieved. Possible values:
   * `ClientsAccess`.
   * `DisplayType`. 
   * `Exchange`
   * `GridColumns`
   * `Indicator`
   * `IndicatorOptions`
   * `Options`
   * `Theme`
   * `Timeframe`
   * `Widget`

There are also two optional parameters:

* **description** \(query\). This is a string filter that will return a specific access setting with the provided description.
* **startsWith** \(query\). This is string filter that returns access settings whose **name** parameter starts with the specified string.

Here's the final template for this API request:

```text
GET apiURL/v1.0/access-types/Options/allowed?startsWith=Option
```

### Response

In response to this API request, you'll receive a JSON file containing the list of access settings.

```javascript
[
  {
    "Id": 425,
    "Name": "AllowDepositWithdrawalDetails",
    "Category": "Options",
    "Description": "AccountInfo",
    "Options": "12",
    "OptionsType": "checkBox"
  },
  {
    "Id": 435,
    "Name": "AllowCommissionsAndFeesDetails",
    "Category": "Options",
    "Description": "AccountInfo",
    "Options": "12",
    "OptionsType": "checkBox"
  },
  {
    "Id": 551,
    "Name": "AccountInfoFooter",
    "Category": "Options",
    "Description": "AccountInfo",
    "Options": "12",
    "OptionsType": "input"
  },
  {
    "Id": 552,
    "Name": "AllowAccountInfoFooter",
    "Category": "Options",
    "Description": "AccountInfo",
    "Options": "12",
    "OptionsType": "checkBox"
  }
]
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
      <td style="text-align:left">Id</td>
      <td style="text-align:left">Internal ID of the access setting.</td>
    </tr>
    <tr>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">The name of access setting (filtered by the <b>startsWith</b> query parameter).</td>
    </tr>
    <tr>
      <td style="text-align:left">Category</td>
      <td style="text-align:left">The category specified as the path parameter.</td>
    </tr>
    <tr>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">The description of the access setting (filtered by the <b>description</b> query
        parameter).</td>
    </tr>
    <tr>
      <td style="text-align:left">Options</td>
      <td style="text-align:left">The ID of the setting in internal databases.</td>
    </tr>
    <tr>
      <td style="text-align:left">OptionsType</td>
      <td style="text-align:left">
        <p>The type of the setting. Possible values:</p>
        <ul>
          <li><code>input</code> &#x2014; text field</li>
          <li><code>spinner</code> &#x2014; the value of such settings can re retrieved
            via this endpoint. In that endpoint, simply insert the <b>Name</b> parameter
            from this endpoint into the <b>startsWith</b> query parameter.</li>
          <li><code>checkbox</code>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

