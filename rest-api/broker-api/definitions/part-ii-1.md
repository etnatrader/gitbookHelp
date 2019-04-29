# Part II

## Definitions

### FeeModel

| Name | Schema |
| :--- | :--- |
| **CommissionId**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **Leverage**   _optional_ | number \(double\) |
| **Seizure**   _optional_ | enum \(Placement, Execution, Fill, Proportional, Order\) |
| **Value**   _optional_ | number \(double\) |
| **ValueType**   _optional_ | enum \(Absolute, Coefficient\) |

### FeedbackModel

| Name | Schema |
| :--- | :--- |
| **BuildVersion**   _optional_ | string |
| **Comment**   _optional_ | string |
| **Contacts**   _optional_ | string |
| **Files**   _optional_ | &lt; [IAttachItem](./#iattachitem) &gt; array |
| **Id**   _optional_ | integer \(int32\) |
| **Login**   _optional_ | string |
| **Subject**   _optional_ | string |
| **SupportTicket**   _optional_ | string |
| **Timestamp**   _optional_ | integer \(int32\) |
| **UserAgent**   _optional_ | string |

### Formula

Formula model

| Name | Schema |
| :--- | :--- |
| **Expression**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |

### HistoricalTradeDataExportDataModel

| Name | Schema |
| :--- | :--- |
| **DefaultFileName**   _optional_ | string |
| **Indicators**   _optional_ | &lt; [HistoricalTradeDataExportIndicatorModel](./#historicaltradedataexportindicatormodel) &gt; array |
| **Securities**   _optional_ | &lt; integer \(int32\) &gt; array |
| **TimeFrame**   _optional_ | [TimeFrameModel](./#timeframemodel) |

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
| **ActionResource**   _optional_ | [WebActionMapModel](./#webactionmapmodel) |
| **Description**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **KeyboardShortcut**   _optional_ | string |
| **Parameters**   _optional_ | &lt; [HotkeyParameterMapModel](./#hotkeyparametermapmodel) &gt; array |

### HotkeyParameterMapModel

| Name | Schema |
| :--- | :--- |
| **HotkeyId**   _optional_ | integer \(int32\) |
| **Id**   _optional_ | integer \(int32\) |
| **ParameterId**   _optional_ | integer \(int32\) |
| **ParameterName**   _optional_ | string |
| **ParameterType**   _optional_ | integer \(int32\) |
| **Value**   _optional_ | string |

### IAttachItem

| Name | Schema |
| :--- | :--- |
| **FileName**   _optional_ | string |
| **IsImage**   _optional_ | boolean |
| **Type**   _optional_ | string |
| **Url**   _optional_ | string |

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

### InternalPositionModel

| Name | Schema |
| :--- | :--- |
| **AccountId**   _optional_ | integer \(int32\) |
| **AverageClosePrice**   _optional_ | number \(double\) |
| **AverageOpenPrice**   _optional_ | number \(double\) |
| **CostBasis**   _optional_ | number \(double\) |
| **CreateDate**   _optional_ | string \(date-time\) |
| **DailyCloseProfitLoss**   _optional_ | number \(double\) |
| **DailyCostBasis**   _optional_ | number \(double\) |
| **DayQuantity**   _optional_ | number \(double\) |
| **ExcessChanges**   _optional_ | number \(double\) |
| **Id**   _optional_ | integer \(int32\) |
| **LastLot**   _optional_ | number \(double\) |
| **Locked**   _optional_ | boolean |
| **MarginType**   _optional_ | enum \(Empty, Cash, Margin, Short\) |
| **ModifyDate**   _optional_ | string \(date-time\) |
| **OpenQuantity**   _optional_ | number \(double\) |
| **Quantity**   _optional_ | number \(double\) |
| **RealizedProfitLoss**   _optional_ | number \(double\) |
| **SecurityId**   _optional_ | integer \(int32\) |
| **SpreadQuantity**   _optional_ | number \(double\) |
| **StopLossPrice**   _optional_ | number \(double\) |
| **TakeProfitPrice**   _optional_ | number \(double\) |
| **Unsettled**   _optional_ | number \(double\) |
| **UnsettledDate**   _optional_ | string \(date-time\) |

### InternalSecurityResource

| Name | Schema |
| :--- | :--- |
| **AddedDate**   _optional_ | string \(date-time\) |
| **AllowMargin**   _optional_ | boolean |
| **AllowShort**   _optional_ | boolean |
| **AllowTrade**   _optional_ | boolean |
| **BaseCurrency**   _optional_ | string |
| **ContractSize**   _optional_ | number \(double\) |
| **Currency**   _optional_ | string |
| **Cusip**   _optional_ | string |
| **Description**   _optional_ | string |
| **Enabled**   _optional_ | boolean |
| **Exchange**   _optional_ | string |
| **ExpirationDate**   _optional_ | string \(date-time\) |
| **ExpirationName**   _optional_ | string |
| **ExpirationType**   _optional_ | enum \(Regular, Quarterly, Weekly, Flex, Undefined, Mini, NonStandard\) |
| **Id**   _optional_ | integer \(int32\) |
| **Industry**   _optional_ | string |
| **Isin**   _optional_ | string |
| **Leverage**   _optional_ | number \(double\) |
| **MarginRate**   _optional_ | number \(double\) |
| **ModifyDate**   _optional_ | string \(date-time\) |
| **Name**   _optional_ | string |
| **OptionType**   _optional_ | enum \(Call, Put, Undefined\) |
| **ParentId**   _optional_ | integer \(int32\) |
| **Precision**   _optional_ | integer \(int32\) |
| **Price**   _optional_ | number \(double\) |
| **QuoteSubscriptionKey**   _optional_ | string |
| **Sector**   _optional_ | string |
| **Sedol**   _optional_ | string |
| **SeriesId**   _optional_ | integer \(int32\) |
| **Source**   _optional_ | integer \(int32\) |
| **SourceId**   _optional_ | string |
| **StrikePrice**   _optional_ | number \(double\) |
| **Suffix**   _optional_ | string |
| **Symbol**   _optional_ | string |
| **TickSize**   _optional_ | number \(double\) |
| **Type**   _optional_ | enum \(BankersAcceptance, CertificateOfDeposit, CollateralizeMortgageObligation, CorporateBond, CommercialPaper, CorporatePrivatePlacement, CommonStock, FederalHousingAuthority, FederalHomeLoan, FederalNationalMortgageAssociation, ForeignExchangeContract, Future, GovernmentNationalMortgageAssociation, TreasuriesPlusAgencyDebenture, MutualFund, MortgageInterestOnly, MortgagePrincipleOnly, MortgagePrivatePlacement, MiscellaneousPassThru, MunicipalBond, NoIsitcSecurityType, Option, PreferredStock, RepurchaseAgreement, ReverseRepurchaseAgreement, StudentLoanMarketingAssociation, TimeDeposit, UsTreasuryBill, Warrant, CatsTigersLions, WildcardEntry, ConvertibleBond, MortgageIoette, Index, FakeStockForNonStandartOption, Right, Cryptocurrency, ETF, DepositoryReceipt, CoveredWarrant, Unit\) |
| **UnderlyingSecuritySymbol**   _optional_ | string |
| **Unit**   _optional_ | string |
| **VolumePrecision**   _optional_ | integer \(int32\) |

### InternalUpdatePosition

| Name | Schema |
| :--- | :--- |
| **AccountId**   _optional_ | integer \(int32\) |
| **AverageClosePrice**   _optional_ | number \(double\) |
| **AverageOpenPrice**   _optional_ | number \(double\) |
| **CostBasis**   _optional_ | number \(double\) |
| **CreateDate**   _optional_ | string \(date-time\) |
| **DailyCloseProfitLoss**   _optional_ | number \(double\) |
| **DailyCostBasis**   _optional_ | number \(double\) |
| **DayQuantity**   _optional_ | number \(double\) |
| **ExcessChanges**   _optional_ | number \(double\) |
| **LastLot**   _optional_ | number \(double\) |
| **Locked**   _optional_ | boolean |
| **MarginType**   _optional_ | enum \(Empty, Cash, Margin, Short\) |
| **ModifyDate**   _optional_ | string \(date-time\) |
| **OpenQuantity**   _optional_ | number \(double\) |
| **Quantity**   _optional_ | number \(double\) |
| **RealizedProfitLoss**   _optional_ | number \(double\) |
| **SecurityId**   _optional_ | integer \(int32\) |
| **SpreadQuantity**   _optional_ | number \(double\) |
| **StopLossPrice**   _optional_ | number \(double\) |
| **TakeProfitPrice**   _optional_ | number \(double\) |
| **Unsettled**   _optional_ | number \(double\) |
| **UnsettledDate**   _optional_ | string \(date-time\) |

### LevelInfoMapModel

| Name | Schema |
| :--- | :--- |
| **BottomPrice**   _optional_ | number \(double\) |
| **GreenCandles**   _optional_ | &lt; integer \(int32\) &gt; array |
| **RedCandles**   _optional_ | &lt; integer \(int32\) &gt; array |
| **TopPrice**   _optional_ | number \(double\) |

### LocalizationResourceMapModel

| Name | Schema |
| :--- | :--- |
| **Culture**   _optional_ | string |
| **Key**   _optional_ | string |
| **Set**   _optional_ | string |
| **Value**   _optional_ | string |

### ModifyOrderResource

Modify order parameters

| Name | Description | Schema |
| :--- | :--- | :--- |
| **ClientId**   _optional_ | Client order id. | string |
| **ExecutionInstructions**   _optional_ | Algo order execution instructions. | &lt; string, string &gt; map |
| **ExpireDate**   _optional_ | Expire date. Assigned by client. | string \(date-time\) |
| **Id**   _required_ | Internal order id.   **Minimum value** : `1`   **Maximum value** : `2147483647` | integer \(int32\) |
| **Legs**   _optional_ | Order legs | &lt; [ModifyOrderResource](./#modifyorderresource) &gt; array |
| **Price**   _optional_ | Price \(not used for some order types\). | number \(double\) |
| **Quantity**   _optional_ | Quantity. Assigned by client.   **Minimum value** : `0` | number \(double\) |
| **StopPrice**   _optional_ | Stop price \(used for stop orders\). | number \(double\) |
| **TrailingLimitAmount**   _optional_ |  | number \(double\) |
| **TrailingLimitAmountType**   _optional_ |  | enum \(Absolute, Persentage\) |
| **TrailingStopAmount**   _optional_ |  | number \(double\) |
| **TrailingStopAmountType**   _optional_ |  | enum \(Absolute, Persentage\) |
| **ValidationsToBypass**   _optional_ | Flag property indicating validation rules to bypass | integer \(int32\) |

### ModifyUserModel

| Name | Schema |
| :--- | :--- |
| **EmailAddress**   _optional_ | string |
| **Enabled**   _optional_ | boolean |
| **EntitlementsPhoneNumber**   _optional_ | string |
| **ExpirationDate**   _optional_ | string \(date-time\) |
| **FirstName**   _optional_ | string |
| **LastName**   _optional_ | string |
| **Middle**   _optional_ | string |
| **PhoneNumber**   _optional_ | string |
| **Salutation**   _optional_ | enum \(NoSalutation, Mr, Mrs, Ms, Dr, Sir, Madam\) |
| **Suffix**   _optional_ | enum \(NoSuffix, Jr, Sr, Second, Third, Fourth\) |
| **TimeZoneInfoId**   _optional_ | string |

### MultilegAllocationRequest

| Name | Schema |
| :--- | :--- |
| **AccountType**   _optional_ | enum \(Cash, Margin\) |
| **Comment**   _optional_ | string |
| **Commission**   _optional_ | number \(double\) |
| **FromAccount**   _optional_ | string |
| **Instructions**   _optional_ | &lt; string, string &gt; map |
| **Legs**   _optional_ | &lt; [AllocationLegInfo](./#allocationleginfo) &gt; array |
| **ToAccount**   _optional_ | string |

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
| **Legs**   _optional_ | Multileg order legs. Assigned by client. | &lt; [OrderResource](./#orderresource) &gt; array |
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

