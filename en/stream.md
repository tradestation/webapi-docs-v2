---
layout: en
title: Stream
category: stream
permalink: stream/
weight: 7
---

### Summary

Streaming API methods provide the consumer with asynchronous streaming data such as quotes & barchart data. 

*note*: Requires real-time exchange entitlements.

### Service URI

`/v2/stream/{resource}`

### Methods

* [Quote/Changes](quote-changes) | Retrieves only changes in quote information for a symbol list
* [Quote/Snapshots](quote-snapshots) | Retrieves a full quote object for any change in quote information for a symbol list
* [BarChart](barchart) | Retrieves quote information that can be used to build a chart
* [TickBars](tick-bars) | Streams tick bars

### Protocol

Streaming API methods utilize chunked-encoding over the http protocol for delivering data events asynchronously.

*See also* [rfc2616 section 3.6.1](http://tools.ietf.org/html/rfc2616#section-3.6.1)

### Behavior

Streaming API methods sometimes behave differently than the other API calls due to the inherent difference between short-lived and long-lived requests.  Some of the areas where it differs include:

* [End of Stream Conditions](end-of-stream-conditions) | Stream end and error conditions.
* [Content Types](content-types) | Supported Content Types & encodings.
* [Heartbeats](heartbeats) | Stream activity detection & zombie stream preventions.



