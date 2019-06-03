---
description: Modify the address of a particular user
---

# Modify User's Address

## Overview

This GET endpoint enables you to modify the address of the user whose ID is provided in the request's path.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request]().
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the internal identifier of the user whose address is to be modified. User IDs can be listed with [this method](../../managing-users/get-users-info/).
5. **user** \(body\). This is the new address of the user.

Here's the final template for this API request:

```text
PUT apiURL/v1.0/users/{userID}/addresses
```

### Request Body Sample

```javascript
{
  "StreetAddress1": "string", //required
  "StreetAddress2": "string",
  "City": "string", //required
  "State": 5, //required
  "PostalCode": "string", // required
  "CountryId": 10 //required
}
```

where:

| Parameter | Description |
| :--- | :--- |
| StreetAddress1 | This is the first line of the user's new address. |
| StreetAddress2 | This is the second line of the user's new address. |
| City | This is the new city in which the user is residing. |
| State | This is the internal identifier of the new state in which the user is residing \(applicable only for the United States\). |
| PostalCode | This is the user's new postal code. |
| CountryId | This is the internal identifier of the new country in which the user is residing. |

## Country and State Identifiers

The **State** and **CountryId** identifiers represent internal identifiers of different countries and US states in the integer format. Each country and US state has a corresponding identifier that you can look up in the following tables.

### US States and Their Corresponding IDs

```text
        Unknown = 0,
        AL = 1,
        AK = 2,
        AZ = 3,
        AR = 4,
        CA = 5,
        CO = 6,
        CT = 7,
        DE = 8,
        FL = 9,
        GA = 10,
        HI = 11,
        ID = 12,
        IL = 13,
        IN = 14,
        IA = 15,
        KS = 16,
        KY = 17,
        LA = 18,
        ME = 19,
        MD = 20,
        MA = 21,
        MI = 22,
        MN = 23,
        MS = 24,
        MO = 25,
        MT = 26,
        NE = 27,
        NV = 28,
        NH = 29,
        NJ = 30,
        NM = 31,
        NY = 32,
        NC = 33,
        ND = 34,
        OH = 35,
        OK = 36,
        OR = 37,
        PA = 38,
        RI = 39,
        SC = 40,
        SD = 41,
        TN = 42,
        TX = 43,
        UT = 44,
        VT = 45,
        VA = 46,
        WA = 47,
        WV = 48,
        WI = 49,
        WY = 50,
        DC = 51,
        PR = 52,
```

### Countries and their Corresponding IDs

VALUES \(CountryId, Country name\):

