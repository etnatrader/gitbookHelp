# Part IV

## Definitions

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
| **Levels**   _optional_ | &lt; [LevelInfoMapModel]() &gt; array |
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
| **Fee**   _optional_ | [FeeModel]() |
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
| **m\_Item1**   _optional_ | [PhoneNumberModel]() |
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
| **UserModel**   _optional_ | [UserInfoModel]() |

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
| **Quotes**   _optional_ | Order validation quotes. | &lt; [QuoteModel]() &gt; array |

### WatchlistModel

| Name | Schema |
| :--- | :--- |
| **CreateDate**   _optional_ | string \(date-time\) |
| **Description**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **ModifyDate**   _optional_ | string \(date-time\) |
| **Name**   _optional_ | string |
| **ReadOnly**   _optional_ | boolean |
| **SecurityList**   _optional_ | &lt; [SecurityModel]() &gt; array |
| **Source**   _optional_ | string |
| **Type**   _optional_ | enum \(UserList, SystemList, Snapshot\) |

### WebActionMapModel

| Name | Schema |
| :--- | :--- |
| **Action**   _optional_ | string |
| **Description**   _optional_ | string |
| **Id**   _optional_ | integer \(int32\) |
| **Name**   _optional_ | string |
| **Parameters**   _optional_ | &lt; [WebActionParameterMapModel]() &gt; array |

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

