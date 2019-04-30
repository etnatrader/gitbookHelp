# Basic Authentication

### Single-Factor Authentication 

{% tabs %}
{% tab title="Python" %}
{% code-tabs %}
{% code-tabs-item title="Initial Authentication" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://priv-api-et-demo-prod.etnasoft.us/api/"
	EtAppKey = "your EtAppKey from the BO Companies widget"

	token = 'uninitialized'

	username = "your username in ETNA Trader"
	password = "your password in ETNA Trader"

	def initialAuth(self):
	    #Creating a POST request
		authenticationRequest = requests.post(self.baseURL + 'token', 
											  headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Username":self.username, "Password":self.password})

		print('Authorization status code: ' + str(authenticationRequest.status_code) + '\n')

		try:
			responseJSON = authenticationRequest.json()
			print(responseJSON)
			self.token = "Bearer " + responseJSON["Token"]
			return responseJSON
		except:
			return "No response"
			
#Performing initial Authentication
sampleRequest = EtnaAPIRequest()
sampleRequest.initialAuth()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

In this example, there's a class called `EtnaAPIRequest` that has five properties:

* `baseURL` — this is the URL that hosts your API. Each solution has its own base URL for both the Trader and the Developer API.
* `EtAppKey` — this is the unique key of your solution that can be retrieved from the BO companies widget in ETNA Trader.
* `Token` — this is the authentication token that must be provided in all API requests except for the first one \(authentication\).
* `Username` and `password` — these are the credentials of a user on whose behalf all API requests will be made.

The first method — `initialAuth` — creates a POST request to the base URL appended by `token` \(each endpoint has its own unique address\). As for headers, the authentication endpoint requires you to provide the following parameters:

* `"Accept" : "application/json"`— use this parameter to accept the authorization token that will be returned in response to this request.
* `EtAppKey` — use this parameter to identify your app in all requests.
* `Username` and `password` — these are the credentials of the user on whose behalf all subsequent requests will be made.

In response to this request, you'll receive a JSON file that contains the token \(provided that all the parameters were correctly specified\):

```javascript
{'State': 'Succeeded', 'Token': 'Fake/Cl++ZKkDecvgAAAAAOgAAAAAIAACAAAAB8WguNLQWKAUhh7QbSvsHZMGhO6xlNiSFPptfJRlnD0hABAADlr/R6NVs3V+nl2HJlzM8qOLy3MvGU313ecOIsR9GBF14QsRVohtUPRyoiNpdZ9BRql9EdGstABoDNlYF4TLNJeEyF8WEaKL+gEHP4OXmbQTnpD6swG7+2Y3MWe6atpglyzFsJiDoMRuHMMOLbM3h3zy4+E3wgewghduRvBzgRa9pmp7iuCSF9RixJAO+pW+VzNXdfalulcBMdbVBaomN08TATGvrLjsDRKbzMy3j02w1qPc2dE7xo4svIxwWfMj+wpPDUDg4Low4Solyfk3qdK0W9/gYBvGGCB/Ppg6GRJYuFZf5+KHpbb43k/M8QFaXzpmlEL4HTYfC6cjDRsngmOzAwTK0WqT/7NpE+o1X610AAAAC3eKWYjv0Il+s4H0hr+Tkqc6L3+2IcT97KcTCMP7/Xrb7Pa/ybDPoZ3ZVHiU7JBUFaS4MEaZ44u7Zrsu/gbOxG'}
```

You can then extract the returned token and assign it to the `token` property.
{% endtab %}
{% endtabs %}

#### CURL

```text
curl -X POST --header 'Content-Type: application/x-www-form-urlencoded' --header 'Accept: application/json' --header 'Username: yourEmail' --header 'Password: yourPassword' --header 'Et-App-Key: yourAppKey' --header 'Content-Length: 0' 'https://priv-api-et-demo-prod.etnasoft.us/api/token'
```

