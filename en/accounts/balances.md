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

A generic [Account](../../objects/account) object that has additional dynamic fields per account-type as shown below: 


* [Equity Account](../../objects/equity-account) object if requesting an Equity account 
* [Option Account](../../objects/option-account) object if requesting an option account 
* [Buying Power](../../objects/buying-power) object with beginning of day and realTime data 


### Errors

* `401` | Unauthorized
* `404` | Not Found
* `5xx` | Unknown internal service error. [Contact TradeStation](mailto:webapi@tradestation.com)

### Examples


Example Request:


    GET https://jp-api.tradestation.com/accounts/114275/balances?APIVersion=20150601 HTTP/1.1
    Authorization: Bearer b0R4MHZ5WjhVUVBzQW5wT
    Accept: application/JSON
    Content-Type: application/x-www-form-urlencoded
    Host: api.tradestation.com

Example Response: ([Account](../../objects/account) object)

    HTTP/1.1 200 OK
    Cache-Control: private
    Content-Length: 1028
    Content-Type: application/json; charset=utf-8
    Server: Microsoft-IIS/7.5
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 23 Dec 2014 17:27:36 GMT

    [{
        "Id": "JPEQ10134",
        "AccountDisplayName": "1234 Display Name",
        "Status": "Open",
        "Currency": "JPY",
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
          "CashUnrealizedProfitLoss": 1288.0,
          "MarginBuyingPower": 9000.0,
          "MarginMaintenanceRatio": 5.0,
          "MarginUnrealizedProftLoss": 7100.0,
          "StockValue": 11000.0
        },
        "RealTimeBuyingPower": {
          "AssetValue": 1010576218,
          "BuyOrderValue": 0,
          "CashAvailableForWithdrawalTPlus1": 803415870,
          "CashAvailableForWithdrawalTPlus2": 803415870,
          "CashAvailableForWithdrawalTPlus3": 803415870,
          "CashBalance": 889725058,
          "CashBuyingPower": 889725058,
          "CashUnrealizedProfitLoss": 8175570,
          "ClosedMarginPositionCost": 0,
          "Commission": 0,
          "LongClosingOrderValue": 0,
          "LongOrderValue": 0,
          "MarginBuyingPower": 2678052900,
          "MarginCashRequirement": 0,
          "MarginExcess": 798388098,
          "MarginExpense": 1201549,
          "MarginMaintenanceRatio": 2.166334461097783,
          "MarginPositionOpeningCost": 283692120,
          "MarginRequirement": 90135411,
          "MarginUnrealizedProftLoss": 2310560,
          "MutualFundCollateral": 0,
          "RealizedLoss": 0,
          "RealizedProfitLoss": 0,
          "RealizedProfit": 0,
          "SellOrderValue": 0,
          "ShortClosingOrderValue": 0,
          "ShortOrderValue": 0,
          "StockCollateral": 0,
          "StockValue": 118540600,
          "TaxRestraint": 0,
          "TotalCollateral": 0

        }
      }]




