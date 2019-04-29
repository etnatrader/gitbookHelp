# Part I

## Definitions

### AccountEditableModel

| Name | Description | Schema |
| :--- | :--- | :--- |
| **BaseCash**   _optional_ |  | number \(double\) |
| **Cash**   _optional_ |  | number \(double\) |
| **CashInterestRate**   _optional_ | **Minimum value** : `0` | number \(double\) |
| **Cip**   _optional_ |  | number \(double\) |
| **ClearingAccount**   _required_ |  | string |
| **ClearingFirm**   _optional_ |  | string |
| **CloseEquity**   _optional_ |  | number \(double\) |
| **CommissionPlan**   _optional_ |  | string |
| **CreatedDate**   _optional_ |  | string \(date-time\) |
| **Currency**   _required_ |  | string |
| **DayTradeCall**   _optional_ |  | number \(double\) |
| **DayTrades**   _optional_ | **Minimum value** : `0`   **Maximum value** : `2147483647` | integer \(int32\) |
| **DayTradingBuyingPower**   _optional_ |  | number \(double\) |
| **Enabled**   _optional_ |  | boolean |
| **EquityCall**   _optional_ |  | number \(double\) |
| **ExcessEquity**   _optional_ |  | number \(double\) |
| **HouseCall**   _optional_ |  | number \(double\) |
| **InitialCall**   _optional_ |  | number \(double\) |
| **IsAverageAccount**   _optional_ |  | boolean |
| **IsChanged**   _optional_ |  | boolean |
| **MaintenanceCall**   _optional_ |  | number \(double\) |
| **MarginEquity**   _optional_ |  | number \(double\) |
| **MarginInterestRate**   _optional_ | **Minimum value** : `0` | number \(double\) |
| **MarginType**   _optional_ |  | enum \(Empty, Cash, Margin, DayTrader, MarginIra\) |
| **ModifiedDate**   _optional_ |  | string \(date-time\) |
| **MoneyMarket**   _optional_ |  | number \(double\) |
| **OpenExcess**   _optional_ |  | number \(double\) |
| **OptionLevel**   _optional_ | **Minimum value** : `0`   **Maximum value** : `2147483647` | integer \(int32\) |
| **OwnerType**   _optional_ |  | enum \(IndividualCustomer, InstitutionalCustomer, Combined, EmployeeAccount, MarketMaking, OtherProprietary, Unknown, ErrorAccount\) |
| **Permissions**   _optional_ |  | enum \(Empty, LongStock, ShortStock, LongOption, ShortOption, AllowTrade, AllowMargin, AllowOpen\) |
| **RepCode**   _optional_ |  | string |
| **SmaBalance**   _optional_ |  | number \(double\) |
| **Status**   _optional_ |  | enum \(UnSpecified, New, SentToClearing, Approved, Rejected\) |
| **SubscriptionPlanId**   _optional_ | **Minimum value** : `1`   **Maximum value** : `2147483647` | integer \(int32\) |
| **Sweep**   _optional_ |  | number \(double\) |
| **TradeDayBalance**   _optional_ |  | number \(double\) |

### AccountModel

