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

[Position Group](../../objects/position-group) object

### Errors

* `401` | Unauthorized
* `404` | Not Found
* `5xx` | Unknown internal service error. [Contact TradeStation](mailto:webapi@tradestation.com)

### Examples

Example Request:

    GET https://api.tradestation.com/v2/accounts/JPEQ114275/positiongroups/1234?APIVersion=20150101 HTTP/1.1
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
    
    [
      {
        "GroupId": 1,
        "Positions": [
          {
            "FundSource": {
              "GroupId": 1,
              "Commission": 1.0,
              "CommissionConsumptionTax": 1.0,
              "ContractExpirationDate": "2014-12-19 17:00:05.270+00:00",
              "CorporateActionFee": 1.0,
              "CorporateActionFeeConsumptionTax": 1.0,
              "ExecutedQuantity": 1.0,
              "Interest": 1.0,
              "ManagementFee": 1.0,
              "ManagementFeeConsumptionTax": 1.0,
              "MarginLimitCautionFlag": 0,
              "OnOrderQuantity": 1.0,
              "OpenQuantity": 1.0,
              "OpenSettleDate": "2014-12-19 17:00:05.270+00:00",
              "OpenTradeDate": "2014-12-19 17:00:05.270+00:00",
              "OpenTradePrice": 1.0,
              "RealizedGainLoss": 1.0,
              "ShortInterest": 1.0,
              "Type": "Margin"
            },
            "Id": 1,
            "AccountId": "1234",
            "Symbol": "JP:8698-TS",
            "AssetType": "Equity",
            "ExchangeCode": "TYO",
            "TaxationMethod": "Calculated",
            "CountryCode": "JP",
            "Currency": "¥",
            "TotalQuantity": 500.0
          },
          {
            "FundSource": {
              "GroupId": 1,
              "Commission": 2.0,
              "CommissionConsumptionTax": 2.0,
              "ContractExpirationDate": "2014-12-19 17:00:05.270+00:00",
              "CorporateActionFee": 2.0,
              "CorporateActionFeeConsumptionTax": 2.0,
              "ExecutedQuantity": 2.0,
              "Interest": 2.0,
              "ManagementFee": 2.0,
              "ManagementFeeConsumptionTax": 2.0,
              "MarginLimitCautionFlag": 0,
              "OnOrderQuantity": 2.0,
              "OpenQuantity": 2.0,
              "OpenSettleDate": "2014-12-19 17:00:05.270+00:00",
              "OpenTradeDate": "2014-12-19 17:00:05.270+00:00",
              "OpenTradePrice": 2.0,
              "RealizedGainLoss": 2.0,
              "ShortInterest": 2.0,
              "Type": "Margin"
            },
            "Id": 2,
            "AccountId": "1234",
            "Symbol": "JP:8698-TS",
            "AssetType": "Equity",
            "ExchangeCode": "TYO",
            "TaxationMethod": "Calculated",
            "CountryCode": "JP",
            "Currency": "¥",
            "TotalQuantity": 500.0
          }
        ],
        "FundSource": {
          "Commission": 3.0,
          "CommissionConsumptionTax": 3.0,
          "CorporateActionFee": 3.0,
          "CorporateActionFeeConsumptionTax": 3.0,
          "Interest": 3.0,
          "ManagementFee": 3.0,
          "ManagementFeeConsumptionTax": 3.0,
          "OnOrderQuantity": 3.0,
          "RealizedGainLoss": 3.0,
          "ShortInterest": 3.0,
          "Type": "Margin"
        },
        "AccountId": "1234",
        "Symbol": "JP:8698-TS",
        "AssetType": "Equity",
        "ExchangeCode": "TYO",
        "TaxationMethod": "Calculated",
        "CountryCode": "JP",
        "Currency": "¥",
        "TotalQuantity": 1000.0,
        "AveragePrice": 0.0,
        "Quote": {
          "PreviousClose": 1000.0,
          "PreviousCloseDelta": 5.0,
          "PreviousCloseDeltaPercent": 0.05,
          "Last": 1000.0,
          "Ask": 1005.0,
          "Bid": 995.0,
          "Symbol": "JP:8698-TS",
          "Description": "This is a test description for JP:8698-TS"
        }
      }
    ]