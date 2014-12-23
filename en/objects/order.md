---
layout: en
title: Order
category: objects
permalink: order/
---

| Field | Type | Description |
| ----- | ---- | ----------- |
| OrderConfirmId | string | 25-char max. Must be unique id per order per API Key and User |
| AccountId | string | Id of the account used to place the order |
| Symbol | string | Stock Symbol |
| Quantity | string | Number of stocks|
| AssetType | enum | Equity, Option, Future, Forex |
| LimitPrice | decimal |  |
| StopPrice | decimal | |
| Type | enum | Market, Limit, StopLimit, StopMarket |
| Route | string | |
| TimeInForce | enum | Day, DayPlus, GoodTillCancel, GoodTillCancelPlus, GoodTillDate, GoodTillDatePlus, GoodTill1Week, GoodTill1Month, GoodTill1Minute, GoodTill3Minute, GoodTill5Minute, GoodTillCrossing, ImmediateOrCancel, FillorKill, AtTheOpening, AtTheClose, AMOnly, PMOnly  |
| TimeInForceExpiration | date | DateTime with UTC offset |
| Side | enum | Buy, Sell, Short, SellShortExempt, BuyToOpen, BuyToClose, Genbiki, Genwatashi |
| FundSource | enum | Cash, Margin, StandardMargin, NegotiatedMargin |
| TaxationMethod | string | Delayed, Calculated |
| LotSelectionStrategy | enum | FirstInFirstOut, LastInFirstOut |
| Condition | enum | Basic, OrderSendOrder, OrderCancelOrder, Bracket  |

### Example JSON

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
    