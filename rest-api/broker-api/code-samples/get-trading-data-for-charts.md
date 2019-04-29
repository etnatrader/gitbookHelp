# Get Trading Data for Charts

### Get Candles and Indicators for a Security

{% page-ref page="../historical-data/get-candles-and-indicators-for-charts/" %}

{% tabs %}
{% tab title="Python" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://priv-api-et-demo-prod.etnasoft.us/api/"
	EtAppKey = "Et App Key from the BO Companies widget"

	token = 'uninitialized'

	username = "your username"
	password = "your password"

	def simpleAuth(self):
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
    
    def getCandlesAndIndicators(self, securityInfoBody):

		getCandlesAndIndicatorsRequest = requests.put(self.baseURL + 'v1.0/history/symbols/',
													  headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Authorization":self.token},
													  json = securityInfoBody
													  )

		try:
			responseJSON = getCandlesAndIndicatorsRequest.json()
			print (responseJSON)
			return responseJSON
		except:
			return "No response"
			
#Performing initial Authentication
sampleRequest = EtnaAPIRequest()
sampleRequest.simpleAuth()

#declaring chart model
chartDataModel = {
"Security":
	{"Symbol":"AAPL",
	"Exchange":"XNAS",
	"Currency":"USD"},	
"SecurityHistorySettings":
	{"StartDate":1542776400,
	"EndDate":1550764844,
	"CandlesCount":-1,
	"Period":"4h",
	"Interval":-7,
	"IncludeNonMarketData":False},
"IndicatorsHistorySettings":[
	{"Signature":"MACD|4h|false|12|26|9",
	"Interval":-7,
	"StartDate":1542776400,
	"EndDate":1550764844,
	"CandlesCount":-1,
	"Offset":0,
	"Indicator":{
		"id":4,
		"indicatorId":1,
		"type":"movingAverageConvergenceDivergenceIndicator",
		"position":"lower",
		"external":True,
		"settings":{
			"id":4,
			"type":"movingAverageConvergenceDivergenceIndicator",
			"shortThickness":2,
			"longThickness":2,
			"shortBrush":"32c814",
			"longBrush":"dc1414",
			"signalBrush":"ff9900",
			"shortPeriod":12,
			"longPeriod":26,
			"signalPeriod":9,
			"showLastValue":True,
			"showCurrentPoint":True,
			"showLevelBands":False}}}]
}

#retrieving candles and indicators for the Apple stock
sampleRequest.getCandlesAndIndicators(chartDataModel)
```

This method — `getCandlesAndIndicators()` — enables you to retrieve chart data \(candles and indicators\) for a specific security. In response to this request, you'll receive a JSON file with the pricing data that can be used to draw charts. 
{% endtab %}

{% tab title="JavaScript" %}

{% endtab %}

{% tab title="C\#" %}

{% endtab %}
{% endtabs %}

#### CURL

```text
curl -X PUT --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer yourToken' --header 'Et-App-Key: yourKey' -d '{"Security": \ 
 	{"Symbol":"AAPL", \ 
 	"Exchange":"XNAS", \ 
 	"Currency":"USD"}, \ 
 	 \ 
 "SecurityHistorySettings": \ 
 	{"StartDate":1542776400, \ 
 	"EndDate":1550764844, \ 
 	"CandlesCount":-1, \ 
 	"Period":"4h", \ 
 	"Interval":-7, \ 
 	"IncludeNonMarketData":false}, \ 
  \ 
 "IndicatorsHistorySettings":[ \ 
 	{"Signature":"MACD|4h|false|12|26|9", \ 
 	"Interval":-7, \ 
 	"StartDate":1542776400, \ 
 	"EndDate":1550764844, \ 
 	"CandlesCount":-1, \ 
 	"Offset":0, \ 
 	"Indicator":{ \ 
 		"id":4, \ 
 		"indicatorId":1, \ 
 		"type":"movingAverageConvergenceDivergenceIndicator", \ 
 		"position":"lower", \ 
 		"external":true, \ 
 		"settings":{ \ 
 			"id":4, \ 
 			"type":"movingAverageConvergenceDivergenceIndicator", \ 
 			"shortThickness":2, \ 
 			"longThickness":2, \ 
 			"shortBrush":"32c814", \ 
 			"longBrush":"dc1414", \ 
 			"signalBrush":"ff9900", \ 
 			"shortPeriod":12, \ 
 			"longPeriod":26, \ 
 			"signalPeriod":9, \ 
 			"showLastValue":true, \ 
 			"showCurrentPoint":true, \ 
 			"showLevelBands":false}}}] \ 
 }' 'https://priv-api-et-demo-prod.etnasoft.us/api/v1.0/history/symbols'
```



