---
layout: en
title: Heartbeats
category: stream
permalink: heartbeats/
weight: 4
---

### Summary

One of the challenges of consuming a streaming API is determining the difference between a stream that currently has no data and a stream that has silently failed & become a *zombie stream*.  

Heartbeats are a common technique used in these situations.  The streaming API's support *opt-in* for heartbeats by appending a querystring to the service URI indicating that heartbeats should be included and what style and interval to emit heartbeats.

When enabled, the streaming API method will include additional events on the stream that are *json-encoded* with a datetime stamp so the consumer can also validate the latency of the heartbeats.

### Service URI

`https://api.tradestation.com/v2/stream/{resource}?heartbeat={true|false|interval}&heartbeat-style={heartbeat-style}`

### Heartbeat Options

The **heartbeat** querystring parameter can be used as a simple flag for enabling/disabling heartbeats with the values *true* or *false*.  By default, when set to *true* heartbeats will be emitted every 5 seconds.  However, you can override this by providing an interval in milliseconds such as *heartbeat=8000* for every 8 seconds.

### Heartbeat Style (optional)

By default, the heartbeat style is set to **constant**.  This indicates that the heartbeat will occur regardless of actual data events occurring and will continue on a constant interval.

Alternatively, you can set the heartbeat style to **keepalive**.  This indicates that you only want heartbeats whenever no data events are occurring.   In this case, heartbeats will start when no data events have ocurred for the duration of the heartbeat interval (default: 5000ms) and continue until the next data event occurs at which point heartbeats will stop until the next gap in data events.


### Examples

Stream with Default Heartbeats Request:

    GET https://api.tradestation.com/v2/stream/quote/changes?heartbeat=true HTTP/1.1
    Authorization: Bearer accesstokengoeshere
    Host: api.tradestation.com

Stream with Default Heartbeats Response:

    HTTP/1.1 200 OK
    Transfer-Encoding: chunked
    Content-Type: text/plain

    {"heartbeat":1,"timestamp":"\/Date(1399398020000)\/"}
    {"heartbeat":2,"timestamp":"\/Date(1399398025000)\/"}

Stream with 8000ms Heartbeats Request:

    GET https://api.tradestation.com/v2/stream/quote/changes?heartbeat=8000 HTTP/1.1
    Authorization: Bearer accesstokengoeshere
    Host: api.tradestation.com

Stream with 8000ms Heartbeats Response:

    HTTP/1.1 200 OK
    Transfer-Encoding: chunked
    Content-Type: text/plain

    {"heartbeat":1,"timestamp":"\/Date(1399398020000)\/"}
    {"heartbeat":2,"timestamp":"\/Date(1399398028000)\/"}

Stream with Constant-style Heartbeats Request:

    GET https://api.tradestation.com/v2/stream/quote/changes?heartbeat=true&heartbeat-style=constant HTTP/1.1
    Authorization: Bearer accesstokengoeshere
    Host: api.tradestation.com

Stream with Constant-style Heartbeats Response:

    HTTP/1.1 200 OK
    Transfer-Encoding: chunked
    Content-Type: text/plain

    {"heartbeat":1,"timestamp":"\/Date(1399398020000)\/"}
    {"heartbeat":2,"timestamp":"\/Date(1399398025000)\/"}

Stream with Keepalive-style Heartbeats Request:

    GET https://api.tradestation.com/v2/stream/quote/changes?heartbeat=true&heartbeat-style=keepalive HTTP/1.1
    Authorization: Bearer accesstokengoeshere
    Host: api.tradestation.com

Stream with Keepalive-style Heartbeats Response:

    HTTP/1.1 200 OK
    Transfer-Encoding: chunked
    Content-Type: text/plain

    {"heartbeat":1,"timestamp":"\/Date(1399398020000)\/"}
    {"heartbeat":2,"timestamp":"\/Date(1399398025000)\/"}
	{...quote change...}
	{...quote change...}
	{...quote change...}
	{"heartbeat":3,"timestamp":"\/Date(1399398045000)\/"}
	{"heartbeat":4,"timestamp":"\/Date(1399398050000)\/"}

