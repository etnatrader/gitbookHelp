# Get Option Info by Internal ID

### CURRENTLY NOT WORKING

### Overview

This GET endpoint enables you to retrieve information about a particular option. Whereas the last three methods deal with equities' information, this endpoint provides information exclusively about options. 

{% hint style="warning" %}
In order to retrieve information about a particular option, you must use an [authorization token](../authentication/requesting-tokens/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **ID** \(path\). This is the ID of the option whose information you'd like to retrieve.

### Response

In response to this API request, you'll receive a JSON file with comprehensive information about the enquired option:

```text

```

