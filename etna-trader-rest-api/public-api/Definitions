
<a name="definitions"></a>
## Definitions

<a name="accountvalueitem"></a>
### AccountValueItem

|Name|Schema|
|---|---|
|**Date**  <br>*optional*|string (date-time)|
|**Value**  <br>*optional*|number (double)|


<a name="base64filemapmodel"></a>
### Base64FileMapModel

|Name|Schema|
|---|---|
|**Data**  <br>*optional*|string|
|**Name**  <br>*optional*|string|
|**Type**  <br>*optional*|string|


<a name="chartcomparerequestmodel"></a>
### ChartCompareRequestModel

|Name|Schema|
|---|---|
|**Securities**  <br>*optional*|< [SecurityModel](#securitymodel) > array|
|**SecuritiesHistorySettings**  <br>*optional*|[SecurityHistoryRequestSettings](#securityhistoryrequestsettings)|


<a name="charthistorymodel"></a>
### ChartHistoryModel

|Name|Schema|
|---|---|
|**IndicatorsHistory**  <br>*optional*|< < [IndicatorHistoryMapModel](#indicatorhistorymapmodel) > array > array|
|**SecurityHistory**  <br>*optional*|< < [TimeSeriesValueCandleMapModel](#timeseriesvaluecandlemapmodel) > array > array|
|**SupportResistanceHistory**  <br>*optional*|[SupportResistanceMapModel](#supportresistancemapmodel)|


<a name="charthistoryrequestmodel"></a>
### ChartHistoryRequestModel

|Name|Schema|
|---|---|
|**IndicatorsHistorySettings**  <br>*optional*|< [IndicatorHistoryRequestSettings](#indicatorhistoryrequestsettings) > array|
|**Security**  <br>*optional*|[SecurityModel](#securitymodel)|
|**SecurityHistorySettings**  <br>*optional*|[SecurityHistoryRequestSettings](#securityhistoryrequestsettings)|


<a name="createordermodel"></a>
### CreateOrderModel

|Name|Description|Schema|
|---|---|---|
|**ClientId**  <br>*optional*|Client order id.|string|
|**Exchange**  <br>*optional*|Desired exchange.|string|
|**ExecInst**  <br>*optional*|Execution instruction.|enum (DoNotIncrease, DoNotReduce, AllOrNone)|
|**ExecutionInstructions**  <br>*optional*|Algo order execution instructions.|< string, string > map|
|**ExpireDate**  <br>*optional*|Expire date. Assigned by client.|string (date-time)|
|**ExtendedHours**  <br>*optional*|indicates the extended trading session for GTX order execution (pre-market session, post-market session)<br>if empty - than there is no specific requirement for extended session|string|
|**Legs**  <br>*optional*|Order legs|< [CreateOrderModel](#createordermodel) > array|
|**Price**  <br>*optional*|Price (not used for some order types).|number (double)|
|**Quantity**  <br>*optional*|Quantity. Assigned by client.  <br>**Minimum value** : `0`|number (double)|
|**SecurityId**  <br>*optional*|Security id.  <br>**Minimum value** : `1`  <br>**Maximum value** : `2147483647`|integer (int32)|
|**Side**  <br>*optional*|Client side comments.|enum (Buy, Sell, SellShort, BuyToCover)|
|**StopPrice**  <br>*optional*|Stop price (used for stop orders).|number (double)|
|**TimeInforce**  <br>*optional*|Time in force.|enum (Day, GoodTillCancel, AtTheOpening, ImmediateOrCancel, FillOrKill, GoodTillCrossing, GoodTillDate, GoodTillTime)|
|**Token**  <br>*optional*|Additional identity key (usid in market scanner).|string|
|**TrailingLimitAmount**  <br>*optional*||number (double)|
|**TrailingLimitAmountType**  <br>*optional*||enum (Absolute, Persentage)|
|**TrailingStopAmount**  <br>*optional*||number (double)|
|**TrailingStopAmountType**  <br>*optional*||enum (Absolute, Persentage)|
|**Type**  <br>*optional*|Type. Assigned by client.|enum (Market, Limit, Stop, StopLimit, Pegged, TrailingStop, TrailingStopLimit, OneCancelOther, OneTriggerOther, External)|
|**ValidationsToBypass**  <br>*optional*|Flag property indicating validation rules to bypass|integer (int32)|


<a name="createwatchlistmodel"></a>
### CreateWatchlistModel

|Name|Schema|
|---|---|
|**Name**  <br>*optional*|string|
|**Securities**  <br>*optional*|< integer (int32) > array|


<a name="editablehotkeymodel"></a>
### EditableHotkeyModel

|Name|Schema|
|---|---|
|**ActionId**  <br>*optional*|integer (int32)|
|**Description**  <br>*optional*|string|
|**KeyboardShortcut**  <br>*optional*|string|
|**Parameters**  <br>*optional*|< [HotkeyParameterMapModel](#hotkeyparametermapmodel) > array|


<a name="expecting"></a>
### Expecting

|Name|Schema|
|---|---|
|**Reason**  <br>*optional*|string|
|**State**  <br>*optional*  <br>*read-only*|string|
|**Step**  <br>*optional*|string|
|**Token**  <br>*optional*|string|


<a name="failed"></a>
### Failed

|Name|Schema|
|---|---|
|**Reason**  <br>*optional*|string|
|**State**  <br>*optional*  <br>*read-only*|string|
|**Step**  <br>*optional*|string|


<a name="feemodel"></a>
### FeeModel

|Name|Schema|
|---|---|
|**CommissionId**  <br>*optional*|string|
|**Id**  <br>*optional*|integer (int32)|
|**Leverage**  <br>*optional*|number (double)|
|**Seizure**  <br>*optional*|enum (Placement, Execution, Fill, Proportional, Order)|
|**Value**  <br>*optional*|number (double)|
|**ValueType**  <br>*optional*|enum (Absolute, Coefficient)|


<a name="formula"></a>
### Formula
Formula model


|Name|Schema|
|---|---|
|**Expression**  <br>*optional*|string|
|**Id**  <br>*optional*|integer (int32)|
|**Name**  <br>*optional*|string|


<a name="frameparams"></a>
### FrameParams

|Name|Schema|
|---|---|
|**Description**  <br>*optional*|string|
|**Name**  <br>*optional*|string|
|**TargetPercent**  <br>*optional*|number (double)|
|**Tolerance**  <br>*optional*|number (double)|


<a name="hotkeymapmodel"></a>
### HotkeyMapModel

|Name|Schema|
|---|---|
|**ActionId**  <br>*optional*|integer (int32)|
|**ActionName**  <br>*optional*|string|
|**ActionResource**  <br>*optional*|[WebActionMapModel](#webactionmapmodel)|
|**Description**  <br>*optional*|string|
|**Id**  <br>*optional*|integer (int32)|
|**KeyboardShortcut**  <br>*optional*|string|
|**Parameters**  <br>*optional*|< [HotkeyParameterMapModel](#hotkeyparametermapmodel) > array|


<a name="hotkeyparametermapmodel"></a>
### HotkeyParameterMapModel

|Name|Schema|
|---|---|
|**HotkeyId**  <br>*optional*|integer (int32)|
|**Id**  <br>*optional*|integer (int32)|
|**ParameterId**  <br>*optional*|integer (int32)|
|**ParameterName**  <br>*optional*|string|
|**ParameterType**  <br>*optional*|integer (int32)|
|**Value**  <br>*optional*|string|


<a name="ifileupload"></a>
### IFileUpload

|Name|Description|Schema|
|---|---|---|
|**Data**  <br>*optional*|**Pattern** : `"^(?:[A-Za-z0-9+/]{4})*(?:[A-Za-z0-9+/]{2}==\|[A-Za-z0-9+/]{3}=)?$"`|string (byte)|
|**Description**  <br>*optional*||string|
|**FileKey**  <br>*optional*||string|
|**FileName**  <br>*optional*||string|
|**Id**  <br>*optional*||integer (int32)|
|**Timestamp**  <br>*optional*||string (date-time)|
|**Type**  <br>*optional*||enum (Other, ImageJpeg, ImageGif, ImagePng, ImageBitmap, ImageIco, TextHtml, TextPlain, VideoMpeg, VideoQuicktime)|


<a name="isecurity"></a>
### ISecurity

|Name|Schema|
|---|---|
|**AddedDate**  <br>*optional*  <br>*read-only*|string (date-time)|
|**AllowMargin**  <br>*optional*  <br>*read-only*|boolean|
|**AllowShort**  <br>*optional*  <br>*read-only*|boolean|
|**AllowTrade**  <br>*optional*  <br>*read-only*|boolean|
|**BaseCurrency**  <br>*optional*  <br>*read-only*|string|
|**CmsSuffix**  <br>*optional*  <br>*read-only*|string|
|**ContractSize**  <br>*optional*  <br>*read-only*|number (double)|
|**CqsSuffix**  <br>*optional*  <br>*read-only*|string|
|**Currency**  <br>*optional*  <br>*read-only*|string|
|**Cusip**  <br>*optional*  <br>*read-only*|string|
|**Description**  <br>*optional*  <br>*read-only*|string|
|**Enabled**  <br>*optional*  <br>*read-only*|boolean|
|**Exchange**  <br>*optional*  <br>*read-only*|string|
|**ExpirationDate**  <br>*optional*  <br>*read-only*|string (date-time)|
|**ExpirationName**  <br>*optional*  <br>*read-only*|string|
|**ExpirationType**  <br>*optional*  <br>*read-only*|enum (Regular, Quarterly, Weekly, Flex, Undefined, Mini, NonStandard)|
|**Id**  <br>*optional*  <br>*read-only*|integer (int32)|
|**Industry**  <br>*optional*  <br>*read-only*|string|
|**Isin**  <br>*optional*  <br>*read-only*|string|
|**Leverage**  <br>*optional*  <br>*read-only*|number (double)|
|**MarginRate**  <br>*optional*  <br>*read-only*|number (double)|
|**ModifyDate**  <br>*optional*  <br>*read-only*|string (date-time)|
|**Name**  <br>*optional*  <br>*read-only*|string|
|**NasdaqSuffix**  <br>*optional*  <br>*read-only*|string|
|**OptionType**  <br>*optional*  <br>*read-only*|enum (Call, Put, Undefined)|
|**ParentId**  <br>*optional*  <br>*read-only*|integer (int32)|
|**Precision**  <br>*optional*  <br>*read-only*|integer (int32)|
|**Price**  <br>*optional*  <br>*read-only*|number (double)|
|**QuoteSubscriptionKey**  <br>*optional*  <br>*read-only*|string|
|**Sector**  <br>*optional*  <br>*read-only*|string|
|**Sedol**  <br>*optional*  <br>*read-only*|string|
|**SeriesId**  <br>*optional*  <br>*read-only*|integer (int32)|
|**Source**  <br>*optional*  <br>*read-only*|integer (int32)|
|**SourceId**  <br>*optional*  <br>*read-only*|string|
|**StrikePrice**  <br>*optional*  <br>*read-only*|number (double)|
|**Suffix**  <br>*optional*  <br>*read-only*|string|
|**Symbol**  <br>*optional*  <br>*read-only*|string|
|**TickSize**  <br>*optional*  <br>*read-only*|number (double)|
|**Type**  <br>*optional*  <br>*read-only*|enum (BankersAcceptance, CertificateOfDeposit, CollateralizeMortgageObligation, CorporateBond, CommercialPaper, CorporatePrivatePlacement, CommonStock, FederalHousingAuthority, FederalHomeLoan, FederalNationalMortgageAssociation, ForeignExchangeContract, Future, GovernmentNationalMortgageAssociation, TreasuriesPlusAgencyDebenture, MutualFund, MortgageInterestOnly, MortgagePrincipleOnly, MortgagePrivatePlacement, MiscellaneousPassThru, MunicipalBond, NoIsitcSecurityType, Option, PreferredStock, RepurchaseAgreement, ReverseRepurchaseAgreement, StudentLoanMarketingAssociation, TimeDeposit, UsTreasuryBill, Warrant, CatsTigersLions, WildcardEntry, ConvertibleBond, MortgageIoette, Index, FakeStockForNonStandartOption, Right, Cryptocurrency, ETF, DepositoryReceipt, CoveredWarrant, Unit)|
|**UnderlyingSecuritySymbol**  <br>*optional*  <br>*read-only*|string|
|**Unit**  <br>*optional*  <br>*read-only*|string|
|**VolumePrecision**  <br>*optional*  <br>*read-only*|integer (int32)|


<a name="indicatorhistorymapmodel"></a>
### IndicatorHistoryMapModel

|Name|Schema|
|---|---|
|**Date**  <br>*optional*|integer (int32)|
|**Values**  <br>*optional*|< number (double) > array|


<a name="indicatorhistoryrequestsettings"></a>
### IndicatorHistoryRequestSettings

|Name|Schema|
|---|---|
|**CandlesCount**  <br>*optional*|integer (int32)|
|**EndDate**  <br>*optional*|integer (int32)|
|**IncludeNonMarketData**  <br>*optional*|boolean|
|**Interval**  <br>*optional*|integer (int32)|
|**Offset**  <br>*optional*|integer (int32)|
|**Period**  <br>*optional*|string|
|**Signature**  <br>*optional*|string|
|**StartDate**  <br>*optional*|integer (int32)|


<a name="levelinfomapmodel"></a>
### LevelInfoMapModel

|Name|Schema|
|---|---|
|**BottomPrice**  <br>*optional*|number (double)|
|**GreenCandles**  <br>*optional*|< integer (int32) > array|
|**RedCandles**  <br>*optional*|< integer (int32) > array|
|**TopPrice**  <br>*optional*|number (double)|


<a name="modifyordermodel"></a>
### ModifyOrderModel
Modify order parameters


|Name|Description|Schema|
|---|---|---|
|**ClientId**  <br>*optional*|Client order id.|string|
|**ExecutionInstructions**  <br>*optional*|Algo order execution instructions.|< string, string > map|
|**ExpireDate**  <br>*optional*|Expire date. Assigned by client.|string (date-time)|
|**Id**  <br>*required*|Internal order id.  <br>**Minimum value** : `1`  <br>**Maximum value** : `2147483647`|integer (int32)|
|**Legs**  <br>*optional*|Order legs|< [ModifyOrderModel](#modifyordermodel) > array|
|**Price**  <br>*optional*|Price (not used for some order types).|number (double)|
|**Quantity**  <br>*optional*|Quantity. Assigned by client.  <br>**Minimum value** : `0`|number (double)|
|**StopPrice**  <br>*optional*|Stop price (used for stop orders).|number (double)|
|**TrailingLimitAmount**  <br>*optional*||number (double)|
|**TrailingLimitAmountType**  <br>*optional*||enum (Absolute, Persentage)|
|**TrailingStopAmount**  <br>*optional*||number (double)|
|**TrailingStopAmountType**  <br>*optional*||enum (Absolute, Persentage)|
|**ValidationsToBypass**  <br>*optional*|Flag property indicating validation rules to bypass|integer (int32)|


<a name="ordermodel"></a>
### OrderModel

|Name|Description|Schema|
|---|---|---|
|**AccountId**  <br>*optional*|Account id. Assigned by OMS.|integer (int32)|
|**AveragePrice**  <br>*optional*|Average execution price. Assigned by executor.|number (double)|
|**ClientId**  <br>*optional*|Client order id (ClOrdID). Assigned by OMS.|string|
|**Comment**  <br>*optional*|Client side comments. Assigned by client.|string|
|**CounterPartyOrderId**  <br>*optional*|Executor order id. Assigned by executor.|string|
|**CreateDate**  <br>*optional*|Creation date. Assigned by OMS.|string (date-time)|
|**Date**  <br>*optional*|Last modification date. Assigned by OMS.|string (date-time)|
|**Description**  <br>*optional*|Used to indicate reject reason or broker comment. Assigned by executor.|string|
|**Exchange**  <br>*optional*|Desired exchange. Assigned by client.|string|
|**ExecBrocker**  <br>*optional*|Order route name. Assigned by executor.|string|
|**ExecId**  <br>*optional*|Execution id.|string|
|**ExecInst**  <br>*optional*|Execution instruction. Assigned by client.|enum (DoNotIncrease, DoNotReduce, AllOrNone)|
|**ExecutedQuantity**  <br>*optional*|Executed quantity. Assigned by executor.|number (double)|
|**ExecutionInstructions**  <br>*optional*|Algo order execution instructions.|< string, string > map|
|**ExecutionStatus**  <br>*optional*|Last modification status. Assigned by OMS or executor.|enum (New, PartiallyFilled, Filled, DoneForDay, Canceled, Replaced, PendingCancel, Stopped, Rejected, Suspended, PendingNew, Calculated, Expired, AcceptedForBidding, PendingReplace, Error, Held)|
|**ExecutionVenue**  <br>*optional*|Executor name, to which the order was routed. Assigned by OMS router.|string|
|**ExpireDate**  <br>*optional*|Expire date. Assigned by client.|string (date-time)|
|**ExtendedHours**  <br>*optional*|indicates the extended trading session for GTX order execution (pre-market session, post-market session)<br>if empty - than there is no specific requirement for extended session|string|
|**Id**  <br>*optional*|Unique order id. Assigned by OMS.|integer (int32)|
|**InitialType**  <br>*optional*|Initial type. Assigned by OMS.|enum (Market, Limit, Stop, StopLimit, Pegged, TrailingStop, TrailingStopLimit, OneCancelOther, OneTriggerOther, External)|
|**IsExternal**  <br>*optional*|This property indicates that order was accepted from external system and fields like ClientOrderId should be persisted.<br>It's a hack for orders from MessageAcceptor.<br>Assigned be client.|boolean|
|**LastMarket**  <br>*optional*|Exchange where order was filled. Assigned by executor.|string|
|**LastPrice**  <br>*optional*|Last quote. Assigned by executor.|number (double)|
|**LastQuantity**  <br>*optional*|Last transaction executed quantity. Assigned by executor.|number (double)|
|**LeavesQuantity**  <br>*optional*|Unfilled quantity. Assigned by executor.|number (double)|
|**Legs**  <br>*optional*|Multileg order legs. Assigned by client.|< [OrderModel](#ordermodel) > array|
|**OrigClientId**  <br>*optional*|Client order id (ClOrdID). Assigned by OMS.|string|
|**ParentClientId**  <br>*optional*|Client order id (ClOrdID) of parent order in a case of mleg order.|string|
|**ParentId**  <br>*optional*|Parent order id. Assigned by OMS.|integer (int32)|
|**ParentRequestId**  <br>*optional*||integer (int32)|
|**Price**  <br>*optional*|Price (not used for some order types). Assigned by client.|number (double)|
|**Quantity**  <br>*optional*|Quantity. Assigned by client.|number (double)|
|**RequestId**  <br>*optional*|Request id. Assigned by OMS.|integer (int32)|
|**RequestStatus**  <br>*optional*|Indicate order processing status within OMS. Assigned by OMS.|enum (RequireValidation, Validated, Rejected, Executing, Complete, Error)|
|**SecurityId**  <br>*optional*|Security id. Assigned by client.|integer (int32)|
|**SettDate**  <br>*optional*|date of settlement. Received from execution venue or calculated by OMS, assigned by OMS or executor.|string (date-time)|
|**SettlementDate**  <br>*optional*|Date of settlement deal|string (date-time)|
|**Side**  <br>*optional*|Side. Assigned by client.|enum (Buy, Sell, SellShort, BuyToCover)|
|**StateId**  <br>*optional*|State id. Assigned by OMS.|integer (int32)|
|**Status**  <br>*optional*|Current order status. Assigned by OMS or executor.|enum (New, PartiallyFilled, Filled, DoneForDay, Canceled, Replaced, PendingCancel, Stopped, Rejected, Suspended, PendingNew, Calculated, Expired, AcceptedForBidding, PendingReplace, Error, Held)|
|**StopPrice**  <br>*optional*|Stop price (used for stop orders). Assigned by client.|number (double)|
|**Target**  <br>*optional*|Execution target. Assigned by OMS.|enum (Ignore, New, Modify, Cancel, Execution, Status, CancelReject, Reject, Error, All)|
|**TimeInForce**  <br>*optional*|Time in force. Assigned by client.|enum (Day, GoodTillCancel, AtTheOpening, ImmediateOrCancel, FillOrKill, GoodTillCrossing, GoodTillDate, GoodTillTime)|
|**Token**  <br>*optional*|Additional identity key (usid in market scanner).|string|
|**TrailingLimitAmount**  <br>*optional*|Assigned by client.|number (double)|
|**TrailingLimitAmountType**  <br>*optional*|Assigned by client.|enum (Absolute, Persentage)|
|**TrailingStopAmount**  <br>*optional*|Assigned by client.|number (double)|
|**TrailingStopAmountType**  <br>*optional*|Assigned by client.|enum (Absolute, Persentage)|
|**TransType**  <br>*optional*|Execution transaction type.|enum (New, Cancel, Correct, Status)|
|**TransactionDate**  <br>*optional*|Last transaction date. Assigned by OMS or executor.|string (date-time)|
|**Type**  <br>*optional*|Type. Assigned by client.|enum (Market, Limit, Stop, StopLimit, Pegged, TrailingStop, TrailingStopLimit, OneCancelOther, OneTriggerOther, External)|
|**UserId**  <br>*optional*|User id. Assigned by OMS.|integer (int32)|
|**ValidationsToBypass**  <br>*optional*|Flag property indicating validation rules to bypass|integer (int32)|


<a name="pagingresult-hotkeymapmodel"></a>
### PagingResult[HotkeyMapModel]

|Name|Description|Schema|
|---|---|---|
|**NextPageLink**  <br>*optional*|Next page|string|
|**PreviousPageLink**  <br>*optional*|Previous page|string|
|**Result**  <br>*optional*|Result collection|< [HotkeyMapModel](#hotkeymapmodel) > array|
|**TotalCount**  <br>*optional*|Items total count|integer (int32)|


<a name="pagingresult-pricealertinfomodel"></a>
### PagingResult[PriceAlertInfoModel]

|Name|Description|Schema|
|---|---|---|
|**NextPageLink**  <br>*optional*|Next page|string|
|**PreviousPageLink**  <br>*optional*|Previous page|string|
|**Result**  <br>*optional*|Result collection|< [PriceAlertInfoModel](#pricealertinfomodel) > array|
|**TotalCount**  <br>*optional*|Items total count|integer (int32)|


<a name="pagingresult-rebalanceframe"></a>
### PagingResult[RebalanceFrame]

|Name|Description|Schema|
|---|---|---|
|**NextPageLink**  <br>*optional*|Next page|string|
|**PreviousPageLink**  <br>*optional*|Previous page|string|
|**Result**  <br>*optional*|Result collection|< [RebalanceFrame](#rebalanceframe) > array|
|**TotalCount**  <br>*optional*|Items total count|integer (int32)|


<a name="pagingresult-submitfeedbackmodel"></a>
### PagingResult[SubmitFeedbackModel]

|Name|Description|Schema|
|---|---|---|
|**NextPageLink**  <br>*optional*|Next page|string|
|**PreviousPageLink**  <br>*optional*|Previous page|string|
|**Result**  <br>*optional*|Result collection|< [SubmitFeedbackModel](#submitfeedbackmodel) > array|
|**TotalCount**  <br>*optional*|Items total count|integer (int32)|


<a name="pagingresult-transactionmapmodel"></a>
### PagingResult[TransactionMapModel]

|Name|Description|Schema|
|---|---|---|
|**NextPageLink**  <br>*optional*|Next page|string|
|**PreviousPageLink**  <br>*optional*|Previous page|string|
|**Result**  <br>*optional*|Result collection|< [TransactionMapModel](#transactionmapmodel) > array|
|**TotalCount**  <br>*optional*|Items total count|integer (int32)|


<a name="pagingresult-webactionmapmodel"></a>
### PagingResult[WebActionMapModel]

|Name|Description|Schema|
|---|---|---|
|**NextPageLink**  <br>*optional*|Next page|string|
|**PreviousPageLink**  <br>*optional*|Previous page|string|
|**Result**  <br>*optional*|Result collection|< [WebActionMapModel](#webactionmapmodel) > array|
|**TotalCount**  <br>*optional*|Items total count|integer (int32)|


<a name="phonenumbermodel"></a>
### PhoneNumberModel

|Name|Schema|
|---|---|
|**PhoneNumber**  <br>*optional*|string|
|**PhoneNumberState**  <br>*optional*|enum (NotLinked, Active, Suspended, NotVerified)|


<a name="positionmodel"></a>
### PositionModel

|Name|Schema|
|---|---|
|**AccountId**  <br>*optional*|integer (int32)|
|**AverageClosePrice**  <br>*optional*|number (double)|
|**AverageOpenPrice**  <br>*optional*|number (double)|
|**CompanyName**  <br>*optional*|string|
|**ContractSize**  <br>*optional*|number (double)|
|**CostBasis**  <br>*optional*|number (double)|
|**CreateDate**  <br>*optional*|string (date-time)|
|**DailyCloseProfitLoss**  <br>*optional*|number (double)|
|**DailyCostBasis**  <br>*optional*|number (double)|
|**DayQuantity**  <br>*optional*|number (double)|
|**ExcessChanges**  <br>*optional*|number (double)|
|**Id**  <br>*optional*|integer (int32)|
|**ModifyDate**  <br>*optional*|string (date-time)|
|**Name**  <br>*optional*|string|
|**Quantity**  <br>*optional*|number (double)|
|**RealizedProfitLoss**  <br>*optional*|number (double)|
|**SecurityCurrency**  <br>*optional*|string|
|**SecurityId**  <br>*optional*|integer (int32)|
|**SecurityType**  <br>*optional*|string|
|**StopLossPrice**  <br>*optional*|number (double)|
|**Symbol**  <br>*optional*|string|
|**TakeProfitPrice**  <br>*optional*|number (double)|


<a name="pricealerteditablemodel"></a>
### PriceAlertEditableModel
Editable price alert


|Name|Description|Schema|
|---|---|---|
|**Argument**  <br>*optional*|Trigger value  <br>**Minimum value** : `0`|number (double)|
|**ExpirationDate**  <br>*optional*|Expiration date|integer (int64)|
|**Field**  <br>*required*|Alert type|string|
|**Operator**  <br>*required*|Alert trigger operator|string|
|**SecurityId**  <br>*optional*|Alert trigger security id  <br>**Minimum value** : `0`  <br>**Maximum value** : `2147483647`|integer (int32)|
|**State**  <br>*optional*|Target alert state|enum (New, Expired, Completed, Stopped)|


<a name="pricealertinfomodel"></a>
### PriceAlertInfoModel
Price alert info


|Name|Description|Schema|
|---|---|---|
|**Argument**  <br>*optional*|Trigger value|number (double)|
|**CreatedDate**  <br>*optional*|Created Date|integer (int64)|
|**ExpirationDate**  <br>*optional*|Expiration date|integer (int64)|
|**Field**  <br>*optional*|Alert type|string|
|**Id**  <br>*optional*|Internal price alert identifier|integer (int32)|
|**Operator**  <br>*optional*|Alert trigger operator|string|
|**SecurityId**  <br>*optional*|Alert trigger security id|integer (int32)|
|**State**  <br>*optional*|Target alert state|enum (New, Expired, Completed, Stopped)|


<a name="quotemodel"></a>
### QuoteModel

|Name|Schema|
|---|---|
|**Ask**  <br>*optional*|number (double)|
|**Bid**  <br>*optional*|number (double)|
|**Last**  <br>*optional*|number (double)|
|**OpenInterest**  <br>*optional*|number (double)|
|**Volume**  <br>*optional*|number (double)|


<a name="rebalanceframe"></a>
### RebalanceFrame

|Name|Schema|
|---|---|
|**Descendants**  <br>*optional*|< [RebalanceFrame](#rebalanceframe) > array|
|**Description**  <br>*optional*|string|
|**Id**  <br>*optional*|integer (int32)|
|**IsReferenced**  <br>*optional*|boolean|
|**Name**  <br>*optional*|string|
|**TargetPercent**  <br>*optional*|number (double)|
|**Tolerance**  <br>*optional*|number (double)|
|**UnitType**  <br>*optional*  <br>*read-only*|enum (Node, SecurityLeaf, Cash)|


<a name="rebalancemodel"></a>
### RebalanceModel

|Name|Schema|
|---|---|
|**AbsoluteActualPercent**  <br>*optional*|number (double)|
|**AbsoluteTargetPercent**  <br>*optional*|number (double)|
|**AbsoluteTolerance**  <br>*optional*|number (double)|
|**ActualPercent**  <br>*optional*|number (double)|
|**Descendants**  <br>*optional*|< [RebalanceModel](#rebalancemodel) > array|
|**Description**  <br>*optional*|string|
|**Gain**  <br>*optional*|number (double)|
|**GainPercent**  <br>*optional*|number (double)|
|**Id**  <br>*optional*|integer (int32)|
|**Name**  <br>*optional*|string|
|**TargetPercent**  <br>*optional*|number (double)|
|**Tolerance**  <br>*optional*|number (double)|
|**UnitType**  <br>*optional*  <br>*read-only*|enum (Node, SecurityLeaf, Cash)|
|**Value**  <br>*optional*|number (double)|


<a name="securitycontainerframe"></a>
### SecurityContainerFrame

|Name|Schema|
|---|---|
|**Descendants**  <br>*optional*  <br>*read-only*|< [RebalanceFrame](#rebalanceframe) > array|
|**Description**  <br>*optional*|string|
|**Id**  <br>*optional*|integer (int32)|
|**IsReferenced**  <br>*optional*|boolean|
|**Name**  <br>*optional*|string|
|**Security**  <br>*optional*|[ISecurity](#isecurity)|
|**SecurityId**  <br>*optional*|integer (int32)|
|**TargetPercent**  <br>*optional*|number (double)|
|**Tolerance**  <br>*optional*|number (double)|
|**UnitType**  <br>*optional*  <br>*read-only*|enum (Node, SecurityLeaf, Cash)|


<a name="securityframeparams"></a>
### SecurityFrameParams

|Name|Schema|
|---|---|
|**Description**  <br>*optional*|string|
|**Name**  <br>*optional*|string|
|**SecurityId**  <br>*optional*|integer (int32)|
|**TargetPercent**  <br>*optional*|number (double)|
|**Tolerance**  <br>*optional*|number (double)|


<a name="securityhistoryrequestsettings"></a>
### SecurityHistoryRequestSettings

|Name|Schema|
|---|---|
|**CandlesCount**  <br>*optional*|integer (int32)|
|**EndDate**  <br>*optional*|integer (int32)|
|**IncludeNonMarketData**  <br>*optional*|boolean|
|**Interval**  <br>*optional*|integer (int32)|
|**Period**  <br>*optional*|string|
|**StartDate**  <br>*optional*|integer (int32)|


<a name="securitymodel"></a>
### SecurityModel

|Name|Schema|
|---|---|
|**AddedDate**  <br>*optional*|string (date-time)|
|**BaseCurrency**  <br>*optional*|string|
|**ContractSize**  <br>*optional*|number (double)|
|**Currency**  <br>*optional*|string|
|**Cusip**  <br>*optional*|string|
|**Description**  <br>*optional*|string|
|**Exchange**  <br>*optional*|string|
|**ExpirationDate**  <br>*optional*|string (date-time)|
|**ExpirationType**  <br>*optional*|enum (Regular, Quarterly, Weekly, Flex, Undefined, Mini, NonStandard)|
|**Id**  <br>*optional*|integer (int32)|
|**Industry**  <br>*optional*|string|
|**Isin**  <br>*optional*|string|
|**MarginRate**  <br>*optional*|number (double)|
|**ModifyDate**  <br>*optional*|string (date-time)|
|**OptionType**  <br>*optional*|enum (Call, Put, Undefined)|
|**ParentId**  <br>*optional*|integer (int32)|
|**Precision**  <br>*optional*|integer (int32)|
|**Sector**  <br>*optional*|string|
|**Sedol**  <br>*optional*|string|
|**SeriesId**  <br>*optional*|integer (int32)|
|**Source**  <br>*optional*|integer (int32)|
|**StrikePrice**  <br>*optional*|number (double)|
|**Suffix**  <br>*optional*|string|
|**Symbol**  <br>*optional*|string|
|**TickSize**  <br>*optional*|number (double)|
|**Type**  <br>*optional*|enum (BankersAcceptance, CertificateOfDeposit, CollateralizeMortgageObligation, CorporateBond, CommercialPaper, CorporatePrivatePlacement, CommonStock, FederalHousingAuthority, FederalHomeLoan, FederalNationalMortgageAssociation, ForeignExchangeContract, Future, GovernmentNationalMortgageAssociation, TreasuriesPlusAgencyDebenture, MutualFund, MortgageInterestOnly, MortgagePrincipleOnly, MortgagePrivatePlacement, MiscellaneousPassThru, MunicipalBond, NoIsitcSecurityType, Option, PreferredStock, RepurchaseAgreement, ReverseRepurchaseAgreement, StudentLoanMarketingAssociation, TimeDeposit, UsTreasuryBill, Warrant, CatsTigersLions, WildcardEntry, ConvertibleBond, MortgageIoette, Index, FakeStockForNonStandartOption, Right, Cryptocurrency, ETF, DepositoryReceipt, CoveredWarrant, Unit)|
|**UnderlyingSecuritySymbol**  <br>*optional*|string|
|**Unit**  <br>*optional*|string|
|**VolumePrecision**  <br>*optional*|integer (int32)|


<a name="securitysignature"></a>
### SecuritySignature

|Name|Schema|
|---|---|
|**Exchange**  <br>*optional*|string|
|**Symbol**  <br>*optional*|string|


<a name="submitfeedbackmodel"></a>
### SubmitFeedbackModel

|Name|Schema|
|---|---|
|**BuildVersion**  <br>*optional*|string|
|**Comment**  <br>*optional*|string|
|**Contacts**  <br>*optional*|string|
|**ImagesToUpload**  <br>*optional*|< [Base64FileMapModel](#base64filemapmodel) > array|
|**Subject**  <br>*optional*|string|


<a name="subscriptionmodel"></a>
### SubscriptionModel
Web API notification service subscription representation


|Name|Description|Schema|
|---|---|---|
|**Channel**  <br>*optional*|Channel for subscription messages delivery|enum (Email, MobileText, MobilePush, WebPopupAlert, Disabled)|
|**State**  <br>*optional*|Subscription state|enum (NotLinked, Active, Suspended, NotVerified)|
|**SubscriptionType**  <br>*optional*|Subscription notification type|enum (OrderExecution, OrderForReview, OrderOnReview, OrderPlacement, OrderReplacement, PriceAlert)|


<a name="succeed"></a>
### Succeed

|Name|Schema|
|---|---|
|**State**  <br>*optional*  <br>*read-only*|string|
|**Token**  <br>*optional*|string|


<a name="supportresistancemapmodel"></a>
### SupportResistanceMapModel

|Name|Schema|
|---|---|
|**Levels**  <br>*optional*|< [LevelInfoMapModel](#levelinfomapmodel) > array|
|**ResistancePrice**  <br>*optional*|number (double)|
|**SupportPrice**  <br>*optional*|number (double)|


<a name="timeseriesvaluecandlemapmodel"></a>
### TimeSeriesValueCandleMapModel

|Name|Schema|
|---|---|
|**Close**  <br>*optional*|number (double)|
|**DateTime**  <br>*optional*  <br>*read-only*|string (date-time)|
|**High**  <br>*optional*|number (double)|
|**IsMarket**  <br>*optional*|boolean|
|**Low**  <br>*optional*|number (double)|
|**Open**  <br>*optional*|number (double)|
|**OpenInterest**  <br>*optional*|integer (int32)|
|**Time**  <br>*optional*|integer (int32)|
|**ValuationLevels**  <br>*optional*|< number (double) > array|
|**Volume**  <br>*optional*|number (double)|


<a name="timezoneinfoitem"></a>
### TimeZoneInfoItem

|Name|Schema|
|---|---|
|**description**  <br>*optional*|string|
|**ianaId**  <br>*optional*|string|
|**name**  <br>*optional*|string|


<a name="transactionmapmodel"></a>
### TransactionMapModel

|Name|Schema|
|---|---|
|**AccountId**  <br>*optional*|integer (int32)|
|**Date**  <br>*optional*|string (date-time)|
|**Description**  <br>*optional*|string|
|**Fee**  <br>*optional*|[FeeModel](#feemodel)|
|**Id**  <br>*optional*|integer (int32)|
|**IsDayTrade**  <br>*optional*|boolean|
|**LeavesQuantity**  <br>*optional*|number (double)|
|**OrderStateId**  <br>*optional*|integer (int32)|
|**Quantity**  <br>*optional*|number (double)|
|**SecurityId**  <br>*optional*|integer (int32)|
|**Type**  <br>*optional*|enum (Undefined, Commission, OrderExecution, OptionExpiration, Payment, ManualManipulation, Clearing, Rpl)|
|**Value**  <br>*optional*|number (double)|


<a name="tuple-int32-string"></a>
### Tuple[Int32,String]

|Name|Schema|
|---|---|
|**m_Item1**  <br>*optional*|integer (int32)|
|**m_Item2**  <br>*optional*|string|


<a name="tuple-phonenumbermodel-int32"></a>
### Tuple[PhoneNumberModel,Int32]

|Name|Schema|
|---|---|
|**m_Item1**  <br>*optional*|[PhoneNumberModel](#phonenumbermodel)|
|**m_Item2**  <br>*optional*|integer (int32)|


<a name="useraccountmodel"></a>
### UserAccountModel

|Name|Schema|
|---|---|
|**AccessType**  <br>*optional*|enum (Full, ReadOnly, ClosePositionsOnly)|
|**Alias**  <br>*optional*|string|
|**ClearingAccount**  <br>*optional*|string|
|**Enabled**  <br>*optional*|boolean|
|**Id**  <br>*optional*|integer (int32)|
|**MarginType**  <br>*optional*|enum (Empty, Cash, Margin, DayTrader, MarginIra)|


<a name="userinfomodel"></a>
### UserInfoModel

|Name|Schema|
|---|---|
|**AddedDate**  <br>*optional*|string (date-time)|
|**Email**  <br>*optional*|string|
|**FirstName**  <br>*optional*|string|
|**LastName**  <br>*optional*|string|
|**Login**  <br>*optional*|string|
|**MiddleName**  <br>*optional*|string|
|**Salutation**  <br>*optional*|enum (NoSalutation, Mr, Mrs, Ms, Dr, Sir, Madam)|
|**Suffix**  <br>*optional*|enum (NoSuffix, Jr, Sr, Second, Third, Fourth)|
|**UserId**  <br>*optional*|integer (int32)|


<a name="verifyordermodel"></a>
### VerifyOrderModel

|Name|Description|Schema|
|---|---|---|
|**Commission**  <br>*optional*|The commission of the order.|number (double)|
|**Commissions**  <br>*optional*|The commission of the order.|< string, number (double) > map|
|**Cost**  <br>*optional*|The cost of the order.|number (double)|
|**ErrorDescription**  <br>*optional*|Error description.|string|
|**ErrorDescriptionArgs**  <br>*optional*|Error description arguments.|< string > array|
|**IsSuccessful**  <br>*optional*|Result.|boolean|
|**NetCost**  <br>*optional*|The net cost of the order.|number (double)|
|**Quotes**  <br>*optional*|Order validation quotes.|< [QuoteModel](#quotemodel) > array|


<a name="watchlistmodel"></a>
### WatchlistModel

|Name|Schema|
|---|---|
|**CreateDate**  <br>*optional*|string (date-time)|
|**Description**  <br>*optional*|string|
|**Id**  <br>*optional*|integer (int32)|
|**ModifyDate**  <br>*optional*|string (date-time)|
|**Name**  <br>*optional*|string|
|**ReadOnly**  <br>*optional*|boolean|
|**SecurityList**  <br>*optional*|< [SecurityModel](#securitymodel) > array|
|**Source**  <br>*optional*|string|
|**Type**  <br>*optional*|enum (UserList, SystemList, Snapshot)|


<a name="webactionmapmodel"></a>
### WebActionMapModel

|Name|Schema|
|---|---|
|**Action**  <br>*optional*|string|
|**Description**  <br>*optional*|string|
|**Id**  <br>*optional*|integer (int32)|
|**Name**  <br>*optional*|string|
|**Parameters**  <br>*optional*|< [WebActionParameterMapModel](#webactionparametermapmodel) > array|


<a name="webactionparametermapmodel"></a>
### WebActionParameterMapModel

|Name|Schema|
|---|---|
|**ActionId**  <br>*optional*|integer (int32)|
|**Id**  <br>*optional*|integer (int32)|
|**Name**  <br>*optional*|string|
|**Type**  <br>*optional*|integer (int32)|