| Name | Schema |
| :--- | :--- |
| **BaseCash**   _optional_ | number \(double\) |
| **Cash**   _optional_ | number \(double\) |
| **CashInterestRate**   _optional_ | number \(double\) |
| **Cip**   _optional_ | number \(double\) |
| **ClearingAccount**   _optional_ | string |
| **ClearingFirm**   _optional_ | string |
| **CloseEquity**   _optional_ | number \(double\) |
| **CommissionPlan**   _optional_ | string |
| **CreatedDate**   _optional_ | string \(date-time\) |
| **Currency**   _optional_ | string |
| **DayTradeCall**   _optional_ | number \(double\) |
| **DayTrades**   _optional_ | integer \(int32\) |
| **DayTradingBuyingPower**   _optional_ | number \(double\) |
| **Enabled**   _optional_ | boolean |
| **EquityCall**   _optional_ | number \(double\) |
| **ExcessEquity**   _optional_ | number \(double\) |
| **HouseCall**   _optional_ | number \(double\) |
| **Id**   _optional_ | integer \(int32\) |
| **InitialCall**   _optional_ | number \(double\) |
| **IsAverageAccount**   _optional_ | boolean |
| **IsChanged**   _optional_ | boolean |
| **MaintenanceCall**   _optional_ | number \(double\) |
| **MarginEquity**   _optional_ | number \(double\) |
| **MarginInterestRate**   _optional_ | number \(double\) |
| **MarginType**   _optional_ | enum \(Empty, Cash, Margin, DayTrader, MarginIra\) |
| **ModifiedDate**   _optional_ | string \(date-time\) |
| **MoneyMarket**   _optional_ | number \(double\) |
| **OpenExcess**   _optional_ | number \(double\) |
| **OptionLevel**   _optional_ | integer \(int32\) |
| **OwnerType**   _optional_ | enum \(IndividualCustomer, InstitutionalCustomer, Combined, EmployeeAccount, MarketMaking, OtherProprietary, Unknown, ErrorAccount\) |
| **Permissions**   _optional_ | enum \(Empty, LongStock, ShortStock, LongOption, ShortOption, AllowTrade, AllowMargin, AllowOpen\) |
| **RepCode**   _optional_ | string |
| **SmaBalance**   _optional_ | number \(double\) |
| **Status**   _optional_ | enum \(UnSpecified, New, SentToClearing, Approved, Rejected\) |
| **SubscriptionPlanId**   _optional_ | integer \(int32\) |
| **Sweep**   _optional_ | number \(double\) |
| **TradeDayBalance**   _optional_ | number \(double\) |

### AccountValueItem

| Name | Schema |
| :--- | :--- |
| **Date**   _optional_ | string \(date-time\) |
| **Value**   _optional_ | number \(double\) |

### AllocationLegInfo

| Name | Schema |
| :--- | :--- |
| **Action**   _optional_ | enum \(Buy, Sell, SellShort, BuyToCover, SellToClose, BuyToClose, SellToOpen, BuyToOpen\) |
| **Price**   _optional_ | number \(double\) |
| **Quantity**   _optional_ | number \(double\) |
| **Symbol**   _optional_ | string |

### AllocationResultInfo\[MultilegAllocationRequest\]

Allocation request result

