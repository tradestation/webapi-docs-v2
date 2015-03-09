---
layout: en
title: Account
category: objects
permalink: account/
---

| Field | Type | Description |
| ----- | ---- | ----------- |
| Id | string | Account Id |
| AccountDisplayName | string | Account Display Name |
| Status | enum | Current status of the account: Open, Close |
| Restrictions | enum | Restrictions applicable to this account e.g. MarginCall, LiquidatingTransactionOnly, ClosingTransactionOnly, NintyDaysClosingTransactionOnly |
| Currency | string | Currency |
| AllowedFundSources | enum | Fund sources the account is allowed to use e.g. Cash, Margin, StandardMargin, NegotiatedMargin |
| AllowedAssets | enum | Assets the account is allowed to trade e.g. Equity, Option, Future, Forex |
| MarketValue | decimal | Sum of market values for currently held positions |
| TotalUnclearedDeposits | decimal | Total funds that are not available for trading and are deducted from your account balance. |
| Equity | [Equity](../equity-account) | Data object with equity account properties |
| Option | [Option](../option-account) | Data object with option account properties |
| BODBuyingPower  | [Buying Power](../buying-power) | Data object with beginning of day Buying Power properties |
| RealTimeBuyingPower | [Buying Power](../buying-power) | Data object with real time Buying Power properties |