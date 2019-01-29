# Action Syntax

### Introduction

When a user triggers a hotkey, the [previously defined action](./) associated with this hotkey is executed.

When web actions are firing with widget selection there are several types of widget context available in _**`widgetContext`**_ ``property of action function _**`params`**_ **``**parameter. 

### Context Types <a id="Webactionsdevelopment-ContextTypes"></a>

Context types can have different set of functions but can be resolved using  _**`getContextType`**_ **``**function and global constants:

* _**`window.ETNA.WidgetContext.Types.MarketDepth`**_ – market depth widget context
* _**`window.ETNA.WidgetContext.Types.Chart`**_ ``– chart widget context
* _**`window.ETNA.WidgetContext.Types.TradeTicket`**_ ``– trade ticket widget context

### Market depth widget context reference <a id="Webactionsdevelopment-Marketdepthwidgetcontextreference"></a>

_**`widgetContext.getContextType()`**_

Returns _**`window.ETNA.WidgetContext.Types.MarketDepth`**_  constant value.

_**`widgetContext.getSymbol()`**_

Returns widget currently selected symbol.

_**`widgetContext.getQuoteData()`**_

Returns widget current quote.

### Chart widget context reference <a id="Webactionsdevelopment-Chartwidgetcontextreference"></a>

_**`widgetContext.getContextType()`**_

Returns _**`window.ETNA.WidgetContext.Types.Chart`**_ constant value.

_**`widgetContext.getSymbol()`**_

Returns widget currently selected symbol.

_**`widgetContext.getQuoteData()`**_

Returns widget current quote.

### Trade ticket widget context reference <a id="Webactionsdevelopment-Tradeticketwidgetcontextreference"></a>

_**`widgetContext.getContextType()`**_

Returns _**`window.ETNA.WidgetContext.Types.TradeTicket`**_ ``constant value.

_**`widgetContext.getSymbol`**_

Returns widget currently selected symbol.

_**`widgetContext.getLimitPrice(getFromSecondTicket)`**_

_**`getFromSecondTicket`**_:Boolean ``

determines whether the value should be retrieved from  second ticket. Value will be retrieved from first by default.

Retruns limit price set on target ticket

_**`widgetContext.setLimitPrice(value, setToSecondTicket)`**_

_**`value:Number`**_

value to be set on ticket limit price

_**`setToSecondTicket`**_:Boolean ``

determines whether the value should be set on second ticket. Value will be set on first by default

Sets specified value on target ticket limit price.

_**`widgetContext.getStopPrice(getFromSecondTicket`**_\)

_**`getFromSecondTicket`**_:Boolean ``

determines whether the value should be retrieved from second ticket. Value will be retrieved from first by default.

Retruns stop price set on target ticket

_**`widgetContext.setStopPrice(value, setToSecondTicket`**_\)

_**`value:Number`**_

value to be set on ticket stop price

_**`setToSecondTicket`**_:Boolean ``

determines whether the value should be set on second ticket. Value will be set on first by default

Sets specified value on target ticket stop price.

_**`widgetContext.getQuantity(getFromSecondTicket)`**_

_**`getFromSecondTicket`**_:Boolean ``

determines whether the value should be retrieved from second ticket. Value will be retrieved from first by default.

Retruns quantity set on target ticket

_**`widgetContext.setQuantity(value, setToSecondTicket`**_\)

_**`value:Number`**_

quantity to be set on ticket stop price

_**`setToSecondTicket`**_:Boolean ``

determines whether the value should be set on second ticket. Value will be set on first by default

Sets specified quantity on target ticket.

_**`widgetContext.getQuoteData`**_

Returns widget current quote.

_**`widgetContext.getTradeTicketType`**_

Returns trade ticket type. Possible values: 'Simple', 'OTO', 'OCO'  


