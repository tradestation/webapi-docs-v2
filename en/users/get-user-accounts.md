---
layout: en
title: Get User Accounts
category: users
permalink: accounts/
weight: 1
tags: JPEQ
---

### Summary

Requesting accounts associated to a particular user

### Details

* Method: `GET`
* Path: `/users/{userid}/accounts`
* URI Parameters:

  * {userid}
* Authentication: Requires a valid access token

### Returns

[Account Info](../../objects/account-info) object

### Errors

* `401` | Unauthorized
* `404` | Not Found
* `5xx` | Unknown internal service error. [Contact TradeStation](mailto:webapi@tradestation.com)

### Examples

Example Request:

    GET https://[jp-]api.tradestation.com/v2/users/userid/accounts HTTP/1.1
    Authorization: Bearer Ym5BcWVGVHB5NjNKSkJ2bjFHR0FrMEVYekF0M3VuMlZZ
    Accept: application/JSON
    Host: api.tradestation.com

Example Response: ([Account Info](../../objects/account-info) object details)

    HTTP/1.1 200 OK
    Cache-Control: private
    Content-Length: 205
    Content-Type: application/JSON; charset=utf-8
    Server: Microsoft-IIS/7.5
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Thu, 06 Jan 2011 17:21:43 GMT
    
    [{
    "Id": "JPEQ10134",
    "AccountDisplayName": "150-10134",
    "Status": "Open",
    "AllowedFundSources": ["Cash", "StandardMargin", "NegotiatedMargin"],
    "AllowedAssets": ["Equity"]
     }, {
    "Id": "JPEQ10195",
    "AccountDisplayName": "150-10195",
    "Status": "Open",
    "AllowedFundSources": ["Cash", "StandardMargin", "NegotiatedMargin"],
    "AllowedAssets": ["Equity"]
    }]
