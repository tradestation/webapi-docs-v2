---
layout: en
title: Order Response
category: objects
permalink: order-result/
---

| Field       | Type   | Description |
| ----------- | ------ | ----------- |
| OrderConfirmId     | guid | Unique id per order per API Key and User |
| Id     | int | Order ID |
| Status | enum | Success, Failed |
| Message     | string | Message string returned from orders service |
| Orders     | OrderResponse | Collections of related orders response |
