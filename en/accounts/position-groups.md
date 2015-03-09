---
layout: en
title: Position Groups
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

[Position Group](../../objects/position-group) or [Position](../../objects/position) object

### Errors

* `401` | Unauthorized
* `404` | Not Found
* `5xx` | Unknown internal service error. [Contact TradeStation](mailto:webapi@tradestation.com)

### Examples

Example Request:

    GET https://[jp-]api.tradestation.com/v2/accounts/JPEQ114275/positiongroups/1234?APIVersion=20150601 HTTP/1.1
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
    Date: Tue, 23 Dec 2014 18:18:32 GMT
    
    [{
        "GroupId": 104,
        "TotalPositions": 1,
        "Positions": [{
            "Id": 103,
            "AccountId": "JPEQ10134",
            "Symbol": "JP:5012-TS",
            "Asset": {
                "Type": "Equity"
            },
            "ExchangeCode": "TS",
            "FundSource": {
                "GroupId": 104,
                "Commission": 15030,
                "CommissionConsumptionTax": 1202,
                "ContractExpirationDate": "2015-07-07 00:00:00.000+00:00",
                "CorporateActionFee": 0,
                "CorporateActionFeeConsumptionTax": 0,
                "ExecutedQuantity": 0,
                "Interest": 29977,
                "ManagementFee": 1000,
                "ManagementFeeConsumptionTax": 80,
                "MarginLimitCautionFlag": 0,
                "OnOrderQuantity": 0,
                "OpenQuantity": 0,
                "OpenSettleDate": "2015-01-13 00:00:00.000+00:00",
                "OpenTradeDate": "2015-01-07 00:00:00.000+00:00",
                "OpenTradePrice": 1002,
                "RealizedGainLoss": 0,
                "ShortInterest": 0,
                "Type": "Margin"
            },
            "TaxationMethod": "Calculated",
            "CountryCode": "",
            "Currency": "",
            "TotalQuantity": 10000,
            "AvailableQuantity": 10000
        }],
        "AccountId": "JPEQ10134",
        "Symbol": "JP:5012-TS",
        "Asset": {
            "Type": "Equity"
        },
        "ExchangeCode": "TS",
        "FundSource": {
            "Commission": 15030,
            "CommissionConsumptionTax": 1202,
            "CorporateActionFee": 0,
            "CorporateActionFeeConsumptionTax": 0,
            "Interest": 29977,
            "ManagementFee": 1000,
            "ManagementFeeConsumptionTax": 80,
            "OnOrderQuantity": 0,
            "RealizedGainLoss": 0,
            "ShortInterest": 0,
            "Type": "Margin"
        },
        "TaxationMethod": "Calculated",
        "CountryCode": "",
        "Currency": "",
        "TotalQuantity": 10000,
        "AvailableQuantity": 10000,
        "AveragePrice": 1002,
        "Quote": {
            "DisplayType": 1,
            "PreviousClose": 1149,
            "PreviousCloseDelta": -170,
            "PreviousCloseDeltaPercent": -14.795474325500436,
            "Last": 979,
            "Ask": 980,
            "Bid": 979,
            "Symbol": "JP:5012-TS",
            "Description": "東燃ゼネラル石油"
        }
    }]
