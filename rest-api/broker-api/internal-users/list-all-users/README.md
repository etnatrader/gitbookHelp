---
description: List all users within a company
---

# List All Users

### Overview

This GET endpoint enables you to list all users within your company, sorted by a particular field. The list of all users is split into multiple pages, each of which can be retrieved in a single request.

{% hint style="warning" %}
In order to retrieve information about a particular user, you must use an [authorization token](../../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are seven required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **pageSize** \(query\). This field indicates the number of users that need to be retrieved per page.
5. **pageNumber** \(query\). This field indicates the number of the page that needs to be retrieved \(all users are split into a set of pages that can be loaded one by one\).
6. **sortBy** \(query\). This is the field by which the retrieved users should be sorted. For example, if the value of this parameter is set to **Id**, the retrieved feedbacks will be sorted by the users' internal identifier in ETNA Trader.
7. **isDesc** \(query\). This field indicates if the list of retrieved users should be sorted in the descending \(true\) or ascending \(false\) order.

There's also one optional parameter worth examining:

* filter \(request query\). This is an SQL query used to retrieve only those users that satisfy the conditions of the query. 

#### Filter Syntax

The syntax for filter queries is rather simple: each parameter of a user can serve as a filter. The conditions that a parameter needs to satisfy can be expressed in the following ways:

1. **Parameter** \(=, &lt;, &gt;, &lt;=, &gt;=\) **value**. For example: `Id = 1007`
2. **Parameter** \(=, contains, startsWith, endsWith\) **string**. For example: `MiddleName = ''`
3. **Parameter** in \(**value1**, **value2**, etc.\). In this case the parameter has to be contained in the set of values in the parentheses to satisfy the filter condition. For example: `Id in (7420, 7630, 9870)`
4. **Parameter** between **Value1** and **Value2**. In this case the parameter has to be in the specified range between Value1 and Value2 to satisfy the filter condition. For example: `AddedDate between #2019-01-09T18:31:42# and #2019-03-14T18:31:42#`.

Boolean values are provided in the following format: `true` and `false`.

Numeric values are provided in the regular format: `2500`.

Strings must be highlighted with single quotation marks: `'USD'`.

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
          <li>MiddleName = &apos;&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all users without a middle name.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>AddedDate &lt;= #2019-03-18T11:10:14.036Z#</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all users who were created out prior to the specified date.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Id between 1 and 1000</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all transactions whose internal identifier lies in the range
            between 1 and 1000.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>{% hint style="info" %}
Note that you can combine different queries to create more complex requests:

* MiddleName = '' and Id between 1 and 1000
{% endhint %}

Here's the final template for this API request:

```text
GET apiURL/v1.0/users
```

### Response

In response to this API request, you'll receive a JSON file with the users from the page specified in the request query:

```javascript
{
  "Result": [
    {
      "Id": 7472,
      "FirstName": "Jim",
      "Middle": "",
      "LastName": "James",
      "EmailAddress": "robert.zakiev@etnatrader.com",
      "Login": "robert.zakievdev",
      "Salutation": "NoSalutation",
      "Suffix": "NoSuffix",
      "AddedDate": "2019-02-12T16:51:00.1335811Z",
      "Enabled": true,
      "Deleted": false,
      "TimeZoneInfoId": "Eastern Standard Time",
      "EntitlementsPhoneNumber": ""
    },
    {
      "Id": 7471,
      "FirstName": "",
      "Middle": "",
      "LastName": "",
      "EmailAddress": "bit12345@etnatrader.com",
      "Login": "bit12345",
      "Salutation": "NoSalutation",
      "Suffix": "NoSuffix",
      "AddedDate": "2019-02-05T00:05:38.0146819Z",
      "Enabled": true,
      "Deleted": false,
      "TimeZoneInfoId": "Eastern Standard Time",
      "PhoneNumber": "+11111111111",
      "EntitlementsPhoneNumber": ""
    },
    {
      "Id": 7470,
      "FirstName": "",
      "Middle": "",
      "LastName": "",
      "EmailAddress": "Maggie@etnatrader.com",
      "Login": "Maggie",
      "Salutation": "NoSalutation",
      "Suffix": "Sr",
      "AddedDate": "2019-02-04T19:46:30.0366288Z",
      "Enabled": true,
      "Deleted": false,
      "TimeZoneInfoId": "Eastern Standard Time",
      "PhoneNumber": "+11111111111",
      "EntitlementsPhoneNumber": ""
    },
    {
      "Id": 7469,
      "FirstName": "",
      "Middle": "N",
      "LastName": "",
      "EmailAddress": "BenMorton@etnatrader.com",
      "Login": "BenMorton",
      "Salutation": "NoSalutation",
      "Suffix": "Third",
      "AddedDate": "2019-02-04T18:52:49.8470817Z",
      "Enabled": true,
      "Deleted": false,
      "TimeZoneInfoId": "Eastern Standard Time",
      "PhoneNumber": "+11111111111",
      "EntitlementsPhoneNumber": ""
    },
    {
      "Id": 7468,
      "FirstName": "",
      "Middle": "T",
      "LastName": "",
      "EmailAddress": "Alfonso@etnatrader.com",
      "Login": "Alfonso",
      "Salutation": "NoSalutation",
      "Suffix": "Fourth",
      "AddedDate": "2019-02-04T17:21:02.729225Z",
      "Enabled": true,
      "Deleted": false,
      "TimeZoneInfoId": "Eastern Standard Time",
      "PhoneNumber": "+11111111111",
      "EntitlementsPhoneNumber": ""
    },
    {
      "Id": 7467,
      "FirstName": "",
      "Middle": "",
      "LastName": "",
      "EmailAddress": "rtrt@etnatrader.com",
      "Login": "rtrt",
      "Salutation": "NoSalutation",
      "Suffix": "NoSuffix",
      "AddedDate": "2019-02-04T15:48:36.4033498Z",
      "Enabled": true,
      "Deleted": false,
      "TimeZoneInfoId": "Eastern Standard Time",
      "PhoneNumber": "+11111111111",
      "EntitlementsPhoneNumber": ""
    },
    {
      "Id": 7466,
      "FirstName": "",
      "Middle": "S",
      "LastName": "",
      "EmailAddress": "Fugi@etnatrader.com",
      "Login": "Fugi",
      "Salutation": "NoSalutation",
      "Suffix": "Jr",
      "AddedDate": "2019-02-04T14:54:10.1157721Z",
      "Enabled": true,
      "Deleted": false,
      "TimeZoneInfoId": "Eastern Standard Time",
      "PhoneNumber": "+11111111111",
      "EntitlementsPhoneNumber": ""
    }
  ],
  "NextPageLink": "https://priv-api-etnatrader-dev.etnasoft.us/api/v1.0/users?pageSize=7&pageNumber=1&sortBy=Id&isDesc=true",
  "PreviousPageLink": "",
  "TotalCount": 6323
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal identifier of the user in ETNA Trader. |
| FirstName | This is the first name of the user in ETNA Trader. |
| Middle | This is the middle name of the user in ETNA Trader. |
| LastName | This is the last name of the user in ETNA Trader. |
| EmailAddress | This is the email address of the user. |
| Login | This is the user's login. |
| Salutation | This is a special salutation used to address this user in emails. |
| Suffix | This is the suffix used when addressing the user \(Jr, Sr, I, II, III, etc.\). |
| AddedDate | This is the date on which this user account was added to ETNA Trader. |
| Enabled | This field indicates if the user is active and can make trades in ETNA Trader. |
| Deleted | This field indicates if the user has been deleted. |
| TimeZoneInfoId | This field indicates the time zone in which the user lives. |
| EntitlementsPhoneNumber | This the user's phone number. |
| NextPageLink | This is the link of the next page of users. |
| PreviousPageLink | This is the link of the previous page of users. |
| TotalCount | This is the total number of users in the company. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to list users.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for retrieving users, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

In the following article we provide in-depth coverage of the syntax for this API request.

