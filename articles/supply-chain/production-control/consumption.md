---
# required metadata

title: Calculate material consumption
description: This article provides information about various options that are related to the calculation of material consumption. 
author: johanhoffmann
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BOMDesignerEditBOM, BOMTable, ProdBOM
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 53401
ms.assetid: 9cff88e4-0425-4707-9178-3c2cb10df7c2
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Calculate material consumption

[!include [banner](../includes/banner.md)]

This article provides information about various options that are related to the calculation of material consumption. 

The following options that are related to the calculation of material consumption are available on the **Setup** and **Step consumption** tabs on the **Line details** FastTab of the **Bill of materials** page.

## Variable and constant consumption
In the **Consumption is** field, you can select whether consumption should be calculated as a constant quantity or a variable quantity. Select **Constant** if a fixed quantity or volume is required for the production, regardless of the quantity that is produced. Select **Variable**, which is the default setting, if the required amount of material in the finished goods is proportional to the number of finished goods that are produced.

## Calculating consumption from a formula
In the **Formula** field, you can set up various formulas for calculating material consumption. If you use the default value, **Standard**, the consumption isn't calculated from a formula. The following formulas work together with the **Height**, **Width**, **Depth**, **Density**, and **Constant** fields:

-   Height \* Constant
-   Height \* Width \* Constant
-   Height \* Width \* Depth \* Constant
-   (Height \* Width \* Depth / Density) \* Constant

## Rounding up and multiples
Together, the **Rounding up** and **Multiples** fields let you round up the material consumption value. For example, you can round up the value according to the handling unit in which the raw material is picked for production. The following options are available in the **Rounding up** field: **Quantity**, **Measurement**, and **Consumption**.

### Quantity

If you select **Quantity** as the rounding-up mechanism, the quantity must be a multiple of the specified quantity. For example, if whole numbers are required, select **1** in the **Multiples** field. Numbers are then rounded up to a quantity that is divisible by 1.

### Measurement

Typically, you select **Measurement** as the rounding-up mechanism when the raw material comes in specific dimensions. For example, a piece of 2-meter metal tube is required for a finished good, and the metal tube is stored in 4.5-meter lengths. In this case, the **Measurement** rounding-up mechanism can be used to calculate how many metal tubes are required to produce a specific number of pieces of the finished good. For this example, the **Formula** field is set to **Height \* Constant**. The **Height** field is set to **2** to indicate the length of the tube that is required for the finished good. The **Multiple** field is set to **4.5** to indicate that the tube is picked in lengths of 4.5 meters. Here is the calculation:

1.  Number of multiples that are required for 10 pieces of the finished good: 10 ÷ 2 = 5 pieces
2.  Total consumption:  4.5 × 5 = 22.5 meters of metal tube

It's assumed that 0.5 meter of tube is scrapped for every five pieces of tube that are consumed.

### Consumption

Typically, you select **Consumption** as the rounding-up mechanism when raw material must be picked in whole quantities of a specific handling unit of the product. For example, 2 quarts of paint are used to produce one piece of a finished good, and the paint is picked in 25-quart cans. In this case, the **Consumption** rounding-up mechanism can be used to round up consumption to whole numbers of 25-quart cans. Here is the calculation for the amount of paint that is required if 180 pieces of the finished good must be produced:

1.  Paint that is required, excluding scrap: 180 × 2 = 360 quarts
2.  Number of cans: 360 ÷ 25 = 14.4, which is rounded up to 15
3.  Paint that is required, including scrap: 15 × 25 = 375 quarts

## Step consumption
Step consumption is used to calculate constant consumption in quantity intervals. If you select **Step consumption** in the **Formula** field on the **Setup** tab, you can add information about the steps on the **Step consumption** tab. The fixed consumed quantity can be set up in intervals of the produced quantity. For example, step consumption is set up as shown in the following table.

| From series | Quantity |
|-------------|----------|
| 0.00        | 10.0000  |
| 100.00      | 20.0000  |
| 200.00      | 40.0000  |

The bill of materials (BOM) quantity is 1, and the production quantity is 110. The formula for the consumption is From series (Quantity) = Consumption. Because the production quantity is 110, it falls into the "From 100 series." Therefore, the quantity is 20.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]