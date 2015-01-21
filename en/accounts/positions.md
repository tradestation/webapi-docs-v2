---
layout: en
title: Positions
category: accounts
permalink: positions/
weight: 2
version: 2.4
---

### Summary

Requesting position information for a particular account

### Details

* Method: `GET`
* Path: `/accounts/{accountkey}/positions`
* URI Parameters:  
  * `{accountkey}` = The value of `Key` from [AccountInfo](../../objects/account-info) object
* Authentication: Requires a valid access token

### Returns

[Position](../../objects/position) object

### Results Filter

This endpoint accommodates a subset of the [Open Data Protocol](http://www.odata.org/developers/protocols/uri-conventions#FilterSystemQueryOption) which can be used with the $filter querystring parameter to filter responses.

Example positions request that filters results in symbol = AAPL

    /v2/accounts/123456/positions?oauth_token=accessTokenGoesHere&$filter=symbol%20eq%20'AAPL'

### Errors

* `401` | Unauthorized
* `404` | Not Found
* `5xx` | Unknown internal service error. [Contact TradeStation](mailto:webapi@tradestation.com)

### Examples

Example Request:

    GET https://[jp-]api.tradestation.com/v2/accounts/114275/positions?APIVersion=20150601 HTTP/1.1
    Authorization: Bearer b0R4MHZ5WjhVUVBzQW5w
    Accept: application/JSON
    Content-Type: application/x-www-form-urlencoded
    Host: api.tradestation.com

Example Response ([Position](../../objects/position) object details):

    HTTP/1.1 200 OK
    Cache-Control: private
    Content-Length: 7358
    Content-Type: application/JSON; charset=utf-8
    Server: Microsoft-IIS/7.5
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 23 Dec 2014 18:18:32 GMT
    
    [
      {
        "FundSource": {
        "Type": "Cash"
        },
        "Id": 1,
        "AccountId": "1234",
        "AccountDisplayName": "Test Account Display Name",
        "Symbol": "JP:8698-TS",
        "AssetType": "Equity",
        "ExchangeCode": "TYO",
        "TaxationMethod": "Calculated",
        "Direction": "Long",
        "CountryCode": "JP",
        "Currency": "¥",
        "TotalQuantity": 500.0,
        "AveragePrice": 242.0,
        "UnrealizedGainLoss": 10.0,
        "UnrealizedGainLossPercent": 1.0,
        "MarketValue": 100.0,
        "OpenDateTime": "2014-12-22 19:52:32.080+00:00"
      },
      {
        "FundSource": {
        "Type": "Cash"
        },
        "Id": 2,
        "AccountId": "1234",
        "AccountDisplayName": "Test Account Display Name",
        "Symbol": "JP:1722-TS",
        "AssetType": "Equity",
        "ExchangeCode": "TYO",
        "TaxationMethod": "Calculated",
        "Direction": "Long",
        "CountryCode": "JP",
        "Currency": "¥",
        "TotalQuantity": 100.0,
        "AveragePrice": 1028.0,
        "UnrealizedGainLoss": 10.0,
        "UnrealizedGainLossPercent": 1.0,
        "MarketValue": 100.0,
        "OpenDateTime": "2014-12-22 19:52:32.080+00:00",
        "Quote": {
          "PreviousClose": 100.0,
          "PreviousCloseDelta": 5.0,
          "PreviousCloseDeltaPercent": 0.05,
          "Last": 100.0,
          "Ask": 105.0,
          "Bid": 95.0,
          "Symbol": "JP:1722-TS",
          "Description": "This is a test description for JP:1722-TS"
        }
       }
    ]
