---
layout: en
title: API Versions
category: getting-started
permalink: api-versions/
weight: 4
---

The TradeStation WebAPI is a living API that attempts to improve its contract over time.  As a result, we will introduce new versions over time that include new and breaking changes to the existing API.

### Requesting a specific API version

API-consumers must pass the `APIVersion` via the querystring on each request.  

For example, the current API version is:

* [20150601](../../versions/20150601) - Global/Japanese Equities release.

NOTE: For legacy applications, omitting the `APIVersion` parameter will continue to route to [version 20101026](../../versions/20101026), but will be deprecated at some point in the near future, so its in your best interest to start specifying the APIVersion you wish to receive.

See [Available Versions](../../versions) for more details on what changes are included in each API version.


### Versioning Rules

* Versions are integer value based upon the publish date such as 20140101 for January 1, 2014.
* Only official version numbers are supported - you may not specify any random date, nor the current date.
* Versions are "Opt-In" per request so that you can slowly adopt new versions on a per resource basis.
  * There is no need to request a different version for each API resource.
  * It's recommended that you upgrade all related resources together to avoid unexpected inconsistencies.
* New versions may not affect all resources, and any unaffected resource will continue to work the same as the prior version.
* Versions have a limited lifetime after which it will become deprecated and ultimately will require API-consumers to update to a newer version or else become obsolete.


### Errors

* `401` | Unauthorized
* `400` | Bad Request. 
   * "Invalid Request"   
   * "The APIVersion {version} is invalid"
   * "The APIVersion {version} has been deprecated"
   * "The APIVersion {version} has an invalid format. The APIVersion must be numeric and in this pattern YYYYMMDD"
* `5xx` | Unknown internal service error. [Contact TradeStation](mailto:webapi@tradestation.com)


### Example Request

    GET https://[jp-]api.tradestation.com/WebAPI/users/testuser/accounts?APIVersion=20101026 HTTP/1.1
    Authorization: QUNCSmI
    Accept: application/json
    Content-Type: application/x-www-form-urlencoded
    Host: api.tradestation.com
    
### Example Response 

    HTTP/1.1 200 OK
    Cache-Control: private
    Content-Length: 218
    Content-Type: application/json; charset=utf-8
    Server: Microsoft-IIS/7.5
	APIVersion: 20150601
    Date: Fri, 18 Mar 2011 18:21:45 GMT
    
    [  ... body ... ]

### Example Unsupported Version Response 

    HTTP/1.1 400 Bad Request
    Cache-Control: private
    Content-Length: 218
    Content-Type: application/json; charset=utf-8
    Server: Microsoft-IIS/7.5
    Date: Fri, 18 Mar 2011 18:21:45 GMT
    
	{
	  "Error" : {
	    "StatusCode" : 400
	    "Message" : "The APIVersion 20010101 is invalid"
	  }
	}



*Notes:*

* *Documentation examples use json format but support xml formatting unless otherwise specified.*
