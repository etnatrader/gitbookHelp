---
description: Fetch all recent news for a specific security
---

# Get News for a Security

### Introduction

This GET endpoint enables you to fetch the list of all recent news for a specific security by providing its ticker symbol. 

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/requesting-tokens/). The value of this header must have the following format: `Bearer BQ898r9fefi` \(`Bearer` + 1 space + the token\).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **symbol** \(query\). This is the ticker symbol of the security for which the news must be fetched.

Here's the final template for this API request:

```text
GET apiURL/v1.0/news?symbol=AAPL
```

### Response

In response to this API request, you'll receive a JSON file containing the list of the recent news for the specified security.

```javascript
[
  {
    "Key": "AAPL",
    "Date": 1573732801,
    "Source": "AAPL",
    "Header": "Apple&#39;s new 16-inch MacBook pro, a Google checking account?",
    "Attachment": "https://www.yahoo.com/entertainment/apples-16-inch-macbook-pro-120001975.html?.tsrc=rss",
    "Content": "Today&#39;s major tech headlines include first impressions of Apple&#39;s new MacBook Pro, Google possibly offering checking accounts in 2020 and Disney Plus&#39; big launch that included over 10 million sign-ups.",
    "NewsId": 0
  },
  {
    "Key": "AAPL",
    "Date": 1573729200,
    "Source": "AAPL",
    "Header": "Beware of Runs on Bond Funds",
    "Attachment": "https://finance.yahoo.com/m/fc7b20c5-b0b7-3d99-b897-061b961cabad/beware-of-runs-on-bond-funds.html?.tsrc=rss",
    "Content": "In a less favorable market, however, bond fund investors could get hurt—not so much by worsening fundamentals, but the funds’ difficulty to meet redemptions in an illiquid market.  As much as 50% of the assets in high-yield bond funds and 15% of assets of all fixed-income funds could be vulnerable to a liquidity shortfall in the event of heavy investor redemptions.  “There are more risks to open-end bond funds than people are willing to acknowledge,” says Mark Grant, chief global strategist B. Riley FBR.",
    "NewsId": 0
  },
  {
    "Key": "AAPL",
    "Date": 1573725660,
    "Source": "AAPL",
    "Header": "AbbVie Sold $30 Billion in Bonds, and Two More Numbers to Know",
    "Attachment": "https://finance.yahoo.com/m/0551125d-2be3-3dc0-bf9e-e75bb4ad69bc/abbvie-sold-%2430-billion-in.html?.tsrc=rss",
    "Content": "You may have heard that number cited recently as the value of an asteroid called 16 Psyche .  If humans ever manage to mine the asteroid, a flood of space-gold would completely crater the terrestrial market.  All that extra supply would cause today’s gold price to plummet.",
    "NewsId": 0
  }
]
```

where:

| Parameter | Description |
| :--- | :--- |
| Key | This is the ticker symbol of the security for which the news were fetched. |
| Date | This is the date of the news article. |
| Source | This is the ticker symbol of the security for which the news were fetched. |
| Header | This is the header of the news article. |
| Attachment | This is the URL of the news. |
| Content | This is a preview of the news article. |
| NewsId | This is the ID of the news article. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve the news for a specific security.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Failing to Specify the Query Parameters

It's crucial to understand that the _**security**_ parameter must be provided in the request; otherwise you'll receive the 404 status code.

