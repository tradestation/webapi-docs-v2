---
layout: en
title: Place Order
category: orders
permalink: place-order/
weight: 1
---

### Summary

Resource for placing orders

### Details

* Method: `POST`
* Path: `/orders`
* URI Parameters:

  * none
* Request Body:

  * [Order Request](../../objects/order) object serialized in JSON or XML

*JSONP*

* URI Parameters

  * none
* Query String Parameters
  * data = URL Encoded JSON serialized [Order Request](../../objects/order) object
  * callback = jQuery method to callback
  * oauth_token = AccessToken
* URL:

      /jsonp/orders/send?data=EncodedSerializedOrderObjectGoesHere
      &callback=jQueryCallback
      &oauth_token=AccessTokenGoesHere
* Authentication: Requires a valid access token

### Returns    

A collection of the [Order Response](../../objects/order-result) object

### Errors

* `401` | Unauthorized
* `404` | Not Found
* `5xx` | Unknown internal service error. [Contact TradeStation
](mailto:webapi@tradestation.com)

### Examples

Example Request:

    POST https://[jp-]api.tradestation.com/v2/orders?APIVersion=20150601 HTTP/1.1
    Authorization: Bearer Qk5WZG01Y2dxRXNyV2kyMGVl
    Accept: application/json
    Content-Type: application/json
    Content-Length: 149
    Expect: 100-continue
    Connection: Keep-Alive
    Host: api.tradestation.com
    
    {
        "OrderConfirmId": "B86D7397-6B2A-4760-ADC6-A6FBA0C31470",
        "ClientTag": "OrderBar",
        "AccountId": "281994",
        "AssetType": "Equity",
        "Side": "Buy",
        "ExchangeCode": "TS",
        "TimeInForce": "DayPlus",
        "LimitPrice": "0.14",
        "Type": "Limit",
        "Quantity": 5,
        "StopPrice": 14.12,
        "Symbol": "JP:8698-TS",
        "TimeInForceExpiration": null,
        "FundSource": "Cash",
        "TaxationMethod": "Calculated",
        "CostBasisMethod" : "FIFO",
        "Condition": "Basic"
    }

Example Response:

    HTTP/1.1 200 OK
    Content-Length: 113
    Content-Type: application/json; charset=utf-8
    
    [{
        "OrderConfirmId": "B86D7397-6B2A-4760-ADC6-A6FBA0C31470",
        "Id": 207887693,
        "Status": "Success",
        "Orders": [
        {
           "Id": "216420"
        }
        ]
    }]

