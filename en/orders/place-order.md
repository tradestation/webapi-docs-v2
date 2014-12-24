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

  * [Order](../../objects/order) object serialized in JSON or XML

*JSONP*

* URI Parameters

  * none
* Query String Parameters
  * data = URL Encoded JSON serialized [Order](../../objects/order) object
  * callback = jQuery method to callback
  * oauth_token = AccessToken
* URL:

      /jsonp/orders/send?data=EncodedSerializedOrderObjectGoesHere
      &callback=jQueryCallback
      &oauth_token=AccessTokenGoesHere
* Authentication: Requires a valid access token

### Returns    

A collection of the [Order Result](../../objects/order-result) object

### Errors

* `401` | Unauthorized
* `404` | Not Found
* `5xx` | Unknown internal service error. [Contact TradeStation
](mailto:webapi@tradestation.com)

### Examples

Example Request:

    POST https://api.tradestation.com/v2/orders?APIVersion=20150101 HTTP/1.1
    Authorization: Bearer Qk5WZG01Y2dxRXNyV2kyMGVl
    Accept: application/json
    Content-Type: application/json
    Content-Length: 149
    Expect: 100-continue
    Connection: Keep-Alive
    Host: api.tradestation.com
    
    {
        "OrderConfirmId": "96x0c/Bq00qatgyO+QO4pA",
        "AccountId": 281994,
        "AssetType": "Equity",
        "Side": "Buy",
        "TimeInForce": "DayPlus",
        "LimitPrice": "0.14",
        "Type": "Limit",
        "Quantity": 5,
        "Route": "Intelligent",
        "StopPrice": 14.12,
        "Symbol": "JP:8698-TS",
        "TimeInForceExpiration": null,
        "FundSource": "Cash",
        "TaxationMethod": "Calculated",
        "LotSelectionStrategy": "FirstInFirstOut",
        "Condition": "Basic"
    }

Example Response:

    HTTP/1.1 200 OK
    Content-Length: 113
    Content-Type: application/json; charset=utf-8
    
    [{
        "Message": "Sent order: Buy 5 JP:8698-TS",
        "Id": 207887693,
        "Status": "Success"
    }]

