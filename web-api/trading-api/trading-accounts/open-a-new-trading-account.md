# Open a New Trading Account

### Introduction

This POST endpoint enables to send a request for opening a new trading account. The process of creating new trading accounts differs based on the clearing firm responsible for handing these requests; in this article we will demonstrate how to open a new paper trading account in ETNA Trader's demo environment.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userId** \(query\). This is the ID of the user account to which the new trading account will be bound.
5. **model** \(body\). This is a JSON file that contains detailed information about the new account opening request.

### Request Body

The body of this request represents the information about the to-be-created account opening request. It must be sent in the JSON format with the parameters described in the following table:

| Parameter | Description |
| :--- | :--- |
| FormType | For paper trading, the parameter must be equal to **Direct**. |
| AccountProvider | This is the clearing firm responsible for handling account requests. For paper trading, specify **PaperTrading**. |

```javascript
{
  "FormType": "Direct",
  "AccountProvider": "PaperTrading"
}
```

Here's the final template for this API request:

```text
POST apiURL/v1.0/user/{userId}/account-requests/open
```

{% hint style="info" %}
To create a new account opening request on behalf of the user whose authorization token you provide in the request header, replace _userId_ with **@me**
{% endhint %}

### Response

In response to this API request, you will receive a JSON file containing information about the status of the request.

```text
{
  "Id": "ed8fcaac-70d6-4045-afb8-febe2d4a6af7",
  "UserId": "7125",
  "Status": "New",
  "FormType": "Direct",
  "RequestType": "Open",
  "AccountProvider": "PaperTrading",
  "CreatedAt": "2019-11-22T15:20:20.4433333Z"
}
```

For convenience purposes, paper trading accounts need not be approved by administrators \(unlike regular accounts that must be approved by both administrators and the clearing firm\). Once a paper trading account opening request has been created, a new account will immediately be created and bound to the user whose ID was provided as a query parameter.

You may list the user's trading accounts via the following API endpoint:

{% page-ref page="../user-accounts/list-users-accounts/" %}

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to send a new account opening request.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Failing to Specify All Body Parameters

Another common mistake when making this request is failing to specify all of the required body parameters. Doing so will result in the 500 status code and the following error message:

```javascript
{
    "message": "An error occurred while processing your request",
    "error": "Unexpected server error"
}
```