```text
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(-1, 'Unknown', 'UN', 0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(2, 'UnitedStates','US',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(3,'Afghanistan','AF',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(4,'Albania','AL',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(5,'Algeria','DZ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(6,'AmericanSamoa','AS',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(7,'Andorra','AD',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(8,'Angola','AO',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(9,'Anguilla','AI',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(10,'AntiguaandBarbuda','AG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(11,'Argentina','AR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(12,'Armenia','AM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(13,'Aruba','AW',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(14,'Australia','AU',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(15,'Austria','AT',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(16,'Azerbaijan','AZ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(17,'Bahamas','BS',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(18,'Bahrain','BH',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(19,'Bangladesh','BD',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(20,'Barbados','BB',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(21,'Belarus','BY',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(22,'Belgium','BE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(23,'Belize','BZ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(24,'Benin','BJ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(25,'Bermuda','BM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(26,'Bhutan','BT',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(27,'Bolivia','BO',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(28,'BosniaandHerzegovina','BA',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(29,'Botswana','BW',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(30,'Brazil','BR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(31,'BruneiDarussalam','BN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(32,'Bulgaria','BG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(33,'BurkinaFaso','BF',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(34,'Burundi','BI',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(35,'Cambodia','KH',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(36,'Cameroon','CM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(37,'Canada','CA',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(38,'CapeVerde','CV',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(39,'CaymanIslands','KY',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(40,'CentralAfricanRepublic','CF',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(41,'Chad','TD',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(42,'Chile','CL',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(43,'China','CN',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(44,'Colombia','CO',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(45,'Comoros','KM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(46,'CongoTheDemocraticRepublicofThe','CD',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(47,'CookIslands','CK',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(48,'CostaRica','CR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(49,'CoteDivoire','CI',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(50,'Croatia','HR',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(51,'Cuba','CU',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(52,'Cyprus','CY',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(53,'CzechRepublic','СZ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(54,'Denmark','DK',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(55,'Djiboutis','DJ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(56,'Dominica','DM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(57,'DominicanRepublic','DO',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(58,'Ecuador','EC',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(59,'Egypt','EG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(60,'ElSalvador','SV',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(61,'EquatorialGuinea','GQ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(62,'Eritrea','ER',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(63,'Estonia','EE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(64,'Ethiopia','ET',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(65,'FalklandIslandsMalvinas','FK',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(66,'FaroeIslands','FO',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(67,'Fiji','FJ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(68,'Finland','FI',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(69,'France','FR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(70,'FrenchGuiana','GF',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(71,'FrenchPolynesia','PF',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(72,'Gabon','GA',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(73,'Gambia','GM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(74,'Georgia','GE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(75,'Germany','DE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(76,'Ghana','GH',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(77,'Gibraltar','GI',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(78,'Greece','GR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(79,'Greenland','GL',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(80,'Grenada','GD',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(81,'Guadeloupe','GP',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(82,'Guam','GU',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(83,'Guatemala','GT',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(84,'Guinea','GN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(85,'Guineabissau','GW',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(86,'Guyana','GY',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(87,'Haiti','HT',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(88,'Honduras','HN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(89,'HongKong','HK',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(90,'Hungary','HU',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(91,'Iceland','IS',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(92,'India','IN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(93,'Indonesia','ID',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(94,'Iran','IR',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(95,'Iraq','IQ',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(96,'Ireland','IE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(97,'Israel','IL',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(98,'Italy','IT',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(99,'Jamaica','JM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(100,'Japan','JP',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(101,'Jordan','JO',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(102,'Kazakhstan','KZ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(103,'Kenya','KE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(104,'Kiribati','KI',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(105,'Kuwait','KW',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(106,'Kyrgyzstan','KG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(107,'Laos','LA',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(108,'Latvia','LV',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(109,'Lebanon','LB',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(110,'Lesotho','LS',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(111,'Liberia','LR',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(112,'LibyanArabJamahiriya','LY',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(113,'Liechtenstein','LI',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(114,'Lithuania','LT',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(115,'Luxembourg','LU',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(116,'Macau','MO',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(117,'Macedonia','MK',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(118,'Madagascar','MG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(119,'Malawi','MW',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(120,'Malaysia','MY',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(121,'Maldives','MV',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(122,'Mali','ML',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(123,'Malta','MT',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(124,'MarshallIslands','MH',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(125,'Martinique','MQ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(126,'Mauritania','MR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(127,'Mauritius','MU',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(128,'Mexico','MX',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(129,'MicronesiaFederatedStatesof','FM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(130,'MoldovaRepublicof','MD',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(131,'Monaco','MC',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(132,'Mongolia','MN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(133,'Montenegro','ME',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(134,'Montserrat','MS',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(135,'Morocco','MA',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(136,'Mozambique','MZ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(137,'Myanmar','MM',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(138,'Namibia','NA',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(139,'Nauru','NR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(140,'Nepal','NP',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(141,'Netherlands','NL',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(142,'NetherlandsAntilles','AN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(143,'NewCaledonia','NC',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(144,'NewZealand','NZ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(145,'Nicaragua','NI',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(146,'Niger','NE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(147,'Nigeria','NG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(148,'Niue','NU',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(149,'NorthernMarianaIslands','MP',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(150,'KoreaNorth','KP',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(151,'Norway','NO',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(152,'Oman','OM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(153,'Pakistan','PK',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(154,'Palau','PW',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(155,'PalestinianTerritory','PS',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(156,'Panama','PA',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(157,'PapuaNewGuinea','PG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(158,'Paraguay','PY',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(159,'Peru','PE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(160,'Philippines','PH',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(161,'Poland','PL',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(162,'Portugal','PT',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(163,'PuertoRico','PR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(164,'Qatar','QA',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(165,'Reunion','RE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(166,'Congo','CG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(167,'Romania','RO',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(168,'Russia','RU',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(169,'Rwanda','RW',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(170,'SaintKittsandNevis','KN',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(171,'SaintLucia','LC',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(172,'SaintVincentandTheGrenadines','VC',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(173,'Samoa','WS',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(174,'SanMarino','SM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(175,'SaoTomeandPrincipe','ST',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(176,'SaudiArabia','SA',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(177,'Senegal','SN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(178,'SerbiaandMontenegro','CS',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(179,'Seychelles','SC',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(180,'SierraLeone','SL',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(181,'Singapore','SG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(182,'Slovakia','SK',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(183,'Slovenia','SI',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(184,'SolomonIslands','SB',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(185,'Somalia','SO',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(186,'SouthAfrica','ZA',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(187,'KoreaSouth','KR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(188,'Spain','ES',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(189,'SriLanka','LK',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(190,'Sudan','SD',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(191,'Suriname','SR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(192,'Swaziland','SZ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(193,'Sweden','SE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(194,'Switzerland','CH',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(195,'Syria','SY',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(196,'Taiwan','TW',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(197,'Tajikistan','TJ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(198,'TanzaniaUnitedRepublicof','TZ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(199,'Thailand','TH',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(200,'Tibet','CH',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(201,'Timorleste','TL',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(202,'Togo','TG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(203,'Tokelau','TK',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(204,'Tonga','TO',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(205,'TrinidadandTobago','TT',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(206,'Tunisia','TN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(207,'Turkey','TR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(208,'Turkmenistan','TM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(209,'Tuvalu','TV',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(210,'Uganda','UG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(211,'Ukraine','UA',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(212,'UnitedArabEmirates','AE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(213,'UnitedKingdom','GB',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(214,'Uruguay','UY',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(215,'Uzbekistan','UZ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(216,'Vanuatu','VU',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(217,'VaticanCity','VA',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(218,'Venezuela','VE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(219,'Vietnam','VN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(220,'VirginIslandsBritish','VG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(221,'VirginIslandsUS','VI',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(222,'WallisandFutuna','WF',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(223,'WesternSahara','EH',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(224,'Yemen','YE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(225,'Zambia','ZM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(226,'Zimbabwe','ZW',1)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(227,'Antarctica','AQ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(228,'AshmoreandCartierIslands','AU',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(229,'AzoresPotugal','PT',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(230,'BakerIsland','UM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(232,'BonaireCauracaoNetherlandsAntilles','AN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(233,'BouvetIsland','BV',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(234,'BritishIndianOceanTerritory','IO',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(236,'ClippertonIsland','IP',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(237,'CocosKeelingIslands','CC',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(238,'CoralSeaIslandsTerritory','AU',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(239,'Corsica','FR',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(240,'Curacao','CW',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(241,'EastTimor','TL',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(242,'EuropaIsland','EU',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(243,'FrenchSouthernandAntarcticLands','TF',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(244,'GazaStrip','PS',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(245,'GloriosoIslands','HM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(246,'Guernsey','GG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(247,'HeardIslandandMcDonaldIslands','HM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(248,'HowlandIsland','UM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(249,'IsleofMan','IM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(250,'JanMayen','SJ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(251,'JarvisIsland','UM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(252,'Jersey','JE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(253,'JohnstonAtoll','UM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(255,'KingmanReef','UM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(256,'Mayotte','YT',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(257,'MidwayIslands','UM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(258,'NavassaIsland','UM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(259,'NorfolkIsland','NF',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(260,'PalmyraAtoll','UM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(261,'ParacelIslands','PF',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(262,'PitcairnIsland','PN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(263,'SarawakMalaysai','MY',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(264,'SouthGeorgiaandtheSouthSandwichIslands','GS',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(265,'SpratlyIslands','PG',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(266,'StSaintMartinGuadeloupe','MF',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(267,'StHelenaAscensionIslandandTristandeCunhaIslandGroup','SH',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(268,'StKittsStChristopherNevis','KN',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(269,'StLucia','LC',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(270,'StPierreandMiquelon','PM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(271,'SvalbardSpitsbergen','SJ',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(272,'TromelinIsland','TE',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(273,'TurksandCaicosIslands','TC',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(274,'WakeIsland','UM',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(275,'WestBank','PS',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(276,'WesternSamoa','WS',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(277,'WindwardIslandsGrenadinesNothernStVincent','VC',0)
-- NEW COUNTRIES --
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(278,'Akrotiri','CY',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(279,'Dhekelia','CY',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(280,'Kosovo','XK',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(281,'OtherCountry','OC',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(282,'SaintBarthelemy','BL',0)
INSERT INTO #TEMP_Country (Id, Name, Code, SelfDefinedCode) VALUES(283,'SintMaarten','MF',0)
```

## Response

In response to this API request, you'll receive a JSON file with with the updated user's address.

```javascript
{
  "StreetAddress1": "Downing Street 10",
  "City": "London",
  "State": 0,
  "CountryId": 1
}
```

where:

| Parameter | Description |
| :--- | :--- |
| StreetAddress | This is the street address of the user. |
| City | This is the city is which the user is residing. |
| State | This is the state in which the user is residing \(if applicable\). |
| CountryId | This is the user's country's internal identifier in ETNA Trader. |

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to modify a user's address.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

