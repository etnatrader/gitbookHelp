# Part III

## Definitions

### PagingResult\[AccountModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [AccountModel](./#accountmodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[FeedbackModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [FeedbackModel](./#feedbackmodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[HotkeyMapModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [HotkeyMapModel](./#hotkeymapmodel) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[IList\[UserModel\]\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; &lt; [UserModel](./#usermodel) &gt; array &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[InternalSecurityResource\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [InternalSecurityResource](./#internalsecurityresource) &gt; array |
| **TotalCount**   _optional_ | Items total count | integer \(int32\) |

### PagingResult\[LocalizationResourceMapModel\]

| Name | Description | Schema |
| :--- | :--- | :--- |
| **NextPageLink**   _optional_ | Next page | string |
| **PreviousPageLink**   _optional_ | Previous page | string |
| **Result**   _optional_ | Result collection | &lt; [LocalizationResourceMapModel](./#localizationresourcemapmodel) &gt; array |
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

### PaymentInfoModel

| Name | Schema |
| :--- | :--- |
| **Amount**   _optional_ | number \(double\) |
| **CreateDate**   _optional_ | string \(date-time\) |
| **Description**   _optional_ | string |

### PhoneNumberModel

| Name | Schema |
| :--- | :--- |
| **PhoneNumber**   _optional_ | string |
| **PhoneNumberState**   _optional_ | enum \(NotLinked, Active, Suspended, NotVerified\) |

### PolicyEditableModel

Editable policy

| Name | Description | Schema |
| :--- | :--- | :--- |
| **Name**   _required_ | Name | string |

### PolicyInfoModel

| Name | Schema |
| :--- | :--- |
| **Date**   _optional_ | string \(date-time\) |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |
| **Rules**   _optional_ | &lt; [PolicyRuleInfoModel](./#policyruleinfomodel) &gt; array |

### PolicyRuleEditableModel

Editable policy rule

| Name | Description | Schema |
| :--- | :--- | :--- |
| **Attributes**   _required_ | Rule attributes | &lt; string, string &gt; map |
| **Name**   _required_ | Rule name | string |

### PolicyRuleInfoModel

| Name | Schema |
| :--- | :--- |
| **Attributes**   _optional_ | &lt; string, string &gt; map |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |

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

### ResendOrderReportRequest

| Name | Schema |
| :--- | :--- |
| **EndSequenceNumber**   _optional_ | integer \(int32\) |
| **ExecutionVenue**   _optional_ | string |
| **StartSequenceNumber**   _optional_ | integer \(int32\) |

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

### SimpleAllocationRequest

| Name | Schema |
| :--- | :--- |
| **AccountType**   _optional_ | enum \(Cash, Margin\) |
| **Action**   _optional_ | enum \(Buy, Sell, SellShort, BuyToCover, SellToClose, BuyToClose, SellToOpen, BuyToOpen\) |
| **Comment**   _optional_ | string |
| **Commission**   _optional_ | number \(double\) |
| **FromAccount**   _optional_ | string |
| **Instructions**   _optional_ | &lt; string, string &gt; map |
| **Price**   _optional_ | number \(double\) |
| **Quantity**   _optional_ | number \(double\) |
| **Symbol**   _optional_ | string |
| **ToAccount**   _optional_ | string |



