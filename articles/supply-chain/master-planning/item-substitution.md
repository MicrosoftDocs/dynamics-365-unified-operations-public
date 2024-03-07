---
title: Authorize an adjusted forecast
description: Not all forecast data must be authorized immediately. This article explains how you can specify the period that a forecast is authorized for. It also explains how you can authorize the forecast for specific companies and forecast models.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: ReqDemPlanImportForecastDialog
ms.topic: how-to
ms.date: 03/07/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---


# Item substitution in planning for formulas

[!include [banner](../includes/banner.md)]

You can only use substitute materials during planning for items that use formulas, not for items that use a bill of materials (BOM).

## Example scenario

Consider the following scenario: a food manufacturing company is making an item from a formula that has 20 ingredients. One of the ingredients in the formula can be substituted by one of two other ingredients. However, because these two ingredients are more expensive than the preferred ingredient, substitution is only used when the preferred item is out of stock.

The material that can be substituted is called A, whereas the two materials tha can replace it are called B and C. Material substitution by planning is controlled by the **Plan group** and **Priority** fields on the formula lines.

For example, you could create formula lines for the three materials, and associated formula lines with the same plan group. In this setup, the formula line for material A has the highest priority (lowest number), the formula line for material C has the lowest priority, and the formula line for material B has a priority that is between that of the other two lines.

If you have a demand of the finished item, master planning determines whether the demand for material A can be covered. If the demand can't be covered, master planning looks at materials B and C, in order of priority. If material B is on hand, it will be used after a batch order is firmed for the formula. If none of the materials are on-hand, it will create a planned order for material A.

> [!NOTE]
> When you set up formula lines in a plan group, you should only specify a quantity for the material that has the highest priority. This quantity will then be used to calculate the demand of all the materials in the plan, including the materials that have the lower priority. You can't specify a different quantity on the lower-priority items in the plan group. The quantities for the substitute items should be zero.

## Prerequisites



## Set up item substitution

<!-- KFM: Instructions needed -->

## Shelf life and item substitution

When using material substitution with products that have a limited shelf-life, master planning always ensures that the shelf life of each substitute is also respected.

For example, a formula item could be set up as follows:

- **Ingredient A:**
    - Quantity: 10
    - Priority: 1
    - Plan group: Organic oils
    - Available on-hand: 4, with expiry date of today + 5 days
- **Ingredient B (Substitute for ingredient A):**
    - Priority 2
    - Plan group: Organic oils
    - Available on-hand: 6
    - Expected receipt date: Today + 6 days and negative days = 10 days

Master planning first picks ingredient A with its available quantity 4. Because the required quantity is 10, and there is not enough of ingredient A, master planning will try to use the substitute (ingredient B) for the remaining quantity of 6. However, because the available receipt date of the substitute is later than the expiry date of the on-hand inventory of ingredient A, the substitute won't be used. Instead, master planning creates a planned order for quantity 6 of ingredient A to fulfill the rest of the material needed. <!--KFM: Don't we need to know the expected receipt date of ingredient A in order for this to work? -->

## Enable item substitution

Enable the feature on feature management *Item substitution (plan group) support for Planning Optimization, available on release 10.0.40
