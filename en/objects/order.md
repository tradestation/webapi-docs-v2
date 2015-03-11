---
layout: en
title: Order Request
category: objects
permalink: order/
---

| Field | Type | Description |
| ----- | ---- | ----------- |
| OrderConfirmId | guid | Must be unique id per order per API Key and User |
| ClientTag | string | Optional: Client generated unique identifier |
| AccountId | string | Id of the account used to place the order |
| Symbol | string | Stock Symbol |
| Quantity | string | Number of stocks|
| AssetType | enum | Equity, Option, Future, Forex |
| LimitPrice | decimal |  |
| StopPrice | decimal | |
| Type | enum | Market, Limit, StopLimit, StopMarket |
| TimeInForce | enum | Day, DayPlus, GoodTillCancel, GoodTillCancelPlus, GoodTillDate, GoodTillDatePlus, GoodTill1Week, GoodTill1Month, GoodTill1Minute, GoodTill3Minute, GoodTill5Minute, GoodTillCrossing, ImmediateOrCancel, FillorKill, AtTheOpening, AtTheClose, AMOnly, PMOnly  |
| TimeInForceExpiration | date | DateTime with UTC offset |
| Side | enum | Buy, Sell, Short, SellShortExempt, BuyToOpen, BuyToClose, Genbiki, Genwatashi |
| ExchangeCode | enum | NYSE, NASDAQ, TS, OSE, NG, HC, FK, SP, JQ, HongKong, Shanghai, Shenzhen, ChiX, JPN, Forex, CME, GR, OutsideMarket, OtherForeignMarket |
| FundSource | enum | Cash, Margin, StandardMargin, NegotiatedMargin |
| TaxationMethod | string | Delayed, Calculated |
| CostBasisMethod | enum | FIFO, LIFO, LargestProfit, LargestLoss |
| Condition | enum | Basic, OrderSendOrder, OrderCancelOrder, Bracket  |

### Example JSON

    {
        "OrderConfirmId": "B86D7397-6B2A-4760-ADC6-A6FBA0C31470",
        "ClientTag": "OrderBar",
        "AccountId": "281994",
        "AssetType": "Equity",
        "Side": "Buy",
        "ExchangeCode": "TS",
        "TimeInForce": "DayPlus",
        "LimitPrice": "0.14",
        "Type": "Limit",
        "Quantity": 5,
        "StopPrice": 14.12,
        "Symbol": "JP:8698-TS",
        "TimeInForceExpiration": null,
        "FundSource": "Cash",
        "TaxationMethod": "Calculated",
        "CostBasisMethod" : "FIFO",
        "Condition": "Basic"
    }
    