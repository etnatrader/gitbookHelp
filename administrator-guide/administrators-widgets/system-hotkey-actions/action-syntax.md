# Action Syntax

### Introduction

When a user triggers a hotkey, the [previously defined action](./) associated with this hotkey is executed. These actions represent JavaScript code that developers can use to simplify trading routines. For example, you can create an action that doubles the number of shares in the **Trade Ticket** widget. But before that you should learn how to access the data in such widgets. In this article we outline the syntax for hotkey actions and demonstrate real-world examples that are implemented in our own actions.

### Context Types <a id="Webactionsdevelopment-ContextTypes"></a>

There are several types of widget contexts that are available in the _**`widgetContext`**_property of the _**`params`**_parameter \(accessible by _**`params.widgetContext`**_\). Use this property to determine which widget you're in \(`switch` on it\) before you proceed to perform any data modifications.

Different context types \(widgets\) can have different sets of functions, and you can request the current context with the help of the global _**`getContextType()`**_function and the following global constants:

* _**`window.ETNA.WidgetContext.Types.MarketDepth`**_ – market depth widget context;
* _**`window.ETNA.WidgetContext.Types.Chart`**_– chart widget context;
* _**`window.ETNA.WidgetContext.Types.TradeTicket`**_– trade ticket widget context.

### Market Depth Widget Context <a id="Webactionsdevelopment-Marketdepthwidgetcontextreference"></a>

#### 1. Get the Current Context

_**`widgetContext.getContextType()`**_

This method returns _**`window.ETNA.WidgetContext.Types.MarketDepth`**_.

#### 2. Get the Current Ticker Symbol

_**`widgetContext.getSymbol()`**_

This method returns the ticker symbol of a selected security.

#### 3. Get the Current Quote

_**`widgetContext.getQuoteData()`**_

This method returns the currently selected security's quote.

### Chart Widget Context <a id="Webactionsdevelopment-Chartwidgetcontextreference"></a>

#### 1. Get the Current Context

_**`widgetContext.getContextType()`**_

This method returns _**`window.ETNA.WidgetContext.Types.Chart`**_.

#### 2. Get the Current Ticker Symbol

_**`widgetContext.getSymbol()`**_

This method returns the ticker symbol of the displayed security.

#### 3. Get the Current Quote

_**`widgetContext.getQuoteData()`**_

This method returns the currently selected security's quote.

### Trade Ticket Widget Context <a id="Webactionsdevelopment-Tradeticketwidgetcontextreference"></a>

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


