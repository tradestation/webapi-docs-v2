---
layout: en
title: Position Group
category: objects
permalink: position-group/
---

| Field                 | Type    | Description |
| --------------------- | ------- | ----------- |
| GroupId				| long    | Position Group key |
| AccountId             | string  | Account Identifier |
| Symbol				| string  | Symbol Name for Position Group |
| ExchangeCode			| string  | Abbreviated Exchange Name identifier |
| AssetType				| string  | Classification of Symbol by type of security (EQ,OP,FU,FX) | 
| FundSource			| object ([FundSource](#FundSourceObject)) | Detailed breakdown of Funding & cost of funding.  |
| TaxationMethod		| string  | Indicates any taxation attributes of this position |
| Direction				| string  | Indicates if position is Long or Short |
| CountryCode			| string  | Abbreviated country-code for position | 
| Currency 				| string  | Indicates which currency the position values represent (USD,JPY, etc) |
| TotalQuantity			| long  | Sum of all positions represented by this position group |
| AveragePrice			| decimal | The mean price of all positions that make up this position group |
| UnrealizedGainLoss			| decimal  | Aggregate unrelased gains or losses based upon current market valuation of this position group |
| UnrealizedGainLossPercent			| decimal  | Aggregate percent of unrelased gains or losses based upon current market valuation of this position group |
| MarketValue			| decimal | Aggregate value of this position group based upon the current market valuation of this position group |
| OpenDateTime			| datetime  | When this aggregate position was opened. |
| Positions				| [Position](../position) collection | Position details aggregated by this position group |

##FundSourceObject
| Field                 | Type    | Description |
| --------------------- | ------- | ----------- |
| - Type			| string ([FundSource Type](#FundSourceType))   | Indicates how position group is funded |
| - Commission			| decimal  | |
| - CommissionConsumptionTax			| decimal  | |
| - ManagementFee			| decimal  | |
| - ManagementFeeConsumptionTax			| decimal  | |
| - CorporateActionFee			| decimal  | |
| - CorporateActionFeeConsumptionTax			| decimal  | |
| - Interest			| double  | |
| - OnOrderQuantity			| double  | |
| - TotalExpenses			| decimal  | |
| - DailyLoanCharge			| decimal  | |
| - ShortStockFees			| decimal  | |
| - ShortInterest			| double  | |
| - TotalMarginExpense			| decimal  | |
| - TotalShortRebate			| decimal  | |
| - UnrealizedGainLossPerShare			| decimal  | |


##FundSourceType

* Cash
* Margin



