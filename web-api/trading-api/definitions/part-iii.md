# Part III

## Definitions

### RoboadvisorWhitelabelInfo

| Name                                                  | Schema                        |
| ----------------------------------------------------- | ----------------------------- |
| <p><strong>Footer</strong>  <br><em>optional</em></p> | string                        |
| <p><strong>Icon</strong>  <br><em>optional</em></p>   | [IFileUpload](./#ifileupload) |
| <p><strong>Logo</strong>  <br><em>optional</em></p>   | [IFileUpload](./#ifileupload) |
| <p><strong>Title</strong>  <br><em>optional</em></p>  | string                        |

### SecurityContainerFrame

| Name                                                                               | Schema                                        |
| ---------------------------------------------------------------------------------- | --------------------------------------------- |
| <p><strong>Descendants</strong>  <br><em>optional</em>  <br><em>read-only</em></p> | < [RebalanceFrame](./#rebalanceframe) > array |
| <p><strong>Description</strong>  <br><em>optional</em></p>                         | string                                        |
| <p><strong>Id</strong>  <br><em>optional</em></p>                                  | integer (int32)                               |
| <p><strong>IsReferenced</strong>  <br><em>optional</em></p>                        | boolean                                       |
| <p><strong>Name</strong>  <br><em>optional</em></p>                                | string                                        |
| <p><strong>Security</strong>  <br><em>optional</em></p>                            | [ISecurity](./#isecurity)                     |
| <p><strong>SecurityId</strong>  <br><em>optional</em></p>                          | integer (int32)                               |
| <p><strong>TargetPercent</strong>  <br><em>optional</em></p>                       | number (double)                               |
| <p><strong>Tolerance</strong>  <br><em>optional</em></p>                           | number (double)                               |
| <p><strong>UnitType</strong>  <br><em>optional</em>  <br><em>read-only</em></p>    | enum (Node, SecurityLeaf, Cash)               |

### SecurityFrameParams

| Name                                                         | Schema          |
| ------------------------------------------------------------ | --------------- |
| <p><strong>Description</strong>  <br><em>optional</em></p>   | string          |
| <p><strong>Name</strong>  <br><em>optional</em></p>          | string          |
| <p><strong>SecurityId</strong>  <br><em>optional</em></p>    | integer (int32) |
| <p><strong>TargetPercent</strong>  <br><em>optional</em></p> | number (double) |
| <p><strong>Tolerance</strong>  <br><em>optional</em></p>     | number (double) |

### SecurityHistoryRequestSettings

| Name                                                                | Schema          |
| ------------------------------------------------------------------- | --------------- |
| <p><strong>CandlesCount</strong>  <br><em>optional</em></p>         | integer (int32) |
| <p><strong>EndDate</strong>  <br><em>optional</em></p>              | integer (int32) |
| <p><strong>IncludeNonMarketData</strong>  <br><em>optional</em></p> | boolean         |
| <p><strong>Interval</strong>  <br><em>optional</em></p>             | integer (int32) |
| <p><strong>Period</strong>  <br><em>optional</em></p>               | string          |
| <p><strong>StartDate</strong>  <br><em>optional</em></p>            | integer (int32) |

### SecurityModel

| Name                                                                    | Schema                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ----------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><strong>AddedDate</strong>  <br><em>optional</em></p>                | string (date-time)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| <p><strong>BaseCurrency</strong>  <br><em>optional</em></p>             | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>ContractSize</strong>  <br><em>optional</em></p>             | number (double)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| <p><strong>Currency</strong>  <br><em>optional</em></p>                 | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>Cusip</strong>  <br><em>optional</em></p>                    | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>Description</strong>  <br><em>optional</em></p>              | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>Exchange</strong>  <br><em>optional</em></p>                 | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>ExpirationDate</strong>  <br><em>optional</em></p>           | string (date-time)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| <p><strong>ExpirationType</strong>  <br><em>optional</em></p>           | enum (Regular, Quarterly, Weekly, Flex, Undefined, Mini, NonStandard)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| <p><strong>Id</strong>  <br><em>optional</em></p>                       | integer (int32)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| <p><strong>Industry</strong>  <br><em>optional</em></p>                 | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>Isin</strong>  <br><em>optional</em></p>                     | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>MarginRate</strong>  <br><em>optional</em></p>               | number (double)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| <p><strong>ModifyDate</strong>  <br><em>optional</em></p>               | string (date-time)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| <p><strong>OptionType</strong>  <br><em>optional</em></p>               | enum (Call, Put, Undefined)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| <p><strong>ParentId</strong>  <br><em>optional</em></p>                 | integer (int32)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| <p><strong>Precision</strong>  <br><em>optional</em></p>                | integer (int32)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| <p><strong>Sector</strong>  <br><em>optional</em></p>                   | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>Sedol</strong>  <br><em>optional</em></p>                    | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>SeriesId</strong>  <br><em>optional</em></p>                 | integer (int32)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| <p><strong>Source</strong>  <br><em>optional</em></p>                   | integer (int32)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| <p><strong>StrikePrice</strong>  <br><em>optional</em></p>              | number (double)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| <p><strong>Suffix</strong>  <br><em>optional</em></p>                   | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>Symbol</strong>  <br><em>optional</em></p>                   | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>TickSize</strong>  <br><em>optional</em></p>                 | number (double)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| <p><strong>Type</strong>  <br><em>optional</em></p>                     | enum (BankersAcceptance, CertificateOfDeposit, CollateralizeMortgageObligation, CorporateBond, CommercialPaper, CorporatePrivatePlacement, CommonStock, FederalHousingAuthority, FederalHomeLoan, FederalNationalMortgageAssociation, ForeignExchangeContract, Future, GovernmentNationalMortgageAssociation, TreasuriesPlusAgencyDebenture, MutualFund, MortgageInterestOnly, MortgagePrincipleOnly, MortgagePrivatePlacement, MiscellaneousPassThru, MunicipalBond, NoIsitcSecurityType, Option, PreferredStock, RepurchaseAgreement, ReverseRepurchaseAgreement, StudentLoanMarketingAssociation, TimeDeposit, UsTreasuryBill, Warrant, CatsTigersLions, WildcardEntry, ConvertibleBond, MortgageIoette, Index, FakeStockForNonStandartOption, Right, Cryptocurrency, ETF, DepositoryReceipt, CoveredWarrant, Unit) |
| <p><strong>UnderlyingSecuritySymbol</strong>  <br><em>optional</em></p> | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>Unit</strong>  <br><em>optional</em></p>                     | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p><strong>VolumePrecision</strong>  <br><em>optional</em></p>          | integer (int32)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

### SecuritySignature

| Name                                                    | Schema |
| ------------------------------------------------------- | ------ |
| <p><strong>Currency</strong>  <br><em>optional</em></p> | string |
| <p><strong>Exchange</strong>  <br><em>optional</em></p> | string |
| <p><strong>Symbol</strong>  <br><em>optional</em></p>   | string |

### SubmitFeedbackModel

| Name                                                          | Schema                                                |
| ------------------------------------------------------------- | ----------------------------------------------------- |
| <p><strong>BuildVersion</strong>  <br><em>optional</em></p>   | string                                                |
| <p><strong>Comment</strong>  <br><em>optional</em></p>        | string                                                |
| <p><strong>Contacts</strong>  <br><em>optional</em></p>       | string                                                |
| <p><strong>ImagesToUpload</strong>  <br><em>optional</em></p> | < [Base64FileMapModel](./#base64filemapmodel) > array |
| <p><strong>Subject</strong>  <br><em>optional</em></p>        | string                                                |

### SubscriptionModel

Web API notification service subscription representation

| Name                                                            | Description                                | Schema                                                                                             |
| --------------------------------------------------------------- | ------------------------------------------ | -------------------------------------------------------------------------------------------------- |
| <p><strong>Channel</strong>  <br><em>optional</em></p>          | Channel for subscription messages delivery | enum (Email, MobileText, MobilePush, WebPopupAlert, Disabled)                                      |
| <p><strong>State</strong>  <br><em>optional</em></p>            | Subscription state                         | enum (NotLinked, Active, Suspended, NotVerified)                                                   |
| <p><strong>SubscriptionType</strong>  <br><em>optional</em></p> | Subscription notification type             | enum (OrderExecution, OrderForReview, OrderOnReview, OrderPlacement, OrderReplacement, PriceAlert) |

### Succeed

| Name                                                                         | Schema |
| ---------------------------------------------------------------------------- | ------ |
| <p><strong>State</strong>  <br><em>optional</em>  <br><em>read-only</em></p> | string |
| <p><strong>Token</strong>  <br><em>optional</em></p>                         | string |

### SupportResistanceMapModel

| Name                                                           | Schema                                              |
| -------------------------------------------------------------- | --------------------------------------------------- |
| <p><strong>Levels</strong>  <br><em>optional</em></p>          | < [LevelInfoMapModel](./#levelinfomapmodel) > array |
| <p><strong>ResistancePrice</strong>  <br><em>optional</em></p> | number (double)                                     |
| <p><strong>SupportPrice</strong>  <br><em>optional</em></p>    | number (double)                                     |

### TimeFrameModel

| Name                                                                | Schema          |
| ------------------------------------------------------------------- | --------------- |
| <p><strong>CandlesCount</strong>  <br><em>optional</em></p>         | integer (int32) |
| <p><strong>EndDate</strong>  <br><em>optional</em></p>              | integer (int32) |
| <p><strong>IncludeNonMarketData</strong>  <br><em>optional</em></p> | boolean         |
| <p><strong>Period</strong>  <br><em>optional</em></p>               | string          |
| <p><strong>StartDate</strong>  <br><em>optional</em></p>            | integer (int32) |

### TimeSeriesValueCandleMapModel

| Name                                                                            | Schema                    |
| ------------------------------------------------------------------------------- | ------------------------- |
| <p><strong>Close</strong>  <br><em>optional</em></p>                            | number (double)           |
| <p><strong>DateTime</strong>  <br><em>optional</em>  <br><em>read-only</em></p> | string (date-time)        |
| <p><strong>High</strong>  <br><em>optional</em></p>                             | number (double)           |
| <p><strong>IsMarket</strong>  <br><em>optional</em></p>                         | boolean                   |
| <p><strong>Low</strong>  <br><em>optional</em></p>                              | number (double)           |
| <p><strong>Open</strong>  <br><em>optional</em></p>                             | number (double)           |
| <p><strong>OpenInterest</strong>  <br><em>optional</em></p>                     | integer (int32)           |
| <p><strong>Time</strong>  <br><em>optional</em></p>                             | integer (int32)           |
| <p><strong>ValuationLevels</strong>  <br><em>optional</em></p>                  | < number (double) > array |
| <p><strong>Volume</strong>  <br><em>optional</em></p>                           | number (double)           |

### TimeZoneInfoItem

| Name                                                       | Schema |
| ---------------------------------------------------------- | ------ |
| <p><strong>description</strong>  <br><em>optional</em></p> | string |
| <p><strong>ianaId</strong>  <br><em>optional</em></p>      | string |
| <p><strong>name</strong>  <br><em>optional</em></p>        | string |

### TransactionMapModel

| Name                                                          | Schema                                                                                                     |
| ------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| <p><strong>AccountId</strong>  <br><em>optional</em></p>      | integer (int32)                                                                                            |
| <p><strong>Date</strong>  <br><em>optional</em></p>           | string (date-time)                                                                                         |
| <p><strong>Description</strong>  <br><em>optional</em></p>    | string                                                                                                     |
| <p><strong>Fee</strong>  <br><em>optional</em></p>            | [FeeModel](./#feemodel)                                                                                    |
| <p><strong>Id</strong>  <br><em>optional</em></p>             | integer (int32)                                                                                            |
| <p><strong>IsDayTrade</strong>  <br><em>optional</em></p>     | boolean                                                                                                    |
| <p><strong>LeavesQuantity</strong>  <br><em>optional</em></p> | number (double)                                                                                            |
| <p><strong>OrderStateId</strong>  <br><em>optional</em></p>   | integer (int32)                                                                                            |
| <p><strong>Quantity</strong>  <br><em>optional</em></p>       | number (double)                                                                                            |
| <p><strong>SecurityId</strong>  <br><em>optional</em></p>     | integer (int32)                                                                                            |
| <p><strong>Type</strong>  <br><em>optional</em></p>           | enum (Undefined, Commission, OrderExecution, OptionExpiration, Payment, ManualManipulation, Clearing, Rpl) |
| <p><strong>Value</strong>  <br><em>optional</em></p>          | number (double)                                                                                            |

### Tuple\[Int32,String]

| Name                                                   | Schema          |
| ------------------------------------------------------ | --------------- |
| <p><strong>m_Item1</strong>  <br><em>optional</em></p> | integer (int32) |
| <p><strong>m_Item2</strong>  <br><em>optional</em></p> | string          |

### Tuple\[PhoneNumberModel,Int32]

| Name                                                   | Schema                                  |
| ------------------------------------------------------ | --------------------------------------- |
| <p><strong>m_Item1</strong>  <br><em>optional</em></p> | [PhoneNumberModel](./#phonenumbermodel) |
| <p><strong>m_Item2</strong>  <br><em>optional</em></p> | integer (int32)                         |

### UserAccountModel

| Name                                                           | Schema                                           |
| -------------------------------------------------------------- | ------------------------------------------------ |
| <p><strong>AccessType</strong>  <br><em>optional</em></p>      | enum (Full, ReadOnly, ClosePositionsOnly)        |
| <p><strong>Alias</strong>  <br><em>optional</em></p>           | string                                           |
| <p><strong>ClearingAccount</strong>  <br><em>optional</em></p> | string                                           |
| <p><strong>Enabled</strong>  <br><em>optional</em></p>         | boolean                                          |
| <p><strong>Id</strong>  <br><em>optional</em></p>              | integer (int32)                                  |
| <p><strong>MarginType</strong>  <br><em>optional</em></p>      | enum (Empty, Cash, Margin, DayTrader, MarginIra) |

### UserInfoModel

| Name                                                      | Schema                                           |
| --------------------------------------------------------- | ------------------------------------------------ |
| <p><strong>AddedDate</strong>  <br><em>optional</em></p>  | string (date-time)                               |
| <p><strong>Email</strong>  <br><em>optional</em></p>      | string                                           |
| <p><strong>FirstName</strong>  <br><em>optional</em></p>  | string                                           |
| <p><strong>LastName</strong>  <br><em>optional</em></p>   | string                                           |
| <p><strong>Login</strong>  <br><em>optional</em></p>      | string                                           |
| <p><strong>MiddleName</strong>  <br><em>optional</em></p> | string                                           |
| <p><strong>Salutation</strong>  <br><em>optional</em></p> | enum (NoSalutation, Mr, Mrs, Ms, Dr, Sir, Madam) |
| <p><strong>Suffix</strong>  <br><em>optional</em></p>     | enum (NoSuffix, Jr, Sr, Second, Third, Fourth)   |
| <p><strong>UserId</strong>  <br><em>optional</em></p>     | integer (int32)                                  |

### VerifyOrderModel

| Name                                                                | Description                    | Schema                                |
| ------------------------------------------------------------------- | ------------------------------ | ------------------------------------- |
| <p><strong>Commission</strong>  <br><em>optional</em></p>           | The commission of the order.   | number (double)                       |
| <p><strong>Commissions</strong>  <br><em>optional</em></p>          | The commission of the order.   | < string, number (double) > map       |
| <p><strong>Cost</strong>  <br><em>optional</em></p>                 | The cost of the order.         | number (double)                       |
| <p><strong>ErrorDescription</strong>  <br><em>optional</em></p>     | Error description.             | string                                |
| <p><strong>ErrorDescriptionArgs</strong>  <br><em>optional</em></p> | Error description arguments.   | < string > array                      |
| <p><strong>IsSuccessful</strong>  <br><em>optional</em></p>         | Result.                        | boolean                               |
| <p><strong>MarginChange</strong>  <br><em>optional</em></p>         | Expected margin value changed. | number (double)                       |
| <p><strong>NetCost</strong>  <br><em>optional</em></p>              | The net cost of the order.     | number (double)                       |
| <p><strong>Quotes</strong>  <br><em>optional</em></p>               | Order validation quotes.       | < [QuoteModel](./#quotemodel) > array |

### WatchlistModel

| Name                                                        | Schema                                      |
| ----------------------------------------------------------- | ------------------------------------------- |
| <p><strong>CreateDate</strong>  <br><em>optional</em></p>   | string (date-time)                          |
| <p><strong>Description</strong>  <br><em>optional</em></p>  | string                                      |
| <p><strong>Id</strong>  <br><em>optional</em></p>           | integer (int32)                             |
| <p><strong>ModifyDate</strong>  <br><em>optional</em></p>   | string (date-time)                          |
| <p><strong>Name</strong>  <br><em>optional</em></p>         | string                                      |
| <p><strong>ReadOnly</strong>  <br><em>optional</em></p>     | boolean                                     |
| <p><strong>SecurityList</strong>  <br><em>optional</em></p> | < [SecurityModel](./#securitymodel) > array |
| <p><strong>Source</strong>  <br><em>optional</em></p>       | string                                      |
| <p><strong>Type</strong>  <br><em>optional</em></p>         | enum (UserList, SystemList, Snapshot)       |

### WebActionMapModel

| Name                                                       | Schema                                                                |
| ---------------------------------------------------------- | --------------------------------------------------------------------- |
| <p><strong>Action</strong>  <br><em>optional</em></p>      | string                                                                |
| <p><strong>Description</strong>  <br><em>optional</em></p> | string                                                                |
| <p><strong>Id</strong>  <br><em>optional</em></p>          | integer (int32)                                                       |
| <p><strong>Name</strong>  <br><em>optional</em></p>        | string                                                                |
| <p><strong>Parameters</strong>  <br><em>optional</em></p>  | < [WebActionParameterMapModel](./#webactionparametermapmodel) > array |

### WebActionParameterMapModel

| Name                                                    | Schema          |
| ------------------------------------------------------- | --------------- |
| <p><strong>ActionId</strong>  <br><em>optional</em></p> | integer (int32) |
| <p><strong>Id</strong>  <br><em>optional</em></p>       | integer (int32) |
| <p><strong>Name</strong>  <br><em>optional</em></p>     | string          |
| <p><strong>Type</strong>  <br><em>optional</em></p>     | integer (int32) |
