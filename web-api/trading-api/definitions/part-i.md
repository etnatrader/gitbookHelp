# Part I

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
| **Legs**   _optional_ | Order legs | &lt; [ModifyOrderResource](./#modifyorderresource) &gt; array |
| **Price**   _optional_ | Price \(not used for some order types\). | number \(double\) |
| **Quantity**   _optional_ | Quantity. Assigned by client.   **Minimum value** : `0` | number \(double\) |
| **StopPrice**   _optional_ | Stop price \(used for stop orders\). | number \(double\) |
| **TrailingLimitAmount**   _optional_ |  | number \(double\) |
| **TrailingLimitAmountType**   _optional_ |  | enum \(Absolute, Persentage\) |
| **TrailingStopAmount**   _optional_ |  | number \(double\) |
| **TrailingStopAmountType**   _optional_ |  | enum \(Absolute, Persentage\) |
| **ValidationsToBypass**   _optional_ | Flag property indicating validation rules to bypass | integer \(int32\) |