| Name | Description | Schema |
| :--- | :--- | :--- |
| **Description**   _optional_ | Error description | string |
| **IsSucceed**   _optional_ | Is allocation request was successfully processed | boolean |
| **Request**   _optional_ |  | [MultilegAllocationRequest](./#multilegallocationrequest) |

### AllocationResultInfo\[SimpleAllocationRequest\]

Allocation request result

| Name | Description | Schema |
| :--- | :--- | :--- |
| **Description**   _optional_ | Error description | string |
| **IsSucceed**   _optional_ | Is allocation request was successfully processed | boolean |
| **Request**   _optional_ |  | [SimpleAllocationRequest](./#simpleallocationrequest) |

### AppKey

| Name | Schema |
| :--- | :--- |
| **CompanyId**   _optional_   _read-only_ | integer \(int32\) |
| **Description**   _optional_   _read-only_ | string |
| **Enabled**   _optional_   _read-only_ | boolean |
| **Id**   _optional_   _read-only_ | integer \(int32\) |
| **Key**   _optional_   _read-only_ | string |
| **Type**   _optional_   _read-only_ | enum \(FrontOffice, Mobile, Custom\) |

### ChartCompareRequestModel

| Name | Schema |
| :--- | :--- |
| **Securities**   _optional_ | &lt; [SecuritySignature](./#securitysignature) &gt; array |
| **SecuritiesHistorySettings**   _optional_ | [SecurityHistoryRequestSettings](./#securityhistoryrequestsettings) |

### ChartHistoryModel

| Name | Schema |
| :--- | :--- |
| **IndicatorsHistory**   _optional_ | &lt; &lt; [IndicatorHistoryMapModel](./#indicatorhistorymapmodel) &gt; array &gt; array |
| **SecurityHistory**   _optional_ | &lt; &lt; [TimeSeriesValueCandleMapModel](./#timeseriesvaluecandlemapmodel) &gt; array &gt; array |
| **SupportResistanceHistory**   _optional_ | [SupportResistanceMapModel](./#supportresistancemapmodel) |

### ChartHistoryRequestModel

| Name | Schema |
| :--- | :--- |
| **IndicatorsHistorySettings**   _optional_ | &lt; [IndicatorHistoryRequestSettings](./#indicatorhistoryrequestsettings) &gt; array |
| **Security**   _optional_ | [SecuritySignature](./#securitysignature) |
| **SecurityHistorySettings**   _optional_ | [SecurityHistoryRequestSettings](./#securityhistoryrequestsettings) |

### ClearingAction

System action

| Name | Description | Schema |
| :--- | :--- | :--- |
| **Disabled**   _optional_ | Is action disabled | boolean |
| **Handlers**   _optional_ | List of actions handlers | &lt; [ClearingActionHandler](./#clearingactionhandler) &gt; array |
| **Name**   _optional_ | System action name | string |

### ClearingActionHandler

System action handler

| Name | Description | Schema |
| :--- | :--- | :--- |
| **Name**   _optional_ | Action handler name | string |
| **Parameters**   _optional_ | Set of handler parameters | &lt; string, string &gt; map |

### CreateAppKey

| Name | Schema |
| :--- | :--- |
| **Description**   _optional_ | string |
| **KeyType**   _optional_ | enum \(FrontOffice, Mobile, Custom\) |

### CreateOrderResource

| Name | Description | Schema |
| :--- | :--- | :--- |
| **ClientId**   _optional_ | Client order id. | string |
| **Exchange**   _optional_ | Desired exchange. | string |
| **ExecInst**   _optional_ | Execution instruction. | enum \(DoNotIncrease, DoNotReduce, AllOrNone\) |
| **ExecutionInstructions**   _optional_ | Algo order execution instructions. | &lt; string, string &gt; map |
| **ExpireDate**   _optional_ | Expire date. Assigned by client. | string \(date-time\) |
| **ExtendedHours**   _optional_ | indicates the extended trading session for GTX order execution \(pre-market session, post-market session\) if empty - than there is no specific requirement for extended session | string |
| **Legs**   _optional_ | Order legs | &lt; [CreateOrderResource](./#createorderresource) &gt; array |
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

### CreateUserModel

| Name | Schema |
| :--- | :--- |
| **EmailAddress**   _optional_ | string |
| **Enabled**   _optional_ | boolean |
| **EntitlementsPhoneNumber**   _optional_ | string |
| **ExpirationDate**   _optional_ | string \(date-time\) |
| **FirstName**   _optional_ | string |
| **LastName**   _optional_ | string |
| **Login**   _optional_ | string |
| **Middle**   _optional_ | string |
| **PhoneNumber**   _optional_ | string |
| **Salutation**   _optional_ | enum \(NoSalutation, Mr, Mrs, Ms, Dr, Sir, Madam\) |
| **Suffix**   _optional_ | enum \(NoSuffix, Jr, Sr, Second, Third, Fourth\) |
| **TimeZoneInfoId**   _optional_ | string |

### CreateWatchlistModel

| Name | Schema |
| :--- | :--- |
| **Name**   _optional_ | string |
| **Securities**   _optional_ | &lt; integer \(int32\) &gt; array |

### EditableHotkeyModel

| Name | Schema |
| :--- | :--- |
| **ActionId**   _optional_ | integer \(int32\) |
| **Description**   _optional_ | string |
| **KeyboardShortcut**   _optional_ | string |
| **Parameters**   _optional_ | &lt; [HotkeyParameterMapModel](./#hotkeyparametermapmodel) &gt; array |

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

