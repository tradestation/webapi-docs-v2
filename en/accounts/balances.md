---
layout: en
title: Balances
category: accounts
permalink: balances/
weight: 1
version: 2.4
---

### Summary

Requesting balance information for a particular account

### Details

* Method: `GET`
* Path: `/accounts/{accountkey}/balances`
* URI Parameters:  
  * `{accountkey}` = The value of `Key` from [AccountInfo](../../objects/account-info) object
* Authentication: Requires a valid access token

### Returns

A generic [Account](../../objects/account) or [Japanese Account](../../objects/jp-account) object that has additional dynamic fields per account-type as shown below: 


* [Equity Account](../../objects/equity-account) object if requesting an Equity account (Type = C, M, or D)
* [Japanese Equity Account](../../objects/jp-equity-account) object for Japanese Equities account (Type = J)
* [Option Account](../../objects/jp-option-account) object if requesting an option account 
* [Buying Power](../../objects/buying-power) object with beginning of day and realTime data 


### Errors

* `401` | Unauthorized
* `404` | Not Found
* `5xx` | Server error [Contact TradeStation](mailto:webapi@tradestation.com)

### Examples


Example Request:


    GET https://jp-api.tradestation.com/accounts/114275/balances?APIVersion=20150101 HTTP/1.1
    Authorization: Bearer b0R4MHZ5WjhVUVBzQW5wT
    Accept: application/JSON
    Content-Type: application/x-www-form-urlencoded
    Host: api.tradestation.com

Example Response: ([Japanese Account](../../objects/jp-account) object)

    HTTP/1.1 200 OK
    Cache-Control: private
    Content-Length: 1028
    Content-Type: application/json; charset=utf-8
    Server: Microsoft-IIS/7.5
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 31 May 2011 17:27:36 GMT

    [{
        "Id": "1234",
        "AccountDisplayName": "1234 Display Name",
        "Status": "Open",
        "Restrictions": [
          "MarginCall"
        ],
        "AllowedFundSources": [
          "Cash",
          "StandardMargin",
          "NegotiatedMargin"
        ],
        "AllowedAssets": [
          "Equity"
        ],
        "Equity": {
          "Enabled": true,
          "DayTrading": {
            "Enabled": false
          }
        },
        "BODBuyingPower": {
          "AssetValue": 8000.0,
          "CashBalance": 8675309.0,
          "CashBuyingPower": 1000001.0,
          "CashUnrealizedPL": 1288.0,
          "MarginBuyingPower": 9000.0,
          "MarginMaintenanceRatio": 5.0,
          "MarginUnrealizedPL": 7100.0,
          "StockValue": 11000.0
        },
        "RealTimeBuyingPower": {}
      }]




Example Request:


    GET https://api.tradestation.com/accounts/114275/balances HTTP/1.1
    Authorization: Bearer b0R4MHZ5WjhVUVBzQW5wT
    Accept: application/JSON
    Content-Type: application/x-www-form-urlencoded
    Host: api.tradestation.com

Example Response: ([Account](../../objects/account) object details)

    HTTP/1.1 200 OK
    Cache-Control: private
    Content-Length: 1028
    Content-Type: application/json; charset=utf-8
    Server: Microsoft-IIS/7.5
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 31 May 2011 17:27:36 GMT
    
    {
        "Alias": "",
        "BODBuyingPower": null, 
        "BODEquity": 3247154.8600,
        "BODNetCash": 2870974.6200,
        "ClosedPositions": [],
        "DisplayName": "121111QA",
        "Key": "121111",
        "MarketValue": 0,
        "Name": "121111QA",
        "RTBuyingPower": null,
        "RealTimeAccountBalance": 2870328.5200,
        "RealTimeBuyingPower": 2867875.219800,
        "RealTimeEquity": 3249600.160200,
        "RealTimeRealizedProfitLoss": 0.0000,
        "RealTimeUnrealizedGains": 2445.300200,
        "RealTimeUnrealizedProfitLoss": 19638.14545186560000000000,
        "Status": "A",
        "StatusDescription": "Active",
        "Type": "C",
        "TypeDescription": "Cash",
        "UnclearedDeposit": 0.0000,
        "BODAccountBalance": 2870974.6200,
        "BODDayTradingMarginableEquitiesBuyingPower": 2870328.5200,
        "BODOptionBuyingPower": 2870328.5200,
        "BODOptionValue": 0.0000,
        "BODOvernightBuyingPower": 2870328.5200,
        "CanDayTrade": true,
        "Commission": 0,
        "DayTrades": 7,
        "DayTradingQualified": true,
        "OptionApprovalLevel": 5,
        "PatternDayTrader": false,
        "RealTimeCostOfPositions": 359005.8545,
        "RealTimeDayTradingMarginableEquitiesBuyingPower": 2870326.520000,
        "RealTimeOptionBuyingPower": 2867877.2198,
        "RealTimeOptionValue": 0.0000000000,
        "RealTimeOvernightBuyingPower": 2870326.520000,
        "UnsettledFund": 646.1000
    }

Example Response: ([Equity Account](../../objects/equity-account) object)

    HTTP/1.1 200 OK
    Cache-Control: private
    Content-Length: 1028
    Content-Type: application/json; charset=utf-8
    Server: Microsoft-IIS/7.5
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 31 May 2011 17:27:36 GMT
    
    [{
        "Key": "131111",
        "Name": "131111QA",
        "Status": "A",
        "StatusDescription": "Active",
        "Type": "C",
        "TypeDescription": "Cash",
        ... etc ...
    }]





