---
layout: en
title: Content Types
category: stream
permalink: content-types/
weight: 4
---

### Summary

The streaming API methods only supports the text/plain content type with a *transfer-encoding* header value of **chunked**.   However, the actual payload of each chunk is *json* with each chunk representing a distinct *json* object.

*note:* The payload may also contain a non-json string such as `END` or `ERROR`.   See [End of Stream Conditions](end-of-stream-conditions) for more details.



