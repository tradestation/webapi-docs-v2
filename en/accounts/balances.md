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




