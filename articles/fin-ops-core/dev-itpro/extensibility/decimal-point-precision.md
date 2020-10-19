---
# required metadata

title: Extending decimal point precision for selected data types
description: This topic describes how to extend decimal point precision for selected data types.
author: LarsBlaaberg
manager: 
ms.date: 09/24/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
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

[!include [banner](../includes/banner.md)]

This topic describes how to extend decimal point precision for selected data types. You can create extensions of specific extended data types of the type Real, to change the decimal point precision for certain scenarios. To change the decimal point precision, change the **NoOfDecimals** property as needed.

Extended data types are hierarchical and inherit behavior from the data type they extend. When changing the number of decimals for one extended data type, the number of decimals on all derived extended data types will follow. In other words, if you find an extended data type where **NoOfDecimalsIsExtensible** is false, then check the parent extended data type, as the number of decimals might be extensible in this wider scope.

## Weight
Weight data can be maintained with a maximum of two decimals by default. 
If you require the ability to enter, maintain, and view weight data with a maximum precision of six decimals, you must extend the decimal point precision for the **WeightBase** extended data type.

## Product width, height and depth
These physical dimensions can be maintained with a maximum of two decimals by default. 
If you require the ability to enter, maintain, and view this data with a maximum precision of six decimals, you must extend the decimal point precision for the **InventWidth**, **InventHeight**, and **InventDepth** extended data types respectively.

## Product quantity
Quantity data that is related to the procuring, consuming, producing, storing, and selling of products can be maintained with a maximum of two decimals by default.
If you require the ability to enter, maintain, and view product quantities with a maximum precision of six decimals points, you must extend the decimal point precision of the **ProductQuantity**, **CostQuantity**, and **CAMMagnitude** extended data types.

Bill of materials, formulas, and production orders allow maintaining quantities with four decimals by default. 
If you require more than four decimals, extend the decimal point precision for the **BOMProductQuantity** extended data type.

### Related data types
**Price unit**, **Price quantity**, and **Charge quantity data** can be extended independently from product quantities.
You can extend the **PriceUnit** extended data type to change the decimal point precision to a value other than the default two for price units.

You can extend the **PriceQty** extended data type to change the decimal point precision to a value other than the default two for price and charge quantities.

### Overloaded data types
There are two extended data types that are used for storing both quantity data and other types of data. These data types must be extended separately.

The **AmountQty** extended data type is used for storing and presenting both amounts and quantities. The **AmountQty** extended data type should be extended to the maximum amount of required decimals for both amounts and quantities. 
For example, if amounts need to be maintained with three decimal points, but quantities still need to be maintained with two decimal points, then the data type should be extended to three decimal points.

The **ProductQuantityHourValue** extended data type is used for storing and presenting both hours and quantities. The **ProductQuantityHourValue** extended data type should be extended to the maximum amount of required decimal points for both hours and quantities.
For example, if quantities need to be maintained with four decimal points, but hours still need to be maintained with two decimal points, then the data type should be extended to four decimal points.


## Unit amounts
By default, unit amounts including prices, line discount amounts, and line charge amounts can be maintained with a maximum of two decimals.

If you require the ability enter, maintain, and view unit amounts with a maximum precision of six decimal points, you must extend the decimal point precision of the **UnitAmountCur**, **UnitAmountMST**, and **CostPriceNonMonetary** extended data types.

If you require a decimal point precision of more than four, you should also extend the PriceRoundOff extended data type.

### Overloaded data types
There are five extended data types that are used for storing both unit amount data and other types of data.

The **PriceDiscAmount** extended data type is used for storing and presenting amounts and unit amounts. The **PriceDiscAmount** extended data type should be extended to the maximum amount of required decimals points for both amounts and unit amounts.
For example, if amounts need to be maintained with three decimal points, but unit amounts need to be maintained with four decimal points, the data type should be extended to four decimal points.

The **MCRRoyaltyValue**, **PdsRebateValue**, **TAMRebateValue**, and **MarkupValue** extended data types are used for storing and presenting amounts, unit amounts, and percentages.
The extended data types should be extended to the maximum amount of required decimal points for amounts, unit amounts, and percentages. For example, if amounts need to be maintained with three decimal points, but unit amounts need to be maintained with four decimal points and percentages should remain maintained with two decimal points, then the data type should be extended to four decimal points.

## Amounts
Amounts, including unit amounts, can be maintained with a maximum of two decimals by default.

If you require the ability to enter, maintain, and view amounts including unit amounts with a precision of maximum six decimal points, you must extend the decimal point precision of the **Amount**, **AmountMST**, and **CostAmountNonMonetary** extended data types.
If you require a different precision for unit amounts other than for amount, follow the description for how to extend the decimal point precision for unit amounts.

### Overloaded data types
There are three extended data types that are used for storing amount data and other types of data. This means that they must be extended separately.

The **AmountQty** extended data type is used for storing and presenting amounts and quantities. The **AmountQty** extended data type should be extended to the maximum amount of required decimals for both amounts and quantities. 
For example, if amounts need to be maintained with three decimal points, but quantities still need to be maintained with two, then the data type should be extended to three decimal points.

The **PriceDiscAmount** extended data type is used for storing and presenting amounts and unit amounts. The **PriceDiscAmount** extended data type should be extended to the maximum amount of required decimals points for amounts and unit amounts.
For example, if amounts need to be maintained with three decimal points, but unit amounts need to be maintained with four decimal points, then the data type should be extended to four decimal points.

The **MarkupValue** extended data type is used for storing and presenting amounts, unit amounts, and percentages.
The extended data types should be extended to the maximum amount of required decimals points for amounts, unit amounts, and percentages.
For example, if amounts need to be maintained with three decimal points, unit amounts need to be maintained with four decimal points, and percentages should remain with two decimal points, then the data type should be extended to four decimal points.
