---
layout: en
title: Account Info
category: objects
permalink: account-info/
---

| Field | Type | Description |
| ----- | ---- | ----------- |
| Id | string |  Unique identifier for an account |
| AccountDisplayName | string | Account Name |
| Status | enum | Open, Close |
| Restrictions | enum | Restrictions applicable to this account e.g. MarginCall, LiquidatingTransactionOnly, ClosingTransactionOnly, NintyDaysClosingTransactionOnly |
| AllowedFundSources | enum | Fund sources the account is allowed to use e.g. Cash, Margin, StandardMargin, NegotiatedMargin |
| AllowedAssets | enum | Assets the account is allowed to trade e.g. Equity, Option, Future, Forex |


