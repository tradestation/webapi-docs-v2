---
layout: en
title: Order Detail
category: objects
permalink: order-detail/
tags: SCKS
---

| Field | Type | Description | Brand |
| ----- | ---- | ----------- | ----- |
| Id | integer | Key for identifying this order | |
| AccountID | string | The account for which this order was placed | |
| AssetType | string | | |
| Side | string | Buy, Sell, Short, SellShortExempt, BuyToOpen, BuyToClose, Genbiki, Genwatashi | |
| Symbol | string | Exchange symbol for this transaction | |
| Quantity | integer | Quantity of shares in the order | |
| Type | string | | |
| LimitPrice | decimal | LimitPrice with decimal precision applied | |
| StopPrice | decimal | StopPrice with decimal precision applied | |
| TimeInForce | string | | |
| FundSource | string | | |
| TaxationMethod | string | Tokutei, Non-Tokutei, Undefined | JPEQ |
| OriginatorId | string | FDCN Id of the user that placed the order | |
| Commission | decimal | Commissions charged for this order | |
| CountryCode | string | The Country Code this order was placed in | |
| CreatedDateTime | string, YYYY-MM-DD hh:mm:ss.ttt | Time in UTC/GMT that order was placed | |
| ExecutedDateTime | string, YYYY-MM-DD hh:mm:ss.ttt | Time in UTC/GMT that order was placed | |
| ExchangeDateTime | string, YYYY-MM-DD hh:mm:ss.ttt | Time in UTC/GMT that order was placed | |
| ExchangeCode | string | | |
| Status | string | Status of Order, [described below](#order_status_categories) | |
| ExecuteQuantity | integer | Quantity executed for order | |
| RemainingQuantity | integer | Quantity remaining to be filled to statisfy order | |
| AverageExecutedPrice | decimal | FilledPrice with decimal precision applied | |
| [Quote](../../objects/quote) | Quote | | |
| - PreviousClose | decimal | Previous day’s close price | |
| - PreviousCloseDelta | decimal | Previous day’s close price | |
| - PreviousCloseDeltaPercent | decimal | Previous day’s close price | |
| - Last | decimal | Last traded price | |
| - Ask | decimal | Ask price | |
| - Bid | decimal | Bid price | |
| - Symbol | string | Symbol name | |
| - Description | string | | &nbsp; |

### Order Status Categories

| TRANSTYPE_ID | DESCRIPTION |
| ------------ | ----------- |
| ACK | Order acknowledged by exchange |
| CAN | Order cancelled (see MESSAGE) |
| EXP | Order expired - time constraint |
| FLL | Order executed in full |
| FLP | Partial fill - order complete |
| FPR | Partial fill - still alive |
| REJ | Order rejected (never accepted by exchange) |
| RJC | Cancel request rejected |
| RJR | Cancel request rejected |