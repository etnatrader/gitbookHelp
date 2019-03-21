---
description: List a fraction of all user feedback
---

# List Users' Feedback

### Overview

This GET endpoint enables you to list user feedback across the entire company. This feedback is split into numerous pages, and you can retrieve each page with a separate API call. Unlike the regular user feedback listing functionality that fetches feedback for a particular user, this method retrieves the entirety of feedback provided by all users.

{% hint style="warning" %}
In order to list users's, you must use an [authorization token]() of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are seven required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request]().
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **pageSize** \(query\). This field indicates the number of user feedbacks that need to be retrieved per page.
5. **pageNumber** \(query\). This field indicates the number of the page that need to be retrieved \(all user feedbacks are split into a set of pages that can be loaded one by one\).
6. **sortBy** \(query\). This is the field by which the retrieved user feedbacks should be sorted. For example, if the value of this parameter is set to **Contacts**, the retrieved feedbacks will be sorted by the users' contact information.
7. **isDesc** \(query\). This field indicates if the list of retrieved feedbacks should be sorted in the descending \(true\) or ascending \(false\) order.

There's also one optional parameter worth examining:

* filter \(request query\). This is an SQL query used to retrieve only those feedbacks that satisfy the conditions of the query. 

#### Filter Syntax

The syntax for filter queries is rather simple: each parameter of a feedback can serve as a filter. The conditions that a parameter needs to satisfy can be expressed in the following ways:

1. **Parameter** \(=, &lt;, &gt;, &lt;=, &gt;=\) **value**. For example: `Timestamp = 0`
2. **Parameter** \(=, contains, startsWith, endsWith\) **string**. For example: `UserAgent contains 'Mozilla'`
3. **Parameter** in \(**value1**, **value2**, etc.\). In this case the parameter has to be contained in the set of values in the parentheses to satisfy the filter condition. For example: `Id in (7420, 7630, 9870)`
4. **Parameter** between **Value1** and **Value2**. In this case the parameter has to be in the specified range between Value1 and Value2 to satisfy the filter condition. For example: `Timestamp between 1552398906 and 1553590520`.

Boolean values are provided in the following format: `true` and `false`.

Numeric values are provided in the regular format: `2500`.

Strings must be highlighted with quotation marks: `'USD'`.

Dates must be highlighted with with the pound sign: `#2019-08-09T18:31:42#`.

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
          <li>Timestamp between 1552398906 and 1553590520</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves feedbacks whose submission date lies in the specified range.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>UserAgent contains &apos;macOS&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves feedbacks who were submitted from a macOS-like operating system.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>BuildVersion = &apos;1.2.47.149&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves feedbacks that were submitted from ETNA Trader of version 1.2.47.149</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Id = 573</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves a specific feedback with ID 573.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Contacts endsWith &apos;etnasoft.com&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all feedbacks in which the sender&apos;s email address end with
            a specific string.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Subject startsWith &apos;CRITICAL&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all feedbacks in which the feedback subject starts with the
            word &apos;CRITICAL&apos;.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Comment = &apos;&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all feedbacks with empty subjects.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Login = &apos;robert.zak&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all feedbacks of a specific user.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>SupportTicket = &apos;string&apos;</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Retrieves all feedbacks without a corresponding support ticket.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>{% hint style="info" %}
Note that you can combine different queries to create more complex requests:

* UserAgent contains 'macOS' and BuildVersion = '1.2.47.149'
{% endhint %}

Here's the final template for this API request:

```text
GET apiURL/v1.0/feedbacks
```

### Response

