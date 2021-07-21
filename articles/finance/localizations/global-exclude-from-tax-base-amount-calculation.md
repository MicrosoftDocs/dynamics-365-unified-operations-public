---
# required metadata

title: Calculating tax on top of price when Prices include taxes is enabled
description: This topic provides information about the functionality for calculating tax on top of price when Prices include taxes is enabled.
author: epodkolz
ms.date: 
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

# Calculating tax on top of price when Prices include taxes is enabled

This topic provides information about how the **Exclude from base amount calculation** parameter of a tax code in a **Tax codes** tab of a Tax feature setup works.

![Exclude from base amount calculation](https://user-images.githubusercontent.com/27483882/126526393-6f462cc7-dd1d-4f97-94c3-9ea23188f798.jpg)


The **Exclude from base amount calculation** option provides a possibility to calculate tax amounts in a flexible way. By enabling the parameter for a **Tax code**, in the scenario when prices include sales tax, the Tax calculation service will calculate tax amounts for the marked sales tax code so as if it was not included into the base amount.
The following example will demonstrate how the tax calculation happens. 
A sales tax group and an item sales tax group contain two sales tax codes and one of them is marked as **Exclude from base amount calculation**:

| Sales tax group/Item sales tax group | Tax rate | Exclude from base amount calculation |
|--------------------------------------|----------|--------------------------------------|
| **TaxCodeA** | 20 % | No |
| **TaxCodeB** | 10 % | Yes |

When a Sales order or a Purchase order is created with a **Prices include sales tax** option enabled and a line Net amount is equal to 120, the tax is calculated as follows:

|  | Tax base amount | Amount |
|--------------------------------------|----------|------------------------------------|
| **TaxCodeA** | 100 | 20 |
| **TaxCodeB** | 120 | 12 |



> [!NOTE]
> In this example, the tax code **TaxCodeA** is configured as **By Net amount**; and **TaxCodeB** is configured as **By Gross amount**.
>
> If the tax code **TaxCodeB** is configured as **By Net Amount**, then its tax base amount is equal to 100 and its tax amount is equal to 10.


