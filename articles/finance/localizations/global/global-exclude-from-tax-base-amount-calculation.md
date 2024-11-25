---
title: Calculate tax on prices when Prices include taxes is enabled
description: Learn about the functionality for calculating tax on prices when the Prices include taxes option is enabled, including an overview on aspects of tax codes.
author: epodkolzina
ms.author: epodkolzina
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 07/28/2021
ms.reviewer: johnmichalak
ms.dyn365.ops.version: AX 10.0.21
---

# Calculate tax on prices when Prices include taxes is enabled

[!include [banner](../../includes/banner.md)]


This article provides information about how the **Exclude from base amount calculation** parameter of a tax code is used.

You can use the **Exclude from base amount calculation** parameter to calculate tax amounts in a flexible way. When this parameter is enabled for a tax code, if prices include sales tax, the Tax calculation service calculates tax amounts for the marked sales tax code as if it wasn't included in the base amount.

The following example shows how the tax calculation is done. 

A sales tax group and an item sales tax group contain two sales tax codes. The **Exclude from base amount calculation** parameter is enabled for one tax code.

| Tax code | Tax rate | Exclude from base amount calculation |
|----------|----------|--------------------------------------|
| TaxCodeA | 20% | No |
| TaxCodeB | 10% | Yes |

If a sales order or a purchase order is created where the **Prices include sales tax** option is enabled, and the net amount of a line equals 120, the tax is calculated in the following way.

| Tax code | Tax base amount | Amount |
|----------|-----------------|--------|
| TaxCodeA | 100 | 20 |
| TaxCodeB | 120 | 12 |

> [!NOTE]
> In this example, tax code TaxCodeA is configured as **By Net amount**, and tax code TaxCodeB is configured as **By Gross amount**. If tax code TaxCodeB is configured as **By Net Amount** instead, its tax base amount equals 100, and its tax amount equals 10.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
