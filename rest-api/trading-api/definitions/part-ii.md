# Part II

## Definitions

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

### PagingResult\[HotkeyMapModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [HotkeyMapModel](./#hotkeymapmodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[PositionResource\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [PositionResource](./#positionresource) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[PriceAlertInfoModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [PriceAlertInfoModel](./#pricealertinfomodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[RebalanceFrame\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [RebalanceFrame](./#rebalanceframe) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[SubmitFeedbackModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [SubmitFeedbackModel](./#submitfeedbackmodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[TransactionMapModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [TransactionMapModel](./#transactionmapmodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[WebActionMapModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [WebActionMapModel](./#webactionmapmodel) &gt; array |
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
| **Descendants**   _optional_ | &lt; [RebalanceFrame](./#rebalanceframe) &gt; array |
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
| **Descendants**   _optional_ | &lt; [RebalanceModel](./#rebalancemodel) &gt; array |
| **Description**   _optional_ | string |
| **Gain**   _optional_ | number \(double\) |
| **GainPercent**   _optional_ | number \(double\) |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |
| **TargetPercent**   _optional_ | number \(double\) |
| **Tolerance**   _optional_ | number \(double\) |
| **UnitType**   _optional_   _read-only_ | enum \(Node, SecurityLeaf, Cash\) |
| **Value**   _optional_ | number \(double\) |

