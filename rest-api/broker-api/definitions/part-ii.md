# Part II

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
| **Levels**   _optional_ | &lt; [LevelInfoMapModel](./#levelinfomapmodel) &gt; array |
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

### TransactionMapModel

| Name | Schema |
| :--- | :--- |
| **AccountId**   _optional_ | integer \(int32\) |
| **Date**   _optional_ | string \(date-time\) |
| **Description**   _optional_ | string |
| **Fee**   _optional_ | [FeeModel](./#feemodel) |
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
| **m\_Item1**   _optional_ | [PhoneNumberModel](./#phonenumbermodel) |
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

### UserAddress

| Name | Schema |
| :--- | :--- |
| **City**   _optional_ | string |
| **CountryId**   _optional_ | integer \(int32\) |
| **PostalCode**   _optional_ | string |
| **State**   _optional_ | integer \(int32\) |
| **StreetAddress1**   _optional_ | string |
| **StreetAddress2**   _optional_ | string |

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

### UserModel

| Name | Schema |
| :--- | :--- |
| **AddedDate**   _optional_ | string \(date-time\) |
| **Deleted**   _optional_ | boolean |
| **EmailAddress**   _optional_ | string |
| **Enabled**   _optional_ | boolean |
| **EntitlementsPhoneNumber**   _optional_ | string |
| **ExpirationDate**   _optional_ | string \(date-time\) |
| **FirstName**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **LastName**   _optional_ | string |
| **Login**   _optional_ | string |
| **Middle**   _optional_ | string |
| **PhoneNumber**   _optional_ | string |
| **Salutation**   _optional_ | enum \(NoSalutation, Mr, Mrs, Ms, Dr, Sir, Madam\) |
| **Suffix**   _optional_ | enum \(NoSuffix, Jr, Sr, Second, Third, Fourth\) |
| **TimeZoneInfoId**   _optional_ | string |

### UserToAccountRelationModel

| Name | Schema |
| :--- | :--- |
| **AccountAccessType**   _optional_ | enum \(Full, ReadOnly, ClosePositionsOnly\) |
| **UserModel**   _optional_ | [UserInfoModel](./#userinfomodel) |

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
| **Quotes**   _optional_ | Order validation quotes. | &lt; [QuoteModel](./#quotemodel) &gt; array |

### WatchlistModel

| Name | Schema |
| :--- | :--- |
| **CreateDate**   _optional_ | string \(date-time\) |
| **Description**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **ModifyDate**   _optional_ | string \(date-time\) |
| **Name**   _optional_ | string |
| **ReadOnly**   _optional_ | boolean |
| **SecurityList**   _optional_ | &lt; [SecurityModel](./#securitymodel) &gt; array |
| **Source**   _optional_ | string |
| **Type**   _optional_ | enum \(UserList, SystemList, Snapshot\) |

### WebActionMapModel

| Name | Schema |
| :--- | :--- |
| **Action**   _optional_ | string |
| **Description**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |
| **Parameters**   _optional_ | &lt; [WebActionParameterMapModel](./#webactionparametermapmodel) &gt; array |

### WebActionModifyModel

| Name | Schema |
| :--- | :--- |
| **Action**   _optional_ | string |
| **Description**   _optional_ | string |
| **Name**   _optional_ | string |

### WebActionParameterMapModel

| Name | Schema |
| :--- | :--- |
| **ActionId**   _optional_ | integer \(int32\) |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |
| **Type**   _optional_ | integer \(int32\) |

