---
layout: en
title: Orders
category: accounts
permalink: orders/
weight: 3
version: 2.4
---

### Summary

Requesting order information for a particular account

### Details

* Method: `GET`
* To request orders that are currently open and/or were created or executed today
  * Path `/accounts/{accountkey}/orders`
  * Path `/accounts/{accountkey1,accountkey2,etc}/orders`
* To request orders that were made since a given date, max of 30 days back.
  * Path `/accounts/{accountkey}/orders?since={date}`
  * Path `/accounts/{accountkey1,accountkey2,etc}/orders?since={date}`
* URI Parameters:
  * `{accountkey}`
  * `{date, MM-DD-YYYY}` = since date of when orders were placed
* Authentication: Requires a valid access token.

### Returns

List of [Order Detail](../../objects/order-detail) object

### Results Filter

This endpoint accomodates a subset of the [Open Data Protocol](http://www.odata.org/developers/protocols/uri-conventions#FilterSystemQueryOption) which can be used with the $filter querystring parameter to filter responses.

Example orders request that filters results for symbol = AAPL

    /v2/accounts/123456/orders?oauth_token=accessTokenGoesHere&$filter=symbol%20eq%20'AAPL'

### Errors

* `401` | Unauthorized
* `404` | Not Found
* `5xx` | Unknown internal service error. [Contact TradeStation](mailto:webapi@tradestation.com)

### Examples

Example Request:

    GET https://[jp-]api.tradestation.com/v2/accounts/123145/orders?APIVersion=20150601 HTTP/1.1
    Authorization: Bearer b0R4MHZ5WjhVUVBzQW5
    Accept: application/JSON
    Content-Type: application/x-www-form-urlencoded
    Host: api.tradestation.com
    
Example Response ([Order Detail](../../objects/order-detail) object details)

    HTTP/1.1 200 OK
    Cache-Control: private
    Content-Length: 1029
    Content-Type: application/JSON; charset=utf-8
    Server: Microsoft-IIS/7.5
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Wed, 05 Jan 2011 18:11:17 GMT
    
    [{
        Id: 1,
        AccountId: "1234",
        AssetType: "Equity",
        Side: "Buy",
        Symbol: "JP:8698-TS",
        Quantity: 100,
        Type: "Market",
        LimitPrice: 235,
        StopPrice: 200,
        TimeInForce: "Day",
        FundSource: "Cash",
        TaxationMethod: "Calculated",
        OriginatorId: "OriginatorFDCN",
        Commission: 4.99,
        CountryCode: "JP",
        CreatedDateTime: "2014-12-18 11:21:25.940+00:00",
        ExecutedDateTime: "2014-12-18 12:21:25.940+00:00",
        ExchangeDateTime: "2014-12-18 11:21:25.948+00:00",
        ExchangeCode: "TYO",
        Status: "Filled",
        ExecutedQuantity: 100,
        RemainingQuantity: 0,
        AverageExecutedPrice: 235,
        Quote: {
            PreviousClose: 1000,
            PreviousCloseDelta: 5,
            PreviousCloseDeltaPercent: 0.05,
            Last: 1000,
            Ask: 1005,
            Bid: 995,
            Symbol: "JP:8698-TS",
            Description: "This is a test description for JP:8698-TS"
        }
    }]