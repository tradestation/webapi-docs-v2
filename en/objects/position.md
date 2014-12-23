---
layout: en
title: Position
category: objects
permalink: position/
---

| Field                 | Type    | Description |
| --------------------- | ------- | ----------- |
| Id                    | long    | The positions unique identifier |
| AccountId             | string  | The unique identifier for the account holder |
| AccountDisplayName    | string  | The unique identifier for the account holder |
| AssetType             | enum    | Asset type: Equity, Option, Future, Forex |
| ExchangeCode          | string  | Exchange Code |
| TaxationMethod        | enum    | Taxation Method Type e.g. Delayed, Calculated |
| Direction             | enum    | Position Direction Type e.g. Long, Short |
| CountryCode           | string  | Country the position and exchange originate |
| Currency              | string  | Denomination that symbol trades in |
| TotalQuantity         | decimal | Quantity of shares held in position |
| AveragePrice          | decimal | Average Price of position held |
| UnrealizedGainLoss    | decimal | Unrealized Gain or Loss |
| UnrealizedGainLossPercent       | decimal | Unrealized Gain or Loss Precentage |
| MarketValue           | decimal | Total Market Value of held position |
| OpenDateTime          | datetime | Open date time with UTC offset |
| Quote                 | [Quote](../quote) | Data object with quote properties |
| FundSource            | [Fund Source](../fund-source) | Data object with fund source properties |

