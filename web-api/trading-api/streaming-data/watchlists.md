# Watchlists

### Subscribe to Сhanges in the List of Traders' Watchlists <a id="Watchlist-Subscribe(&#x421;hangesinthelistofwatchlist)"></a>

| Parameter | Value |
| :--- | :--- |
| **Cmd** | Subscribe.txt |
| **SessionId** | Session ID from the authentication request |
| **Keys** | The ID of the user whose watchlists you would like to retrieve |
| **EntityType** | Watchlist |
| **HttpClientType** | WebSocket |

**Example:** {"Cmd":"Subscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"1159","EntityType":"Watchlist","HttpClientType":"WebSocket"}‌

### Unsubscribe from Сhanges in the List of Traders' Watchlists <a id="Watchlist-Unsubscribe"></a>

| Parameter | Value |
| :--- | :--- |
| **Cmd** | Unsubscribe.txt |
| **SessionId** | Session ID from the authentication request |
| **Keys** | The ID of the user whose watchlists you would like to unsubscribe from |
| **EntityType** | Watchlist |
| **HttpClientType** | WebSocket |

**Example:** {"Cmd":"Unsubscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"1159","EntityType":"Watchlist","HttpClientType":"WebSocket"}‌

### Message <a id="Watchlist-Message"></a>

In response to this request, you will receive the updated list of watchlists in the JSON format.‌

**Example:**‌

**{**‌

* "EntityType":"Watchlist"
* "id":"3013",
* "Key":"1159",
* "CreateDate":"09/08/2015 09:20:49",
* "ModifyDate":"09/08/2015 09:20:49",
* "Description":"",
* "IsDeleted":"True",
* "Name":"Stocks",
* "Type":"UserList",
* "UserId":"1159"

**}**‌

### Subscribe to the Content of a Specific Watchlist <a id="Watchlist-Subscribe(Contentofspecifiedwatchlist)"></a>

| Parameter | Value |
| :--- | :--- |
| **Cmd** | Subscribe.txt |
| **SessionId** | Session ID from the authentication request |
| **Keys** | The ID of the watchlist whose changes you would like to subscribe to |
| **EntityType** | WatchlistContent |
| **HttpClientType** | WebSocket |

**Example:** {"Cmd":"Subscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"287","EntityType":"WatchlistContent","HttpClientType":"WebSocket"}‌

### Unsubscribe from the Content of a Specific Watchlist <a id="Watchlist-Subscribe(Contentofspecifiedwatchlist)-1"></a>

| Parameter | Value |
| :--- | :--- |
| **Cmd** | Unsubscribe.txt |
| **SessionId** | Session ID from the authentication request |
| **Keys** | The ID of the watchlist whose changes you would like to unsubscribe from |
| **EntityType** | WatchlistContent |
| **HttpClientType** | WebSocket |

**Example:** {"Cmd":"Unsubscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"287","EntityType":"WatchlistContent","HttpClientType":"WebSocket"}‌

### Message <a id="Watchlist-Message.1"></a>

In response to this request, you will receive changes in the specified watchlist.‌

**Example:**‌

**{**‌

* "EntityType":"WatchlistContent",
* "Key":"287",
* "AddedSymbols":"680410",
* "RemovedSymbols":"null",

**}**

