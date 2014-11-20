---
layout: en
title: API Versions
category: getting-started
permalink: api-versions/
weight: 4
---

The TradeStation WebAPI is a living API that attempts to improve its contract over time.  As a result, we will introduce new versions over time that include new and breaking changes to the existing API.

Typically, 3 versions will be maintained at any given time:

* Current Version
* Last Version
* Next Version

### Versioning Contract

* Versions use integer numbering with no factional version.
* Versions are Global but are applied Locally to resources. 
   * Apply to the whole API surface, but changes may occur on only 1 or a few resources.
   * If a resource did not change, it will still be carried forward to the next version unchanged, so there is  no need to request a different version for each API resource.
* Versions are opt-in, with each API-version having a limited lifetime after which it will become deprecated and ultimately will require API-consumers to update to a newer version or else become obsolete.
* If no `Accept-Version` header is specified, the "Current" version is used.

### Requesting a specific API version

API-consumers are expected to pass the `Accept-Version` header on each request.

If no `Accept-Version` header is specified, the "Current" version is defaulted.

See below for an example of how to specify a version:


### Errors

* `401` | Unauthorized
* `412` | Precondition Failed.  Version Not Supported
* `5xx` | Unknown internal service error. [Contact TradeStation](mailto:webapi@tradestation.com)


### Example Request

    GET https://api.tradestation.com/WebAPI/users/testuser/accounts HTTP/1.1
    Authorization: QUNCSmI
    Accept: application/json
    Content-Type: application/x-www-form-urlencoded
    Host: api.tradestation.com
	Accept-Version: 2
    
### Example Response 

    HTTP/1.1 200 OK
    Cache-Control: private
    Content-Length: 218
    Content-Type: application/json; charset=utf-8
    Server: Microsoft-IIS/7.5
	Version: 2
    Date: Fri, 18 Mar 2011 18:21:45 GMT
    
    [  ... body ... ]

### Example Unsupported Version Response 

    HTTP/1.1 412OK
    Cache-Control: private
    Content-Length: 218
    Content-Type: application/json; charset=utf-8
    Server: Microsoft-IIS/7.5
    Date: Fri, 18 Mar 2011 18:21:45 GMT
    
    Precondition Failed. Version Not Supported



*Notes:*

* *Documentation examples use json format but support xml formatting unless otherwise specified.*
