---
layout: en
title: Japan
category: markets
permalink: jp/
weight: 4
---

The Japan market has different mechanics from other global markets which impact the TradeStation WebAPI in numerous ways.

This document acts as a consolidated list of the high-level differences in API behavior, requests, responses, and field values for developers consuming the TradeStation WebAPI. 

### Overview

The TradeStation WebAPI underwent a significant redesign with [version 20150101](../../versions/20150101) to improve support for international markets.  Therefore this is the first version where Japan markets are supported.  Below are details of the Japan-specific changes included as part of that version and how they affect API-consumers.  

### Japan-Specific URI
Please use the following base service URI for the Japanese market:

* [https://jpapi.tradestation.com/v2/](https://jpapi.tradestation.com/v2/)

Although the WebAPI can be accessed globally, the above Uri directly addresses the Japan market features.  For all API resources listed in this documentation, you can replace references to https://api.tradestation.com/v2 with the above Uri.

###Symbology
Symbology is the way in which TradeStation interprets symbol data from the TradeStaton Network for display or when passing a Symbol Name to a request when calling the TradeStation WebAPI.

For international equities, the symbol name syntax follows the scheme below with the country code prefix:

* ```{country code}:{symbol name/number}```

However, for the Japan market, symbols are unique across all exchanges, so you must specify which exchange you want by appending a suffix of the exchange-code.

So, for the Japan market the full symbol name syntax follows this scheme:

* ```JP:{symbol number}-{exchange code}```

For example:

* Monex Group (8698) listed on Tokyo Stock Exchange  
   * Symbol: ```JP:8698-TS```
* Sony Corp (6758) listed on JASDAQ  
   * Symbol: ```JP:6758-JQ```

See Also [TradeStation Platform Symbology Types](http://help.tradestation.com/09_00/tradestationhelp/symbology/tradestation_symbology_types.htm).

###Feature Changes

The following WebAPI resources & features were changed to support specific market mechanics and data for  Japan exchanges and regulatory practices.

* [Accounts](../../accounts)
  * [Get User Accounts](../../users/get-user-accounts) (new fields, values)
  * [Balances](../../accounts/balances) (new fields, values)
  * [Orders](../../accounts/orders) (new fields, values)
  * [Positions](../../accounts/positions) (new fields, values)
  * [Position Groups](../../accounts/position-groups) (new resource)