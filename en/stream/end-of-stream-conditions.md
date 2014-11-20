---
layout: en
title: End of Stream Conditions
category: stream
permalink: end-of-stream-conditions/
weight: 4
---

### Summary

The streaming API methods behave differently than the other API calls due to the long-lived nature of the response.  While the non-streaming methods will only return a 200 status code on success, a successful stream request does not return a status code until the stream ends, which may be minutes or hours after beginning the request.

When a streaming API is requested, it will either succeed and begin streaming data or fail just like a normal API method.  When a stream starts successfully, the status code will eventually be a 200 Success once the stream ends.  However, if the stream starts successfully but fails after streaming has begun, then the behavior is different.

Whenever a stream ends for any reason, it will return a 200 status code followed by a data chunk containing either the word `END` or `ERROR` prefix.   The word `END` signifies that the stream intentionally ended due to it reaching the end of the requested set of data such as when a date-range or finite amount of data was requested.  The word `ERROR` indicates that the stream failed due to an abnormal condition after the stream was successfully established.  The word `ERROR` will preceed a message containing the reason.  See below for examples of these Error Reasons.

`warning:` If for some reason a stream ends without one of these words, then it must be treated as a disconnect or abnormal end.   

### Error Reasons

* `NO DATA AVAILABLE` | You requested data for a date range where there is no data available.
* `NOT ENTITLED` | Your user does not have the required entitlements to access this type of data.
* `INVALID SYMBOL` | The symbol you used was invalid or not found.

### Examples

Stream END Example Request:

    GET https://api.tradestation.com/v2/stream/barchart/spy/1/minute/1/06-13-2013 HTTP/1.1
    Authorization: Bearer accesstokengoeshere
    Host: api.tradestation.com

Stream END Example Response:

    HTTP/1.1 200 OK
    Transfer-Encoding: chunked
    Content-Type: text/plain

    {
        "Close": 161.98,
        "DownTicks": 755,
        "DownVolume": 250102,
        "High": 162.0,
        "Low": 161.92,
        "Open": 161.94,
        "Status": 13,
        "TimeStamp": "\/Date(1371066960000)\/",
        "TotalTicks": 1741,
        "TotalVolume": 604346,
        "UnchangedTicks": 0,
        "UnchangedVolume": 0,
        "UpTicks": 986,
        "UpVolume": 354244,
        "OpenInterest": 0
    }
    END

Stream ERROR Example Request:

    GET https://api.tradestation.com/v2/stream/barchart/msft/1/minute/06-13-1951 HTTP/1.1
    Authorization: Bearer accesstokengoeshere
    Host: api.tradestation.com

Stream ERROR Example Response:

    HTTP/1.1 200 OK
    Transfer-Encoding: chunked
    Content-Type: text/plain

    ERROR - NO DATA AVAILABLE

