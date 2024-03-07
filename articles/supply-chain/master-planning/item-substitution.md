---
title: Item substitution for formulas
description: This articles describes how to set up item substitution for formulas in master planning.
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

# Item substitution for formulas

[!include [banner](../includes/banner.md)]

You can only use substitute materials during planning for items that use formulas, not for items that use a bill of materials (BOM).

Consider the following scenario: a food manufacturing company is making an item from a formula that has 20 ingredients. One of the ingredients in the formula can be substituted by one of two other ingredients. However, because these two ingredients are more expensive than the preferred ingredient, substitution is only used when the preferred item is out of stock. The material that can be substituted is called A, whereas the two materials tha can replace it are called B and C.

To set up the substitution, you create a formula line for each of the three ingredients, and associate each of these lines with the same plan group. Because ingredient A is the preferred choice, you would assign it the highest priority (lowest number). Ingredients B and C would be assigned priorities to match their relative preferences (the higher the number, the lower the preference).

If you have a demand for the finished item, master planning determines whether the demand for material A can be covered. If the demand can't be covered, master planning looks at materials B and C, in order of priority. If one of these ingredients is on hand, that ingredient is used (following its priority) when a batch order is firmed for the formula. If none of the materials are on-hand, master planning creates a planned order for the preferred ingredient (ingredient A).

## Prerequisites

To use substitution in planning for formulas, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 or later.
- The feature that is named *Item substitution (Plan group) support for Planning Optimization* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up item substitution

<!-- KFM: Instructions needed. Here is my guess, please review! -->
Follow these steps to set up item substitution for a formula:

1. Go to **Product information management \> Bills of materials and formulas \> Formulas**.
1. Open the formula that you want to set up substitution for.
1. Find the formula line for the material that you want to substitute. Make the following settings for it:
    - **Plan group** – Enter a locally unique name that identifies the group of items that could serve as substitutes for this material.
    - **Priority** – Enter a number that indicates the priority of this material in the plan group. The lower the number, the higher the priority. The most preferred material should have the lowest number. <!--KFM: *Must* it be zero for the preferred material? Or does whatever one is lowest count as the preferred material (which establishes the qty). Or maybe we should recommend using zero either way?  -->
1. Find or add a formula line for the lower-priority substitute material. Make the following settings for it:
    - **Plan group** – Enter the same name that you entered for the preferred material.
    - **Priority** – Enter a number that indicates the priority of this material in the plan group. The lower the number, the higher the priority. Each material in the plan group must have a unique priority number.
    - **Quantity** – Enter 0. This field is not used for substitutes. The quantity of the preferred material (the one with the lowest priority <!--KFM: Or zero priority? -->) specifies the quantity for any of the materials in the plan group.
1. Repeat the previous step for each substitute material.

## Shelf life and item substitution

When using material substitution with products that have a limited shelf-life, master planning always ensures that the shelf life of each substitute is also respected.

For example, a formula item could be set up as follows:

- **Material A:**
    - Quantity: 10
    - Plan group: Organic oils
    - Priority: 1
    - Available on-hand: 4, with expiry date of today + 5 days
- **Material B (Substitute for material A):**
    - Quantity: 0
    - Plan group: Organic oils
    - Priority 2
    - Available on-hand: 6
    - Expected receipt date: Today + 6 days, with 10 negative days

Master planning first picks material A with its available quantity 4. Because the required quantity is 10, and there is not enough of material A, master planning will try to use the substitute (material B) for the remaining quantity of 6. However, because the available receipt date of the substitute is later than the expiry date of the on-hand inventory of material A, the substitute won't be used. Instead, master planning creates a planned order for quantity 6 of material A to fulfill the rest of the material needed. <!--KFM: Don't we need to know the expected receipt date of material A in order to know whether we need to order 6 or 10 of them? Does Item B have no expiry date? How are the negative days relevant? -->
