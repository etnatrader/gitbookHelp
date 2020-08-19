# Part III

## Definitions

### RoboadvisorWhitelabelInfo

| Name | Schema |
| :--- | :--- |
| **Footer**   _optional_ | string |
| **Icon**   _optional_ | [IFileUpload](./#ifileupload) |
| **Logo**   _optional_ | [IFileUpload](./#ifileupload) |
| **Title**   _optional_ | string |

### SecurityContainerFrame

| Name | Schema |
| :--- | :--- |
| **Descendants**   _optional_   _read-only_ | &lt; [RebalanceFrame](./#rebalanceframe) &gt; array |
| **Description**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **IsReferenced**   _optional_ | boolean |
| **Name**   _optional_ | string |
| **Security**   _optional_ | [ISecurity](./#isecurity) |
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
| **ImagesToUpload**   _optional_ | &lt; [Base64FileMapModel](./#base64filemapmodel) &gt; array |
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

### WebActionParameterMapModel

| Name | Schema |
| :--- | :--- |
| **ActionId**   _optional_ | integer \(int32\) |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |
| **Type**   _optional_ | integer \(int32\) |

