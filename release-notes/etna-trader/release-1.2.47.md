---
description: 'Web API updates, support for Thomson Reuters Beta''s FIX Protocol'
---

# Release 1.2.47

## Summary

ETNA Trader receives another major update that brings a set of significant features and improvements. In release 1.2.47 we focused on expanding the functionality of our Web API and also made a few under-the-hood tweaks in the back end to improve performance and user experience. We've also addressed a few discovered bugs, improving the overall stability of ETNA Trader.

### Web API Improvements

By far the biggest improvement of release 1.2.47 is the update of our Web API. First, we've made a few changes to the existing methods for retrieving security information, account information, and placing new orders. Second, we've added a new method for retrieving chart data in the Microsoft Excel format.

#### Retrieving Users' Positions

Starting from version 1.2.47, users' current positions in a particular security can only be retrieved by **providing the ticker symbol** of this security \(as opposed to providing the internal ID of the security in previous releases\).

{% page-ref page="../../rest-api/public-api/positions/get-users-positions-in-security.md" %}

{% hint style="danger" %}
Retrieving users' positions in a particular security via ID is no longer supported.
{% endhint %}

#### Retrieving Security Information

Starting from version 1.2.47,  retrieving information about securities has been split into two sets of methods — one for equities and the other for options:

{% tabs %}
{% tab title="Equities" %}
{% page-ref page="../../rest-api/public-api/securities/get-securitys-info-by-internal-id/" %}

{% page-ref page="../../rest-api/public-api/securities/get-securitys-info-by-ticker.md" %}

{% page-ref page="../../rest-api/public-api/securities/get-securitys-info-by-mask/" %}
{% endtab %}

{% tab title="Options" %}
{% page-ref page="../../rest-api/public-api/securities/get-option-info-by-internal-id.md" %}

{% page-ref page="../../rest-api/public-api/securities/get-option-info-by-ticker.md" %}
{% endtab %}
{% endtabs %}

We've also added two new methods for listing all existing equities and options:

{% page-ref page="../../rest-api/public-api/securities/get-filtered-equities.md" %}

{% page-ref page="../../rest-api/public-api/securities/get-filtered-options.md" %}

#### Placing New Orders

The last change we made to our Web API is the revamped order placement mechanism. Previously, if you wanted to ensure that a new order is properly constructed, you could simply add the dryRun parameter in the request header. Starting from version 1.2.47, we've separated the order placement and replacement procedures into two separate methods:

{% page-ref page="release-1.2.47.md" %}

{% page-ref page="release-1.2.47.md" %}

### Balance Attributes

The first notable improvement of release 1.2.47 is the ability to manage trading accounts' balance attributes. These attributes are displayed in ETNA Trader's **Account Info** widget, and from now on you can determine which of these attributes should be visible to the users.

![](../../.gitbook/assets/screenshot-2019-03-04-at-20.23.29.png)

These attributes can be managed in ETNA Trader's Back Office. There you can enable or disable these attributes as well as modify their descriptions.

![](../../.gitbook/assets/releasenotes1247-1.png)

### 

