---
title: Calculate tax on prices when Prices include taxes is enabled
description: Learn about the functionality for calculating tax on prices when the prices include taxes option is enabled, including an overview on aspects of tax codes.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/18/2026
ms.reviewer: johnmichalak
---

# Calculate tax on prices when prices include taxes is enabled

[!include [banner](../../includes/banner.md)]

This article explains how to use the **Exclude from base amount calculation** parameter of a tax code.

Use the **Exclude from base amount calculation** parameter to calculate tax amounts in a flexible way. When you enable this parameter for a tax code and prices include sales tax, the Tax calculation service calculates tax amounts for the marked sales tax code as if it wasn't included in the base amount.

The following example shows how the tax calculation works.

A sales tax group and an item sales tax group contain two sales tax codes. The **Exclude from base amount calculation** parameter is enabled for one tax code.

| Tax code | Tax rate | Exclude from base amount calculation |
|----------|----------|--------------------------------------|
| TaxCodeA | 20% | No |
| TaxCodeB | 10% | Yes |

If you create a sales order or a purchase order where you enable the **Prices include sales tax** option, and the net amount of a line equals 120, the tax is calculated in the following way.

| Tax code | Tax base amount | Amount |
|----------|-----------------|--------|
| TaxCodeA | 100 | 20 |
| TaxCodeB | 120 | 12 |

> [!NOTE]
> In this example, tax code TaxCodeA is configured as **By Net amount**, and tax code TaxCodeB is configured as **By Gross amount**. If tax code TaxCodeB is configured as **By Net Amount** instead, its tax base amount equals 100, and its tax amount equals 10.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
