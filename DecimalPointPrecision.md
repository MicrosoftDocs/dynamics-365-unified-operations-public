---
# required metadata

title: Extending decimal point precision for selected data types
description: This topic describes how to extend decimal point precision for selected data types.
author: LarsBlaaberg
manager: 
ms.date: 10/10/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 8DA4DA85-0C2D-4CAF-B350-DAC9C1BE4DF9
ms.search.region: Global
# ms.search.industry: 
ms.author: lolsen
ms.search.validFrom: 2018-10-10
ms.dyn365.ops.version: Platform update 21
---

# Extending decimal point precision for selected data types

You can create extensions of specific extended data types of type Real, to change the decimal point precision for the scenarios listed here:

## Weight
Weight data can be maintained with a maximum of two decimals by default.
If you require the ability to enter, maintain and view weight data with a precision of maximum 6 decimals, then you need to extend the decimal point precision for the **WeightBase** extended data type.

## Product Quantity
Quantity data related to the procuring, consuming, producing, storing, and selling products can be maintained with a maximum of two decimals by default.
If you require the ability to enter, maintain and view product quantites with a precision of maximum 6 decimals points, then you need to extend the decimal point precision of the **ProductQuantity, CostQuantity, and CAMMagnitude** extended data types.

Bill of materials, formulas, and production orders allows maintaining quantities with 4 decimals by default. 
If you require more than 4 decimals, then you need to extend the decimal point precision for the **BOMProductQuantity** extended data type.

### Related data types
Price unit as well as Price quantity and Charge quantity data can be extended independently from product quantities.
You can extend the **PriceUnit** extended data type to change the decimal point precision to another value than the default 2 for price units.
You can extend the **PriceQty** extended data type to change the decimal point precision to another value than the default 2 for price and charge quantities.

### Overloaded data types
There are two extended data types which are used for storing both quantity data and other types of data.
These therefore need to be extended separately.

The **AmountQty** extended data type is used for storing and presenting both amounts and quantities. The AmountQty extended data type should therefore be extended to the maximum amount of required decimals for both amounts and quantities. 
For example, if amounts need to be maintained with 3 decimal points, but quantities still need to be maintained with 2 decimal points, then the data type should be extended to 3 decimal points.

The **ProductQuantityHourValue** extended data type is used for storing and presenting both hours and quantities. The ProductQuantityHourValue extended data type should therefore be extended to the maximum amount of required decimal points for both hours and quantities.
For example, if quantities need to be maintained with 4 decimal points, but hours still need to be maintained with 2 decimal points, then the data type should be extended to 4 decimal points.


## Unit amounts
Unit amounts like prices, line discount amounts, and line charge amounts can be maintained with a maximum of two decimals by default.

If you require the ability enter, maintain, and view unit amounts with a precision of maximum 6 decimal points, then you need to extend the decimal point precision of the **UnitAmountCur, UnitAmountMST, and CostPriceNonMonetary** extended data types.

If you require a decimal point precision of more than 4, then you should also extend the PriceRoundOff extended data type.

### Overloaded data types
There are 5 extended data types which are used for storing both unit amount data and other types of data.

The **PriceDiscAmount** extended data type is used for storing and presenting both amounts and unit amounts. The PriceDiscAmount extended data type should therefore be extended to the maximum amount of required decimals points for both amounts and unit amounts.
For example, if amounts need to be maintained with 3 decimal points, but unit amounts need to be maintained with 4 decimal points, then the data type should be extended to 4 decimal points.

The **MCRRoyaltyValue, PdsRebateValue, TAMRebateValue,** and **MarkupValue** extended data types are used for storing and presenting both amounts, unit amounts and percentages.
The extended data types should therefore be extended to the maximum amount of required decimals points for amounts, unit amounts, and percentages
For example, if amounts need to be maintained with 3 decimal points, but unit amounts need to be maintained with 4 decimal points and percentages should remain maintained with 2 decimal points, then the data type should be extended to 4 decimal points.


## Amounts
Amounts including unit amounts can be maintained with a maximum of two decimals by default.

If you require the ability to enter, mantain and view amounts including unit amounts with a precision of maximum 6 decimal points, then you need to extend the decimal point precision  of the **Amount, AmountMST, and CostAmountNonMonetary** extended data types.
If you require a different precision for unit amounts than for amount, then you need to follow the description for how to extended the decimal point precision for unit amounts.

### Overloaded data types
There are three extended data types which are used for storing both amount data and other types of data.
These therefore need to be extended separately.

The **AmountQty** extended data type is used for storing and presenting both amounts and quantities. The AmountQty extended data type should therefore be extended to the maximum amount of required decimals for both amounts and quantities. 
For example, if amounts need to be maintained with 3 decimal points, but quantities still need to be maintained with 2 decimal points, then the data type should be extended to 3 decimal points.

The **PriceDiscAmount** extended data type is used for storing and presenting both amounts and unit amounts. The PriceDiscAmount extended data type should therefore be extended to the maximum amount of required decimals points for both amounts and unit amounts.
For example, if amounts need to be maintained with 3 decimal points, but unit amounts need to be maintained with 4 decimal points, then the data type should be extended to 4 decimal points.

The **MarkupValue** extended data type is used for storing and presenting both amounts, unit amounts and percentages.
The extended data types should therefore be extended to the maximum amount of required decimals points for amounts, unit amounts, and percentages
For example, if amounts need to be maintained with 3 decimal points, unit amounts need to be maintained with 4 decimal points and percentages should remain maintained with 2 decimal points, then the data type should be extended to 4 decimal points.