```javascript
{
  "Result": [
    {
      "Id": 555,
      "Contacts": "romanboss@gmail.com",
      "Subject": "Add Id to user search fields",
      "Comment": "Add Id to user search fields in BO Users widget",
      "Login": "rzhukov",
      "UserAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36",
      "Timestamp": 1548936907,
      "BuildVersion": "1.2.46.177",
      "Files": [
        {
          "Url": "/storage.axd/1bcd26f1-ecfb-4721-9a96-9d446f07b029",
          "IsImage": true,
          "Type": "image/png",
          "FileName": "Screen Shot 2019-01-31 at 7.14.28 AM.png"
        }
      ]
    },
    {
      "Id": 554,
      "Contacts": "kevingliebe@gmail.com",
      "Subject": "Option expiration",
      "Comment": "When a call option expires, shouldn't the \"broker\" automatically exercise the option on my behalf and therefore I should own the stock?  I let a call option expire and nothing happened. ",
      "Login": "kevinkrg6",
      "UserAgent": "flavorNormal v.3.21.3(54); Android 8.1.0 API 27; ONEPLUS ONEPLUS A5010; en_US",
      "Timestamp": 1548793641,
      "BuildVersion": "1.2.46.177",
      "Files": []
    },
    {
      "Id": 553,
      "Contacts": "guerralorenzo18@gmail.com",
      "Subject": "Price Data ",
      "Comment": "Hi I woulld like to use the demo simuilator withe real time data can you tell me the fees to pay ? thank You\nLorenzo ",
      "Login": "lorenz123",
      "UserAgent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36",
      "Timestamp": 1548317661,
      "BuildVersion": "1.2.46.177",
      "Files": []
    },
    {
      "Id": 552,
      "Contacts": "elias.shaan8@gmail.com",
      "Subject": "Covered Calls",
      "Comment": "I was wondering how I could establish a covered call on this simulator. Everytime I try to sell a call it states my equity balance is too low which makes sense of course if I didn't own the underlying asset. How could I make the system recognize that I own collateral for the option?",
      "Login": "elias123456789",
      "UserAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36",
      "Timestamp": 1548293159,
      "BuildVersion": "1.2.46.177",
      "Files": []
    },
    {
      "Id": 551,
      "Contacts": "pimpom2321@gmail.com",
      "Subject": "qUESTION",
      "Comment": "Why all the trades I am doing are going to \"suspended\" status?",
      "Login": "pimpom",
      "UserAgent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36",
      "Timestamp": 1548091741,
      "BuildVersion": "1.2.46.177",
      "Files": []
    },
    {
      "Id": 550,
      "Contacts": "weshazelrigg@gmail.com",
      "Subject": "Account Tab",
      "Comment": "",
      "Login": "Ranger518",
      "UserAgent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36",
      "Timestamp": 1547871269,
      "BuildVersion": "1.2.46.177",
      "Files": []
    },
    {
      "Id": 549,
      "Contacts": "weshazelrigg@gmail.com",
      "Subject": "how to show gain or loss",
      "Comment": "",
      "Login": "Ranger518",
      "UserAgent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36",
      "Timestamp": 1547871252,
      "BuildVersion": "1.2.46.177",
      "Files": []
    },
    {
      "Id": 548,
      "Contacts": "daniele.cermelli@gmail.com",
      "Subject": "IV Ranking / Percentile",
      "Comment": "Is it possible to see the IV Rank or Percentile? I see the IV % but cannot find IV Percentile / Rank.",
      "Login": "DanyTrade",
      "UserAgent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36",
      "Timestamp": 1547822545,
      "BuildVersion": "1.2.46.177",
      "Files": []
    },
    {
      "Id": 547,
      "Contacts": "huntersoasis@yahoo.com",
      "Subject": "how do you delete some of the accounts?",
      "Comment": "how do you delete some of the accounts or give a sub account cash. ",
      "Login": "huntersoasis",
      "UserAgent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36",
      "Timestamp": 1547737113,
      "BuildVersion": "1.2.46.177",
      "Files": []
    },
    {
      "Id": 546,
      "Contacts": "frankie vautrin. 5032701930",
      "Subject": "interested in opening a real trading account. need some learning classes or tutorials?",
      "Comment": "classes?",
      "Login": "1frdfreak",
      "UserAgent": "flavorNormal v.3.21.1(53); Android 8.0.0 API 26; LGE LG-LS998; en_US",
      "Timestamp": 1547221565,
      "BuildVersion": "1.2.46.177",
      "Files": []
    }
  ],
  "NextPageLink": "https://priv-api-etnatrader-dev.etnasoft.us/api/v1.0/feedbacks?pageSize=10&pageNumber=1&sortBy=Id&isDesc=true",
  "PreviousPageLink": "",
  "TotalCount": 529
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Result | This is an array that contains the retrieved feedbacks \(the number of elements in the array depends on the value set in the **pageSize** parameter\). |
| Id | This is the internal identifier of the feedback in ETNA Trader. |
| Contacts | This is the users' contact information. |
| Subject | This is the subject line of a user feedback. |
| Comment | This is the body of a user feedback. |
| Login | This is the login of the user who's submitted the feedback. |
| UserAgent | This is the platform used by the user when they submitted the feedback. |
| TimeStamp | This is the time \(in C\# ticks\) when the feedback was submitted. |
| BuildVersion | This is the version of ETNA Trader that the user was using when they submitted the feedback. |
| Files | This is an array with the files the user attached when submitting the feedback. |
| NextPageLink | This is the next page of the user feedback. |
| PreviousPageLink | This is the previous page of the user feedback. |
| TotalCount | This is the total number of user feedbacks. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to list all users' feedback.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for listing all users' feedback, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

#### Failing to Specify the Query Parameters

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

