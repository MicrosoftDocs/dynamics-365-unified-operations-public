---
# required metadata

title: Calculate tax on prices when Prices include taxes is enabled
description: This topic provides information about the functionality for calculating tax on prices when the Prices include taxes option is enabled.
author: epodkolz
ms.date: 07/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region:
# ms.search.industry: 
ms.author: epodkolz
ms.search.validFrom:
ms.dyn365.ops.version: AX 10.0.21
---

# Calculate tax on prices when Prices include taxes is enabled

[!include [banner](../includes/banner.md)]


This topic provides information about how the **Exclude from base amount calculation** parameter of a tax code is used.

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

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
