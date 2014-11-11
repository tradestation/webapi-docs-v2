---
layout: en
title: Position-Groups
category: accounts
permalink: position-groups/
weight: 2
version: 2.4
---

### Summary

Requesting position information for a specific position group under a particular account.  This is available only for Margin accounts and typically only is used for Margin positions.

### Details

* Method: `GET`
* Path: `/accounts/{accountkeys}/positiongroups/{positiongroupid}`
* URI Parameters:

  * `{accountkeys}` - accounts for which to lookup positions
  * `{positiongroupid}` - specific position group to lookup.
* Authentication: Requires a valid access token

### Returns

[Position Group](../../objects/position-group) object

### Errors

* `401` | Unauthorized
* `5xx` | Unknown internal service error. [Contact TradeStation](mailto:webapi@tradestation.com)

### Examples

Example Request:

    GET https://api.tradestation.com/v2/accounts/JPEQ114275/positiongroups/1234 HTTP/1.1
    Authorization: Bearer b0R4MHZ5WjhVUVBzQW5w
    Accept: application/JSON
    Content-Type: application/x-www-form-urlencoded
    Host: api.tradestation.com

Example Response ([Position Group](../../objects/position-group) object details):

    HTTP/1.1 200 OK
    Cache-Control: private
    Content-Length: 7358
    Content-Type: application/JSON; charset=utf-8
    Server: Microsoft-IIS/7.5
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Wed, 05 Jan 2011 18:18:32 GMT
    
    [{
        "GroupId": 123123
        "AccountID": "JPEQ114275",
        "Symbol": "JP:8698-TS",
        "AssetType": "EQ",
        "AskPrice": 36.96,
        "AskPriceDisplay": "36.96",
        "ExchangeCode": "TSE",
        "TaxationMethod": "Tokutei",
        "LongShort": "L",
        "Country": "Japan",
        "Currency": "JPY",
        "TotalQuantity": 500,
        "AveragePrice": 45.0000000000,
        "AveragePriceDisplay": "45.00",
        "UnrealizedGainLoss": 35.66,	
        "UnrealizedGainLossPercent": 0.336,
        "MarketValue": 18100.00000000000,
        "OpenDateTime": "3\/30\/2014 2:51:49 PM"
        "FundSource": "CASH",
        "Commission": 12.00000000000,
        "CommissionConsumptionTax": 2.00000000000,
        "ManagementFee": 2.00000000000,
        "ManagementFeeConsumptionTax": 2.00000000000,
        "CorporateActionFee": 2.00000000000,
        "CorporateActionFeeConsumptionTax": 2.00000000000,
        "Interest": 5.660000000,
        "OnOrderQuantity": 120,
        "TotalExpenses": 22.00000000000,
        "DailyLoanCharge": 22.00000000000,
        "ShortStockFees": 22.00000000000,
        "ShortInterest": 22.00000000000,
        "TotalMarginExpense": 22.00000000000,
        "TotalShortRebate": 22.00000000000,
        "UnrealizedGainLossPerShare": 22.00000000000,
        "TotalShortRebate": 22.00000000000,
        "Positions" : [
                {
                     ... positions ...
                }]
    }}]