# Get Company Logo By Symbol

{% swagger method="get" path="/v{version}/equities/{symbol}/logo" baseUrl="baseURL" summary="Get Company Logo By Symbol" %}
{% swagger-description %}
This endpoint enables you to retrieve company logo image by ticker symbol under which it’s listed on the exchange.
{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="symbol" type="String" required="true" %}
Ticker symbol for the company for which you are retrieving an image.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="	 Successful request, PNG image of company logo." %}

{% endswagger-response %}
{% endswagger %}
