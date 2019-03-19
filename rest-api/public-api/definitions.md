# Terms and Definitions

## Definitions

### AccountValueItem

| Name | Schema |
| :--- | :--- |
| **Date**   _optional_ | string \(date-time\) |
| **Value**   _optional_ | number \(double\) |

### Base64FileMapModel

| Name | Schema |
| :--- | :--- |
| **Data**   _optional_ | string |
| **Name**   _optional_ | string |
| **Type**   _optional_ | string |

### ChartCompareRequestModel

| Name | Schema |
| :--- | :--- |
| **Securities**   _optional_ | &lt; [SecuritySignature](definitions.md#securitysignature) &gt; array |
| **SecuritiesHistorySettings**   _optional_ | [SecurityHistoryRequestSettings](definitions.md#securityhistoryrequestsettings) |

### ChartHistoryModel

| Name | Schema |
| :--- | :--- |
| **IndicatorsHistory**   _optional_ | &lt; &lt; [IndicatorHistoryMapModel](definitions.md#indicatorhistorymapmodel) &gt; array &gt; array |
| **SecurityHistory**   _optional_ | &lt; &lt; [TimeSeriesValueCandleMapModel](definitions.md#timeseriesvaluecandlemapmodel) &gt; array &gt; array |
| **SupportResistanceHistory**   _optional_ | [SupportResistanceMapModel](definitions.md#supportresistancemapmodel) |

### ChartHistoryRequestModel

| Name | Schema |
| :--- | :--- |
| **IndicatorsHistorySettings**   _optional_ | &lt; [IndicatorHistoryRequestSettings](definitions.md#indicatorhistoryrequestsettings) &gt; array |
| **Security**   _optional_ | [SecuritySignature](definitions.md#securitysignature) |
| **SecurityHistorySettings**   _optional_ | [SecurityHistoryRequestSettings](definitions.md#securityhistoryrequestsettings) |

### CreateOrderResource

| Name | Description | Schema |
| :--- | :--- | :--- |
| **ClientId**   _optional_ | Client order id. | string |
| **Exchange**   _optional_ | Desired exchange. | string |
| **ExecInst**   _optional_ | Execution instruction. | enum \(DoNotIncrease, DoNotReduce, AllOrNone\) |
| **ExecutionInstructions**   _optional_ | Algo order execution instructions. | &lt; string, string &gt; map |
| **ExpireDate**   _optional_ | Expire date. Assigned by client. | string \(date-time\) |
| **ExtendedHours**   _optional_ | indicates the extended trading session for GTX order execution \(pre-market session, post-market session\) if empty - than there is no specific requirement for extended session | string |
| **Legs**   _optional_ | Order legs | &lt; [CreateOrderResource](definitions.md#createorderresource) &gt; array |
| **Price**   _optional_ | Price \(not used for some order types\). | number \(double\) |
| **Quantity**   _optional_ | Quantity. Assigned by client.   **Minimum value** : `0` | number \(double\) |
| **Side**   _optional_ | Client side comments. | enum \(Buy, Sell, SellShort, BuyToCover\) |
| **StopPrice**   _optional_ | Stop price \(used for stop orders\). | number \(double\) |
| **Symbol**   _optional_ | Security symbol. | string |
| **TimeInforce**   _optional_ | Time in force. | enum \(Day, GoodTillCancel, AtTheOpening, ImmediateOrCancel, FillOrKill, GoodTillCrossing, GoodTillDate, GoodTillTime\) |
| **Token**   _optional_ | Additional identity key \(usid in market scanner\). | string |
| **TrailingLimitAmount**   _optional_ |  | number \(double\) |
| **TrailingLimitAmountType**   _optional_ |  | enum \(Absolute, Persentage\) |
| **TrailingStopAmount**   _optional_ |  | number \(double\) |
| **TrailingStopAmountType**   _optional_ |  | enum \(Absolute, Persentage\) |
| **Type**   _optional_ | Type. Assigned by client. | enum \(Market, Limit, Stop, StopLimit, Pegged, TrailingStop, TrailingStopLimit, OneCancelOther, OneTriggerOther, OneTriggerOneCancelOther, External\) |
| **ValidationsToBypass**   _optional_ | Flag property indicating validation rules to bypass | integer \(int32\) |

### CreateWatchlistModel

| Name | Schema |
| :--- | :--- |
| **Name**   _optional_ | string |
| **Securities**   _optional_ | &lt; integer \(int32\) &gt; array |

### EarningInfo

| Name | Schema |
| :--- | :--- |
| **Percent**   _optional_ | number \(double\) |
| **Value**   _optional_ | number \(double\) |

### EditableHotkeyModel

| Name | Schema |
| :--- | :--- |
| **ActionId**   _optional_ | integer \(int32\) |
| **Description**   _optional_ | string |
| **KeyboardShortcut**   _optional_ | string |
| **Parameters**   _optional_ | &lt; [HotkeyParameterMapModel](definitions.md#hotkeyparametermapmodel) &gt; array |

### EquityResource

| Name | Schema |
| :--- | :--- |
| **AddedDate**   _optional_ | string \(date-time\) |
| **AllowMargin**   _optional_ | boolean |
| **AllowShort**   _optional_ | boolean |
| **AllowTrade**   _optional_ | boolean |
| **Currency**   _optional_ | string |
| **Description**   _optional_ | string |
| **Enabled**   _optional_ | boolean |
| **Exchange**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **ModifyDate**   _optional_ | string \(date-time\) |
| **Precision**   _optional_ | integer \(int32\) |
| **Symbol**   _optional_ | string |
| **TickSize**   _optional_ | number \(double\) |
| **Type**   _optional_ | enum \(BankersAcceptance, CertificateOfDeposit, CollateralizeMortgageObligation, CorporateBond, CommercialPaper, CorporatePrivatePlacement, CommonStock, FederalHousingAuthority, FederalHomeLoan, FederalNationalMortgageAssociation, ForeignExchangeContract, Future, GovernmentNationalMortgageAssociation, TreasuriesPlusAgencyDebenture, MutualFund, MortgageInterestOnly, MortgagePrincipleOnly, MortgagePrivatePlacement, MiscellaneousPassThru, MunicipalBond, NoIsitcSecurityType, Option, PreferredStock, RepurchaseAgreement, ReverseRepurchaseAgreement, StudentLoanMarketingAssociation, TimeDeposit, UsTreasuryBill, Warrant, CatsTigersLions, WildcardEntry, ConvertibleBond, MortgageIoette, Index, FakeStockForNonStandartOption, Right, Cryptocurrency, ETF, DepositoryReceipt, CoveredWarrant, Unit\) |
| **VolumePrecision**   _optional_ | integer \(int32\) |

### Expecting

| Name | Schema |
| :--- | :--- |
| **Reason**   _optional_ | string |
| **State**   _optional_   _read-only_ | string |
| **Step**   _optional_ | string |
| **Token**   _optional_ | string |

### Failed

| Name | Schema |
| :--- | :--- |
| **Reason**   _optional_ | string |
| **State**   _optional_   _read-only_ | string |
| **Step**   _optional_ | string |

### FeeModel

| Name | Schema |
| :--- | :--- |
| **CommissionId**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **Leverage**   _optional_ | number \(double\) |
| **Seizure**   _optional_ | enum \(Placement, Execution, Fill, Proportional, Order\) |
| **Value**   _optional_ | number \(double\) |
| **ValueType**   _optional_ | enum \(Absolute, Coefficient\) |

### Formula

Formula model

| Name | Schema |
| :--- | :--- |
| **Expression**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |

### FrameParams

| Name | Schema |
| :--- | :--- |
| **Description**   _optional_ | string |
| **Name**   _optional_ | string |
| **TargetPercent**   _optional_ | number \(double\) |
| **Tolerance**   _optional_ | number \(double\) |

### HistoricalTradeDataExportDataModel

| Name | Schema |
| :--- | :--- |
| **DefaultFileName**   _optional_ | string |
| **Indicators**   _optional_ | &lt; [HistoricalTradeDataExportIndicatorModel](definitions.md#historicaltradedataexportindicatormodel) &gt; array |
| **Securities**   _optional_ | &lt; integer \(int32\) &gt; array |
| **TimeFrame**   _optional_ | [TimeFrameModel](definitions.md#timeframemodel) |

### HistoricalTradeDataExportIndicatorModel

| Name | Schema |
| :--- | :--- |
| **Args**   _optional_ | &lt; object &gt; array |
| **Name**   _optional_ | string |
| **Text**   _optional_ | string |
| **Type**   _optional_ | string |

### HotkeyMapModel

| Name | Schema |
| :--- | :--- |
| **ActionId**   _optional_ | integer \(int32\) |
| **ActionName**   _optional_ | string |
| **ActionResource**   _optional_ | [WebActionMapModel](definitions.md#webactionmapmodel) |
| **Description**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **KeyboardShortcut**   _optional_ | string |
| **Parameters**   _optional_ | &lt; [HotkeyParameterMapModel](definitions.md#hotkeyparametermapmodel) &gt; array |

### HotkeyParameterMapModel

| Name | Schema |
| :--- | :--- |
| **HotkeyId**   _optional_ | integer \(int32\) |
| **Id**   _optional_ | integer \(int32\) |
| **ParameterId**   _optional_ | integer \(int32\) |
| **ParameterName**   _optional_ | string |
| **ParameterType**   _optional_ | integer \(int32\) |
| **Value**   _optional_ | string |

### IFileUpload

| Name | Description | Schema |
| :--- | :--- | :--- |
| **Data**   _optional_ | **Pattern** : `"^(?:[A-Za-z0-9+/]{4})*(?:[A-Za-z0-9+/]{2}==\|[A-Za-z0-9+/]{3}=)?$"` | string \(byte\) |
| **Description**   _optional_ |  | string |
| **FileKey**   _optional_ |  | string |
| **FileName**   _optional_ |  | string |
| **Id**   _optional_ |  | integer \(int32\) |
| **Timestamp**   _optional_ |  | string \(date-time\) |
| **Type**   _optional_ |  | enum \(Other, ImageJpeg, ImageGif, ImagePng, ImageBitmap, ImageIco, TextHtml, TextPlain, VideoMpeg, VideoQuicktime\) |

### ISecurity

| Name | Schema |
| :--- | :--- |
| **AddedDate**   _optional_   _read-only_ | string \(date-time\) |
| **AllowMargin**   _optional_   _read-only_ | boolean |
| **AllowShort**   _optional_   _read-only_ | boolean |
| **AllowTrade**   _optional_   _read-only_ | boolean |
| **BaseCurrency**   _optional_   _read-only_ | string |
| **CmsSuffix**   _optional_   _read-only_ | string |
| **ContractSize**   _optional_   _read-only_ | number \(double\) |
| **CqsSuffix**   _optional_   _read-only_ | string |
| **Currency**   _optional_   _read-only_ | string |
| **Cusip**   _optional_   _read-only_ | string |
| **Description**   _optional_   _read-only_ | string |
| **Enabled**   _optional_   _read-only_ | boolean |
| **Exchange**   _optional_   _read-only_ | string |
| **ExpirationDate**   _optional_   _read-only_ | string \(date-time\) |
| **ExpirationName**   _optional_   _read-only_ | string |
| **ExpirationType**   _optional_   _read-only_ | enum \(Regular, Quarterly, Weekly, Flex, Undefined, Mini, NonStandard\) |
| **Id**   _optional_   _read-only_ | integer \(int32\) |
| **Industry**   _optional_   _read-only_ | string |
| **Isin**   _optional_   _read-only_ | string |
| **Leverage**   _optional_   _read-only_ | number \(double\) |
| **MarginRate**   _optional_   _read-only_ | number \(double\) |
| **ModifyDate**   _optional_   _read-only_ | string \(date-time\) |
| **Name**   _optional_   _read-only_ | string |
| **NasdaqSuffix**   _optional_   _read-only_ | string |
| **OptionType**   _optional_   _read-only_ | enum \(Call, Put, Undefined\) |
| **ParentId**   _optional_   _read-only_ | integer \(int32\) |
| **Precision**   _optional_   _read-only_ | integer \(int32\) |
| **Price**   _optional_   _read-only_ | number \(double\) |
| **QuoteSubscriptionKey**   _optional_   _read-only_ | string |
| **Sector**   _optional_   _read-only_ | string |
| **Sedol**   _optional_   _read-only_ | string |
| **SeriesId**   _optional_   _read-only_ | integer \(int32\) |
| **Source**   _optional_   _read-only_ | integer \(int32\) |
| **SourceId**   _optional_   _read-only_ | string |
| **StrikePrice**   _optional_   _read-only_ | number \(double\) |
| **Suffix**   _optional_   _read-only_ | string |
| **Symbol**   _optional_   _read-only_ | string |
| **TickSize**   _optional_   _read-only_ | number \(double\) |
| **Type**   _optional_   _read-only_ | enum \(BankersAcceptance, CertificateOfDeposit, CollateralizeMortgageObligation, CorporateBond, CommercialPaper, CorporatePrivatePlacement, CommonStock, FederalHousingAuthority, FederalHomeLoan, FederalNationalMortgageAssociation, ForeignExchangeContract, Future, GovernmentNationalMortgageAssociation, TreasuriesPlusAgencyDebenture, MutualFund, MortgageInterestOnly, MortgagePrincipleOnly, MortgagePrivatePlacement, MiscellaneousPassThru, MunicipalBond, NoIsitcSecurityType, Option, PreferredStock, RepurchaseAgreement, ReverseRepurchaseAgreement, StudentLoanMarketingAssociation, TimeDeposit, UsTreasuryBill, Warrant, CatsTigersLions, WildcardEntry, ConvertibleBond, MortgageIoette, Index, FakeStockForNonStandartOption, Right, Cryptocurrency, ETF, DepositoryReceipt, CoveredWarrant, Unit\) |
| **UnderlyingSecuritySymbol**   _optional_   _read-only_ | string |
| **Unit**   _optional_   _read-only_ | string |
| **VolumePrecision**   _optional_   _read-only_ | integer \(int32\) |

### IndicatorHistoryMapModel

| Name | Schema |
| :--- | :--- |
| **Date**   _optional_ | integer \(int32\) |
| **Values**   _optional_ | &lt; number \(double\) &gt; array |

### IndicatorHistoryRequestSettings

| Name | Schema |
| :--- | :--- |
| **CandlesCount**   _optional_ | integer \(int32\) |
| **EndDate**   _optional_ | integer \(int32\) |
| **IncludeNonMarketData**   _optional_ | boolean |
| **Interval**   _optional_ | integer \(int32\) |
| **Offset**   _optional_ | integer \(int32\) |
| **Period**   _optional_ | string |
| **Signature**   _optional_ | string |
| **StartDate**   _optional_ | integer \(int32\) |

### LevelInfoMapModel

| Name | Schema |
| :--- | :--- |
| **BottomPrice**   _optional_ | number \(double\) |
| **GreenCandles**   _optional_ | &lt; integer \(int32\) &gt; array |
| **RedCandles**   _optional_ | &lt; integer \(int32\) &gt; array |
| **TopPrice**   _optional_ | number \(double\) |

### ModifyOrderResource

Modify order parameters

| Name | Description | Schema |
| :--- | :--- | :--- |
| **ClientId**   _optional_ | Client order id. | string |
| **ExecutionInstructions**   _optional_ | Algo order execution instructions. | &lt; string, string &gt; map |
| **ExpireDate**   _optional_ | Expire date. Assigned by client. | string \(date-time\) |
| **Id**   _required_ | Internal order id.   **Minimum value** : `1`   **Maximum value** : `2147483647` | integer \(int32\) |
| **Legs**   _optional_ | Order legs | &lt; [ModifyOrderResource](definitions.md#modifyorderresource) &gt; array |
| **Price**   _optional_ | Price \(not used for some order types\). | number \(double\) |
| **Quantity**   _optional_ | Quantity. Assigned by client.   **Minimum value** : `0` | number \(double\) |
| **StopPrice**   _optional_ | Stop price \(used for stop orders\). | number \(double\) |
| **TrailingLimitAmount**   _optional_ |  | number \(double\) |
| **TrailingLimitAmountType**   _optional_ |  | enum \(Absolute, Persentage\) |
| **TrailingStopAmount**   _optional_ |  | number \(double\) |
| **TrailingStopAmountType**   _optional_ |  | enum \(Absolute, Persentage\) |
| **ValidationsToBypass**   _optional_ | Flag property indicating validation rules to bypass | integer \(int32\) |

### OptionExpirationResource

| Name | Schema |
| :--- | :--- |
| **ExpirationDate**   _optional_ | string \(date-time\) |
| **ExpirationType**   _optional_ | enum \(Regular, Quarterly, Weekly, Flex, Undefined, Mini, NonStandard\) |
| **SeriesId**   _optional_ | integer \(int32\) |
| **SeriesType**   _optional_ | enum \(Standard, NonStandard, Binary, Flex, Undefined\) |

### OptionResource

| Name | Schema |
| :--- | :--- |
| **AddedDate**   _optional_ | string \(date-time\) |
| **AllowMargin**   _optional_ | boolean |
| **AllowShort**   _optional_ | boolean |
| **AllowTrade**   _optional_ | boolean |
| **ContractSize**   _optional_ | number \(double\) |
| **Currency**   _optional_ | string |
| **Description**   _optional_ | string |
| **Enabled**   _optional_ | boolean |
| **Exchange**   _optional_ | string |
| **ExpirationDate**   _optional_ | string \(date-time\) |
| **ExpirationType**   _optional_ | enum \(Regular, Quarterly, Weekly, Flex, Undefined, Mini, NonStandard\) |
| **Id**   _optional_ | integer \(int32\) |
| **ModifyDate**   _optional_ | string \(date-time\) |
| **OptionType**   _optional_ | enum \(Call, Put, Undefined\) |
| **Precision**   _optional_ | integer \(int32\) |
| **SeriesId**   _optional_ | integer \(int32\) |
| **StrikePrice**   _optional_ | number \(double\) |
| **Symbol**   _optional_ | string |
| **TickSize**   _optional_ | number \(double\) |
| **Type**   _optional_ | enum \(BankersAcceptance, CertificateOfDeposit, CollateralizeMortgageObligation, CorporateBond, CommercialPaper, CorporatePrivatePlacement, CommonStock, FederalHousingAuthority, FederalHomeLoan, FederalNationalMortgageAssociation, ForeignExchangeContract, Future, GovernmentNationalMortgageAssociation, TreasuriesPlusAgencyDebenture, MutualFund, MortgageInterestOnly, MortgagePrincipleOnly, MortgagePrivatePlacement, MiscellaneousPassThru, MunicipalBond, NoIsitcSecurityType, Option, PreferredStock, RepurchaseAgreement, ReverseRepurchaseAgreement, StudentLoanMarketingAssociation, TimeDeposit, UsTreasuryBill, Warrant, CatsTigersLions, WildcardEntry, ConvertibleBond, MortgageIoette, Index, FakeStockForNonStandartOption, Right, Cryptocurrency, ETF, DepositoryReceipt, CoveredWarrant, Unit\) |
| **UnderlyingAssetSymbol**   _optional_ | string |
| **VolumePrecision**   _optional_ | integer \(int32\) |

### OrderResource

| Name | Description | Schema |
| :--- | :--- | :--- |
| **AccountId**   _optional_ | Account id. Assigned by OMS. | integer \(int32\) |
| **AveragePrice**   _optional_ | Average execution price. Assigned by executor. | number \(double\) |
| **ClientId**   _optional_ | Client order id \(ClOrdID\). Assigned by OMS. | string |
| **Comment**   _optional_ | Client side comments. Assigned by client. | string |
| **CounterPartyOrderId**   _optional_ | Executor order id. Assigned by executor. | string |
| **CreateDate**   _optional_ | Creation date. Assigned by OMS. | string \(date-time\) |
| **Date**   _optional_ | Last modification date. Assigned by OMS. | string \(date-time\) |
| **Description**   _optional_ | Used to indicate reject reason or broker comment. Assigned by executor. | string |
| **Exchange**   _optional_ | Desired exchange. Assigned by client. | string |
| **ExecBrocker**   _optional_ | Order route name. Assigned by executor. | string |
| **ExecId**   _optional_ | Execution id. | string |
| **ExecInst**   _optional_ | Execution instruction. Assigned by client. | enum \(DoNotIncrease, DoNotReduce, AllOrNone\) |
| **ExecutedQuantity**   _optional_ | Executed quantity. Assigned by executor. | number \(double\) |
| **ExecutionInstructions**   _optional_ | Algo order execution instructions. | &lt; string, string &gt; map |
| **ExecutionStatus**   _optional_ | Last modification status. Assigned by OMS or executor. | enum \(New, PartiallyFilled, Filled, DoneForDay, Canceled, Replaced, PendingCancel, Stopped, Rejected, Suspended, PendingNew, Calculated, Expired, AcceptedForBidding, PendingReplace, Error, Held\) |
| **ExecutionVenue**   _optional_ | Executor name, to which the order was routed. Assigned by OMS router. | string |
| **ExpireDate**   _optional_ | Expire date. Assigned by client. | string \(date-time\) |
| **ExtendedHours**   _optional_ | indicates the extended trading session for GTX order execution \(pre-market session, post-market session\) if empty - than there is no specific requirement for extended session | string |
| **Id**   _optional_ | Unique order id. Assigned by OMS. | integer \(int32\) |
| **InitialType**   _optional_ | Initial type. Assigned by OMS. | enum \(Market, Limit, Stop, StopLimit, Pegged, TrailingStop, TrailingStopLimit, OneCancelOther, OneTriggerOther, OneTriggerOneCancelOther, External\) |
| **IsExternal**   _optional_ | This property indicates that order was accepted from external system and fields like ClientOrderId should be persisted. It's a hack for orders from MessageAcceptor. Assigned be client. | boolean |
| **LastMarket**   _optional_ | Exchange where order was filled. Assigned by executor. | string |
| **LastPrice**   _optional_ | Last quote. Assigned by executor. | number \(double\) |
| **LastQuantity**   _optional_ | Last transaction executed quantity. Assigned by executor. | number \(double\) |
| **LeavesQuantity**   _optional_ | Unfilled quantity. Assigned by executor. | number \(double\) |
| **Legs**   _optional_ | Multileg order legs. Assigned by client. | &lt; [OrderResource](definitions.md#orderresource) &gt; array |
| **OrigClientId**   _optional_ | Client order id \(ClOrdID\). Assigned by OMS. | string |
| **ParentClientId**   _optional_ | Client order id \(ClOrdID\) of parent order in a case of mleg order. | string |
| **ParentId**   _optional_ | Parent order id. Assigned by OMS. | integer \(int32\) |
| **ParentRequestId**   _optional_ |  | integer \(int32\) |
| **Price**   _optional_ | Price \(not used for some order types\). Assigned by client. | number \(double\) |
| **Quantity**   _optional_ | Quantity. Assigned by client. | number \(double\) |
| **RequestId**   _optional_ | Request id. Assigned by OMS. | integer \(int32\) |
| **RequestStatus**   _optional_ | Indicate order processing status within OMS. Assigned by OMS. | enum \(RequireValidation, Validated, Rejected, Executing, Complete, Error\) |
| **SecurityId**   _optional_ | Security internal id; | integer \(int32\) |
| **SettDate**   _optional_ | date of settlement. Received from execution venue or calculated by OMS, assigned by OMS or executor. | string \(date-time\) |
| **SettlementDate**   _optional_ | Date of settlement deal | string \(date-time\) |
| **Side**   _optional_ | Side. Assigned by client. | enum \(Buy, Sell, SellShort, BuyToCover\) |
| **StateId**   _optional_ | State id. Assigned by OMS. | integer \(int32\) |
| **Status**   _optional_ | Current order status. Assigned by OMS or executor. | enum \(New, PartiallyFilled, Filled, DoneForDay, Canceled, Replaced, PendingCancel, Stopped, Rejected, Suspended, PendingNew, Calculated, Expired, AcceptedForBidding, PendingReplace, Error, Held\) |
| **StopPrice**   _optional_ | Stop price \(used for stop orders\). Assigned by client. | number \(double\) |
| **Symbol**   _optional_ |  | string |
| **Target**   _optional_ | Execution target. Assigned by OMS. | enum \(Ignore, New, Modify, Cancel, Execution, Status, CancelReject, Reject, Error, All\) |
| **TimeInForce**   _optional_ | Time in force. Assigned by client. | enum \(Day, GoodTillCancel, AtTheOpening, ImmediateOrCancel, FillOrKill, GoodTillCrossing, GoodTillDate, GoodTillTime\) |
| **Token**   _optional_ | Additional identity key \(usid in market scanner\). | string |
| **TrailingLimitAmount**   _optional_ | Assigned by client. | number \(double\) |
| **TrailingLimitAmountType**   _optional_ | Assigned by client. | enum \(Absolute, Persentage\) |
| **TrailingStopAmount**   _optional_ | Assigned by client. | number \(double\) |
| **TrailingStopAmountType**   _optional_ | Assigned by client. | enum \(Absolute, Persentage\) |
| **TransType**   _optional_ | Execution transaction type. | enum \(New, Cancel, Correct, Status\) |
| **TransactionDate**   _optional_ | Last transaction date. Assigned by OMS or executor. | string \(date-time\) |
| **Type**   _optional_ | Type. Assigned by client. | enum \(Market, Limit, Stop, StopLimit, Pegged, TrailingStop, TrailingStopLimit, OneCancelOther, OneTriggerOther, OneTriggerOneCancelOther, External\) |
| **UserId**   _optional_ | User id. Assigned by OMS. | integer \(int32\) |
| **ValidationsToBypass**   _optional_ | Flag property indicating validation rules to bypass | integer \(int32\) |

### PagingResult\[HotkeyMapModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [HotkeyMapModel](definitions.md#hotkeymapmodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[PositionResource\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [PositionResource](definitions.md#positionresource) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[PriceAlertInfoModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [PriceAlertInfoModel](definitions.md#pricealertinfomodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[RebalanceFrame\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [RebalanceFrame](definitions.md#rebalanceframe) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[SubmitFeedbackModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [SubmitFeedbackModel](definitions.md#submitfeedbackmodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[TransactionMapModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [TransactionMapModel](definitions.md#transactionmapmodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[WebActionMapModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [WebActionMapModel](definitions.md#webactionmapmodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PhoneNumberModel

| Name | Schema |
| :--- | :--- |
| **PhoneNumber**   _optional_ | string |
| **PhoneNumberState**   _optional_ | enum \(NotLinked, Active, Suspended, NotVerified\) |

### PositionResource

| Name | Schema |
| :--- | :--- |
| **AccountId**   _optional_ | integer \(int32\) |
| **AverageClosePrice**   _optional_ | number \(double\) |
| **AverageOpenPrice**   _optional_ | number \(double\) |
| **CompanyName**   _optional_ | string |
| **ContractSize**   _optional_ | number \(double\) |
| **CostBasis**   _optional_ | number \(double\) |
| **CreateDate**   _optional_ | string \(date-time\) |
| **DailyCloseProfitLoss**   _optional_ | number \(double\) |
| **DailyCostBasis**   _optional_ | number \(double\) |
| **DayQuantity**   _optional_ | number \(double\) |
| **ExcessChanges**   _optional_ | number \(double\) |
| **Id**   _optional_ | integer \(int32\) |
| **ModifyDate**   _optional_ | string \(date-time\) |
| **Name**   _optional_ | string |
| **Quantity**   _optional_ | number \(double\) |
| **RealizedProfitLoss**   _optional_ | number \(double\) |
| **SecurityCurrency**   _optional_ | string |
| **SecurityId**   _optional_ | integer \(int32\) |
| **SecurityType**   _optional_ | string |
| **StopLossPrice**   _optional_ | number \(double\) |
| **Symbol**   _optional_ | string |
| **TakeProfitPrice**   _optional_ | number \(double\) |

### PriceAlertEditableModel

Editable price alert

| Name | Description | Schema |
| :--- | :--- | :--- |
| **Argument**   _optional_ | Trigger value   **Minimum value** : `0` | number \(double\) |
| **ExpirationDate**   _optional_ | Expiration date | integer \(int64\) |
| **Field**   _required_ | Alert type | string |
| **Operator**   _required_ | Alert trigger operator | string |
| **SecurityId**   _optional_ | Alert trigger security id   **Minimum value** : `0`   **Maximum value** : `2147483647` | integer \(int32\) |
| **State**   _optional_ | Target alert state | enum \(New, Expired, Completed, Stopped\) |

### PriceAlertInfoModel

Price alert info

| Name | Description | Schema |
| :--- | :--- | :--- |
| **Argument**   _optional_ | Trigger value | number \(double\) |
| **CreatedDate**   _optional_ | Created Date | integer \(int64\) |
| **ExpirationDate**   _optional_ | Expiration date | integer \(int64\) |
| **Field**   _optional_ | Alert type | string |
| **Id**   _optional_ | Internal price alert identifier | integer \(int32\) |
| **Operator**   _optional_ | Alert trigger operator | string |
| **SecurityId**   _optional_ | Alert trigger security id | integer \(int32\) |
| **State**   _optional_ | Target alert state | enum \(New, Expired, Completed, Stopped\) |

### QuoteModel

| Name | Schema |
| :--- | :--- |
| **Ask**   _optional_ | number \(double\) |
| **Bid**   _optional_ | number \(double\) |
| **Last**   _optional_ | number \(double\) |
| **OpenInterest**   _optional_ | number \(double\) |
| **Volume**   _optional_ | number \(double\) |

### RebalanceFrame

| Name | Schema |
| :--- | :--- |
| **Descendants**   _optional_ | &lt; [RebalanceFrame](definitions.md#rebalanceframe) &gt; array |
| **Description**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **IsReferenced**   _optional_ | boolean |
| **Name**   _optional_ | string |
| **TargetPercent**   _optional_ | number \(double\) |
| **Tolerance**   _optional_ | number \(double\) |
| **UnitType**   _optional_   _read-only_ | enum \(Node, SecurityLeaf, Cash\) |

### RebalanceModel

| Name | Schema |
| :--- | :--- |
| **AbsoluteActualPercent**   _optional_ | number \(double\) |
| **AbsoluteTargetPercent**   _optional_ | number \(double\) |
| **AbsoluteTolerance**   _optional_ | number \(double\) |
| **ActualPercent**   _optional_ | number \(double\) |
| **Descendants**   _optional_ | &lt; [RebalanceModel](definitions.md#rebalancemodel) &gt; array |
| **Description**   _optional_ | string |
| **Gain**   _optional_ | number \(double\) |
| **GainPercent**   _optional_ | number \(double\) |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |
| **TargetPercent**   _optional_ | number \(double\) |
| **Tolerance**   _optional_ | number \(double\) |
| **UnitType**   _optional_   _read-only_ | enum \(Node, SecurityLeaf, Cash\) |
| **Value**   _optional_ | number \(double\) |

### RoboadvisorWhitelabelInfo

| Name | Schema |
| :--- | :--- |
| **Footer**   _optional_ | string |
| **Icon**   _optional_ | [IFileUpload](definitions.md#ifileupload) |
| **Logo**   _optional_ | [IFileUpload](definitions.md#ifileupload) |
| **Title**   _optional_ | string |

### SecurityContainerFrame

| Name | Schema |
| :--- | :--- |
| **Descendants**   _optional_   _read-only_ | &lt; [RebalanceFrame](definitions.md#rebalanceframe) &gt; array |
| **Description**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **IsReferenced**   _optional_ | boolean |
| **Name**   _optional_ | string |
| **Security**   _optional_ | [ISecurity](definitions.md#isecurity) |
| **SecurityId**   _optional_ | integer \(int32\) |
| **TargetPercent**   _optional_ | number \(double\) |
| **Tolerance**   _optional_ | number \(double\) |
| **UnitType**   _optional_   _read-only_ | enum \(Node, SecurityLeaf, Cash\) |

### SecurityFrameParams

| Name | Schema |
| :--- | :--- |
| **Description**   _optional_ | string |
| **Name**   _optional_ | string |
| **SecurityId**   _optional_ | integer \(int32\) |
| **TargetPercent**   _optional_ | number \(double\) |
| **Tolerance**   _optional_ | number \(double\) |

### SecurityHistoryRequestSettings

| Name | Schema |
| :--- | :--- |
| **CandlesCount**   _optional_ | integer \(int32\) |
| **EndDate**   _optional_ | integer \(int32\) |
| **IncludeNonMarketData**   _optional_ | boolean |
| **Interval**   _optional_ | integer \(int32\) |
| **Period**   _optional_ | string |
| **StartDate**   _optional_ | integer \(int32\) |

### SecurityModel

| Name | Schema |
| :--- | :--- |
| **AddedDate**   _optional_ | string \(date-time\) |
| **BaseCurrency**   _optional_ | string |
| **ContractSize**   _optional_ | number \(double\) |
| **Currency**   _optional_ | string |
| **Cusip**   _optional_ | string |
| **Description**   _optional_ | string |
| **Exchange**   _optional_ | string |
| **ExpirationDate**   _optional_ | string \(date-time\) |
| **ExpirationType**   _optional_ | enum \(Regular, Quarterly, Weekly, Flex, Undefined, Mini, NonStandard\) |
| **Id**   _optional_ | integer \(int32\) |
| **Industry**   _optional_ | string |
| **Isin**   _optional_ | string |
| **MarginRate**   _optional_ | number \(double\) |
| **ModifyDate**   _optional_ | string \(date-time\) |
| **OptionType**   _optional_ | enum \(Call, Put, Undefined\) |
| **ParentId**   _optional_ | integer \(int32\) |
| **Precision**   _optional_ | integer \(int32\) |
| **Sector**   _optional_ | string |
| **Sedol**   _optional_ | string |
| **SeriesId**   _optional_ | integer \(int32\) |
| **Source**   _optional_ | integer \(int32\) |
| **StrikePrice**   _optional_ | number \(double\) |
| **Suffix**   _optional_ | string |
| **Symbol**   _optional_ | string |
| **TickSize**   _optional_ | number \(double\) |
| **Type**   _optional_ | enum \(BankersAcceptance, CertificateOfDeposit, CollateralizeMortgageObligation, CorporateBond, CommercialPaper, CorporatePrivatePlacement, CommonStock, FederalHousingAuthority, FederalHomeLoan, FederalNationalMortgageAssociation, ForeignExchangeContract, Future, GovernmentNationalMortgageAssociation, TreasuriesPlusAgencyDebenture, MutualFund, MortgageInterestOnly, MortgagePrincipleOnly, MortgagePrivatePlacement, MiscellaneousPassThru, MunicipalBond, NoIsitcSecurityType, Option, PreferredStock, RepurchaseAgreement, ReverseRepurchaseAgreement, StudentLoanMarketingAssociation, TimeDeposit, UsTreasuryBill, Warrant, CatsTigersLions, WildcardEntry, ConvertibleBond, MortgageIoette, Index, FakeStockForNonStandartOption, Right, Cryptocurrency, ETF, DepositoryReceipt, CoveredWarrant, Unit\) |
| **UnderlyingSecuritySymbol**   _optional_ | string |
| **Unit**   _optional_ | string |
| **VolumePrecision**   _optional_ | integer \(int32\) |

### SecuritySignature

| Name | Schema |
| :--- | :--- |
| **Currency**   _optional_ | string |
| **Exchange**   _optional_ | string |
| **Symbol**   _optional_ | string |

### SubmitFeedbackModel

| Name | Schema |
| :--- | :--- |
| **BuildVersion**   _optional_ | string |
| **Comment**   _optional_ | string |
| **Contacts**   _optional_ | string |
| **ImagesToUpload**   _optional_ | &lt; [Base64FileMapModel](definitions.md#base64filemapmodel) &gt; array |
| **Subject**   _optional_ | string |

### SubscriptionModel

Web API notification service subscription representation

| Name | Description | Schema |
| :--- | :--- | :--- |
| **Channel**   _optional_ | Channel for subscription messages delivery | enum \(Email, MobileText, MobilePush, WebPopupAlert, Disabled\) |
| **State**   _optional_ | Subscription state | enum \(NotLinked, Active, Suspended, NotVerified\) |
| **SubscriptionType**   _optional_ | Subscription notification type | enum \(OrderExecution, OrderForReview, OrderOnReview, OrderPlacement, OrderReplacement, PriceAlert\) |

### Succeed

| Name | Schema |
| :--- | :--- |
| **State**   _optional_   _read-only_ | string |
| **Token**   _optional_ | string |

### SupportResistanceMapModel

| Name | Schema |
| :--- | :--- |
| **Levels**   _optional_ | &lt; [LevelInfoMapModel](definitions.md#levelinfomapmodel) &gt; array |
| **ResistancePrice**   _optional_ | number \(double\) |
| **SupportPrice**   _optional_ | number \(double\) |

### TimeFrameModel

| Name | Schema |
| :--- | :--- |
| **CandlesCount**   _optional_ | integer \(int32\) |
| **EndDate**   _optional_ | integer \(int32\) |
| **IncludeNonMarketData**   _optional_ | boolean |
| **Period**   _optional_ | string |
| **StartDate**   _optional_ | integer \(int32\) |

### TimeSeriesValueCandleMapModel

| Name | Schema |
| :--- | :--- |
| **Close**   _optional_ | number \(double\) |
| **DateTime**   _optional_   _read-only_ | string \(date-time\) |
| **High**   _optional_ | number \(double\) |
| **IsMarket**   _optional_ | boolean |
| **Low**   _optional_ | number \(double\) |
| **Open**   _optional_ | number \(double\) |
| **OpenInterest**   _optional_ | integer \(int32\) |
| **Time**   _optional_ | integer \(int32\) |
| **ValuationLevels**   _optional_ | &lt; number \(double\) &gt; array |
| **Volume**   _optional_ | number \(double\) |

### TimeZoneInfoItem

| Name | Schema |
| :--- | :--- |
| **description**   _optional_ | string |
| **ianaId**   _optional_ | string |
| **name**   _optional_ | string |

### TransactionMapModel

| Name | Schema |
| :--- | :--- |
| **AccountId**   _optional_ | integer \(int32\) |
| **Date**   _optional_ | string \(date-time\) |
| **Description**   _optional_ | string |
| **Fee**   _optional_ | [FeeModel](definitions.md#feemodel) |
| **Id**   _optional_ | integer \(int32\) |
| **IsDayTrade**   _optional_ | boolean |
| **LeavesQuantity**   _optional_ | number \(double\) |
| **OrderStateId**   _optional_ | integer \(int32\) |
| **Quantity**   _optional_ | number \(double\) |
| **SecurityId**   _optional_ | integer \(int32\) |
| **Type**   _optional_ | enum \(Undefined, Commission, OrderExecution, OptionExpiration, Payment, ManualManipulation, Clearing, Rpl\) |
| **Value**   _optional_ | number \(double\) |

### Tuple\[Int32,String\]

| Name | Schema |
| :--- | :--- |
| **m\_Item1**   _optional_ | integer \(int32\) |
| **m\_Item2**   _optional_ | string |

### Tuple\[PhoneNumberModel,Int32\]

| Name | Schema |
| :--- | :--- |
| **m\_Item1**   _optional_ | [PhoneNumberModel](definitions.md#phonenumbermodel) |
| **m\_Item2**   _optional_ | integer \(int32\) |

### UserAccountModel

| Name | Schema |
| :--- | :--- |
| **AccessType**   _optional_ | enum \(Full, ReadOnly, ClosePositionsOnly\) |
| **Alias**   _optional_ | string |
| **ClearingAccount**   _optional_ | string |
| **Enabled**   _optional_ | boolean |
| **Id**   _optional_ | integer \(int32\) |
| **MarginType**   _optional_ | enum \(Empty, Cash, Margin, DayTrader, MarginIra\) |

### UserInfoModel

| Name | Schema |
| :--- | :--- |
| **AddedDate**   _optional_ | string \(date-time\) |
| **Email**   _optional_ | string |
| **FirstName**   _optional_ | string |
| **LastName**   _optional_ | string |
| **Login**   _optional_ | string |
| **MiddleName**   _optional_ | string |
| **Salutation**   _optional_ | enum \(NoSalutation, Mr, Mrs, Ms, Dr, Sir, Madam\) |
| **Suffix**   _optional_ | enum \(NoSuffix, Jr, Sr, Second, Third, Fourth\) |
| **UserId**   _optional_ | integer \(int32\) |

### VerifyOrderModel

| Name | Description | Schema |
| :--- | :--- | :--- |
| **Commission**   _optional_ | The commission of the order. | number \(double\) |
| **Commissions**   _optional_ | The commission of the order. | &lt; string, number \(double\) &gt; map |
| **Cost**   _optional_ | The cost of the order. | number \(double\) |
| **ErrorDescription**   _optional_ | Error description. | string |
| **ErrorDescriptionArgs**   _optional_ | Error description arguments. | &lt; string &gt; array |
| **IsSuccessful**   _optional_ | Result. | boolean |
| **MarginChange**   _optional_ | Expected margin value changed. | number \(double\) |
| **NetCost**   _optional_ | The net cost of the order. | number \(double\) |
| **Quotes**   _optional_ | Order validation quotes. | &lt; [QuoteModel](definitions.md#quotemodel) &gt; array |

### WatchlistModel

| Name | Schema |
| :--- | :--- |
| **CreateDate**   _optional_ | string \(date-time\) |
| **Description**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **ModifyDate**   _optional_ | string \(date-time\) |
| **Name**   _optional_ | string |
| **ReadOnly**   _optional_ | boolean |
| **SecurityList**   _optional_ | &lt; [SecurityModel](definitions.md#securitymodel) &gt; array |
| **Source**   _optional_ | string |
| **Type**   _optional_ | enum \(UserList, SystemList, Snapshot\) |

### WebActionMapModel

| Name | Schema |
| :--- | :--- |
| **Action**   _optional_ | string |
| **Description**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |
| **Parameters**   _optional_ | &lt; [WebActionParameterMapModel](definitions.md#webactionparametermapmodel) &gt; array |

### WebActionParameterMapModel

| Name | Schema |
| :--- | :--- |
| **ActionId**   _optional_ | integer \(int32\) |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |
| **Type**   _optional_ | integer \(int32\) |

