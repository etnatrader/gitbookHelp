---
description: Create a new user in ETNA Trader
---

# Create a New User

## Overview

This POST endpoint enables you to create a new user in ETNA Trader. Information about the new user is provided in the request body as a JSON, and the new user is then automatically added to your company.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **sendInvitationEmail** \(query\). This is a boolean parameter that indicates if the newly created user should receive an invitation email.
5. **user** \(body\). This a JSON file that contains information about the to-be-created user.

Here's the final template for this API request:

```text
POST apiURL/v1.0/users
```

### Request Body Sample

The body of the request represents a JSON file with mandatory parameters required for user creation.

### Smallest User Creation Sample

```javascript
{
 "FirstName": "Robert",
 "LastName": "Techie",
 "EmailAddress": "robert@hello.com", 
 "Login": "robert.techie"
}
```

### Comprehensive User Creation Sample

```javascript
{
  "FirstName": "string", //required
  "Middle": "string", 
  "LastName": "string", //required
  "EmailAddress": "test@dciqwiocjfhaosj.com", //required
  "Login": "string", //required
  "Salutation": "NoSalutation", 
  "Suffix": "NoSuffix", 
  "Enabled": true, 
  "TimeZoneInfoId": "New Zealand Standard Time", 
  "ExpirationDate": "2019-03-10T14:11:54.494Z",
  "PhoneNumber": "string",
  "EntitlementsPhoneNumber": "string"
}
```

where:

| Parameter | Description |
| :--- | :--- |
| FirstName | This is the first name of the user in ETNA Trader. |
| Middle | This is the middle name of the user in ETNA Trader. |
| LastName | This is the last name of the user in ETNA Trader. |
| EmailAddress | This is the email address of the new user. |
| Login | This is the user's login. |
| Salutation | This is a special salutation used to address this user in emails. |
| Suffix | This is the suffix used when addressing the user \(Jr, Sr, I, II, III, etc.\). |
| Enabled | This field indicates if the user is active and can make trades in ETNA Trader. |
| TimeZoneInfoId | This field indicates the time zone in which the user lives. |
| ExpirationDate | This is the date on which the user's account will be disabled. |
| PhoneNumber / EntitlementsPhoneNumber | This the user's phone number. |

### TimeZoneInfoID Values Range

```text
Dateline Standard Time

UTC-11

Samoa Standard Time

Hawaiian Standard Time

Alaskan Standard Time

Pacific Standard Time (Mexico)

Pacific Standard Time

US Mountain Standard Time

Mountain Standard Time (Mexico)

Mountain Standard Time

Central America Standard Time

Central Standard Time

Central Standard Time (Mexico)

Canada Central Standard Time

SA Pacific Standard Time

Eastern Standard Time

US Eastern Standard Time

Venezuela Standard Time

Paraguay Standard Time

Atlantic Standard Time

Central Brazilian Standard Time

SA Western Standard Time

Pacific SA Standard Time

Newfoundland Standard Time

E. South America Standard Time

Argentina Standard Time

SA Eastern Standard Time

Greenland Standard Time

Montevideo Standard Time

UTC-02

Mid-Atlantic Standard Time

Azores Standard Time

Cape Verde Standard Time

Morocco Standard Time

UTC

GMT Standard Time

Greenwich Standard Time

W. Europe Standard Time

Central Europe Standard Time

Romance Standard Time

Central European Standard Time

W. Central Africa Standard Time

Namibia Standard Time

Jordan Standard Time

GTB Standard Time

Middle East Standard Time

Egypt Standard Time

Syria Standard Time

South Africa Standard Time

FLE Standard Time

Israel Standard Time

E. Europe Standard Time

Arabic Standard Time

Arab Standard Time

Russian Standard Time

E. Africa Standard Time

Iran Standard Time

Arabian Standard Time

Azerbaijan Standard Time

Mauritius Standard Time

Georgian Standard Time

Caucasus Standard Time

Afghanistan Standard Time

Ekaterinburg Standard Time

Pakistan Standard Time

West Asia Standard Time

India Standard Time

Sri Lanka Standard Time

Nepal Standard Time

Central Asia Standard Time

Bangladesh Standard Time

N. Central Asia Standard Time

Myanmar Standard Time

SE Asia Standard Time

North Asia Standard Time

China Standard Time

North Asia East Standard Time

Singapore Standard Time

W. Australia Standard Time

Taipei Standard Time

Ulaanbaatar Standard Time

Tokyo Standard Time

Korea Standard Time

Yakutsk Standard Time

Cen. Australia Standard Time

AUS Central Standard Time

E. Australia Standard Time

AUS Eastern Standard Time

West Pacific Standard Time

Tasmania Standard Time

Vladivostok Standard Time

Central Pacific Standard Time

New Zealand Standard Time

UTC+12

Fiji Standard Time

Kamchatka Standard Time

Tonga Standard Time
```

## Response

In response to this API request, you'll receive a JSON file that contains information you specified in the request body along with the new user's internal identifier in ETNA Trader:

```javascript
{
  "Id": 7473, //user's internal identifier in ETNA Trader
  "FirstName": "string",
  "Middle": "s",
  "LastName": "string",
  "EmailAddress": "test@dciqwiocjfhaosj.com",
  "Login": "string",
  "Salutation": "NoSalutation",
  "Suffix": "NoSuffix",
  "AddedDate": "2019-03-06T15:12:43.2333427Z",
  "Enabled": true,
  "Deleted": false,
  "TimeZoneInfoId": "New Zealand Standard Time",
  "ExpirationDate": "2019-03-06T14:11:54.494Z",
  "PhoneNumber": "string",
  "EntitlementsPhoneNumber": "string"
}
```

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to create a new user.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Failing to Provide All Required Parameters

Another common mistake when making this API request is failing to provide all required parameters in the request's body. In the request body sample above we have highlighted all required parameters for this request, so ensure that you provide all of them; otherwise you'll receive the 500 status code and the following error message:

```javascript
{
  "message": "An error occurred while processing your request",
  "error": "Unexpected server error"
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

