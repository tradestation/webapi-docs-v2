---
layout: en
title: Overview
description: What is the TradeStation WebAPI?
category: getting-started
permalink: overview/
weight: 1
---

The WebAPI is a collection of web services for interacting with TradeStation services. These services accept and/or return object data via standard HTTP requests.

The WebAPI exposes streaming barchart resources, however, this data is throttled.

All requests are made via HTTPS URIs that represent objects as a hierarchy of resources and/or actions. The data object format is either JSON or XML and is determined by the request's accept header. [Security](../security-overview) is based on the OAuth 2.0 spec and all requests require a user access token be included.

### Base Uri
The Base URI used to access TradeStation WebAPI services is: 

* [https://[jp-]api.tradestation.com/v2](https://[jp-]api.tradestation.com/v2)

However, you can also reach it via region-specific URI's such as:

* Japan market - [https://jpapi.tradestation.com/v2](https://jpapi.tradestation.com/v2)

### Versioning
The WebAPI is versioned to avoid breaking existing consumers.  
  
See [API Versioning](../api-versioning) for details on how versioning impacts API consumers.  
See [Available Versions](../../versions) for a list of available versions.

### Global WebAPI
The WebAPI is global and therefore some features may have different values or requirements for different markets.

See [Markets](../../markets) for details on the supported markets and how they change behavior.



### Example

Here is a simple example of requesting a list of accounts for a particular user:

#### HTTP Request

    GET https://[jp-]api.tradestation.com/v2/users/testuser/accounts?apiversion=20101026 HTTP/1.1
    Authorization: token
    Accept: application/json
    Content-Type: application/x-www-form-urlencoded
    Host: api.tradestation.com

#### HTTP Response

    HTTP/1.1 200 OK
    Cache-Control: private
    Content-Length: 218
    Content-Type: application/json; charset=utf-8
    Server: Microsoft-IIS/7.5
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    X-APIVersion: 20101026
    Date: Fri, 18 Mar 2011 18:21:45 GMT

    [{
        "Key": 987654,
        "Name": "9876543 MyName",
        "Type": "C",
        "TypeDescription": "Cash"
    }, {
        "Key": 876543,
        "Name": "8765432 MyName",
        "Type": "M",
        "TypeDescription": "Margin"
    }, {
        "Key": 765432,
        "Name": "7654321 MyName",
        "Type": "F",
        "TypeDescription": "Futures"
    }]

### Other Notes

* URLs are NOT case sensitive
* All data is assumed to be UTF8 encoded


