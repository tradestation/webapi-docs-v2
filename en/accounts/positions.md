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

[Position](../../objects/position) or [PositionGroup](../../objects/position-group) (derived from Position) object

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

    GET https://jp-api.tradestation.com/v2/accounts/114275/positions?APIVersion=20150601 HTTP/1.1
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
    
       [{
            "Id": 3,
            "AccountId": "JPEQ10134",
            "Symbol": "JP:5008-TS",
            "Asset": {
                "Type": "Equity"
            },
            "FundSource": {
                "Type": "Cash"
            },
            "TaxationMethod": "Calculated",
            "Direction": "Long",
            "CountryCode": "",
            "Currency": "JPY",
            "TotalQuantity": 10000,
            "AvailableQuantity": 10000,
            "AveragePrice": 184,
            "Quote": {
                "DisplayType": 1,
                "PreviousClose": 154,
                "PreviousCloseDelta": 1,
                "PreviousCloseDeltaPercent": 0.6493506493506493,
                "Last": 155,
                "Ask": 155,
                "Bid": 154,
                "Symbol": "JP:5008-TS",
                "Description": "東亜石油"
            }
        }, {
            "GroupId": 55,
            "TotalPositions": 11,
            "AccountId": "JPEQ10134",
            "Symbol": "JP:6629-TS",
            "Asset": {
                "Type": "Equity"
            },
            "ExchangeCode": "JQ",
            "FundSource": {
                "Commission": 1641,
                "CommissionConsumptionTax": 132,
                "CorporateActionFee": 0,
                "CorporateActionFeeConsumptionTax": 0,
                "Interest": 862,
                "ManagementFee": 100,
                "ManagementFeeConsumptionTax": 8,
                "OnOrderQuantity": 0,
                "RealizedGainLoss": 0,
                "ShortInterest": 0,
                "Type": "Margin"
            },
            "TaxationMethod": "Calculated",
            "CountryCode": "",
            "Currency": "",
            "TotalQuantity": 1954,
            "AvailableQuantity": 1954,
            "AveragePrice": 191.6,
            "Quote": {
                "DisplayType": 0,
                "PreviousClose": 0,
                "PreviousCloseDelta": 0,
                "PreviousCloseDeltaPercent": 0,
                "Last": 0,
                "Ask": 0,
                "Bid": 0,
                "Symbol": "JP:6629-TS"
            }
        }
    }]
