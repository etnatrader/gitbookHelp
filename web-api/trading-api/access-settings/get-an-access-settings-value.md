---
description: Retrieve the value of a specific access setting
---

# Get an Access Setting's Value

### Introduction

When you retrieve the [existing access settings for a particular user](get-access-settings-by-category.md), sometimes there's no value for a specific setting in the output, and you need to call this endpoint to retrieve it. This GET endpoint accepts a specific category, two optional filters by **name** and **description**, and returns the required value for that parameter.

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **category** \(path\). The is the category for which the setting's value must be retrieved. 

   Possible values:

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

* **description** \(query\). This is a string filter that will return the value of an access setting with this **description**.
* **startsWith** \(query\). This is string filter that returns the value of an access setting whose **name** starts with this filter.

Here's the final template for this API request:

```text
GET apiURL/v1.0/access-types/Options/value?description=AccountInfo
```

### Response

In response to this API request, you'll receive a JSON file containing the value of the access setting.

```javascript
{
  "AccountInfoFooter": "<span>Footer data</span>"
}
```

