---
title: Item substitution for formulas
description: This article describes how to set up item substitution for formulas in master planning.
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

Consider the following scenario: a food manufacturing company is making an item from a formula that has 20 ingredients. One of the ingredients in the formula can be substituted by one of two other ingredients. However, because these two ingredients are more expensive than the preferred ingredient, substitution is only used when the preferred item is out of stock. The material that can be substituted is called A, whereas the two materials that can replace it are called B and C.

To set up the substitution, you create a formula line for each of the three ingredients, and associate each of these lines with the same plan group. Because ingredient A is the preferred choice, you would assign it the highest priority (lowest number). Ingredients B and C would be assigned priorities to match their relative preferences (the higher the number, the lower the preference).

If you have a demand for the finished item, master planning determines whether the demand for material A can be covered. If the demand can't be covered, master planning looks at materials B and C, in order of priority. If one of these ingredients is on hand, that ingredient is used (following its priority) when a batch order is firmed for the formula. If none of the materials are on-hand, master planning creates a planned order for the preferred ingredient (ingredient A).

## Prerequisites

To use substitution in planning for formulas, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.39 or later.
- The feature that is named *Item substitution (Plan group) support for Planning Optimization* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up item substitution

Follow these steps to set up item substitution for a formula:

1. Go to **Product information management \> Bills of materials and formulas \> Formulas**.
1. Open the formula that you want to set up substitution for.
1. Find the formula line for the material that you want to substitute. Make the following settings for it.
    - **Plan group** – Enter a locally unique name that identifies the group of items that could serve as substitutes for this material.
    - **Priority** – Enter a number that indicates the priority of this material in the plan group. The lower the number, the higher the priority. The most preferred material should have the lowest number.
1. Find or add a formula line for the lower-priority substitute material. Make the following settings for it.
    - **Plan group** – Enter the same name that you entered for the preferred material.
    - **Priority** – Enter a number that indicates the priority of this material in the plan group. The lower the number, the higher the priority. Each material in the plan group must have a unique priority number.
    - **Quantity** – Enter 0. This field isn't used for substitutes. The quantity of the preferred material (the one with the lowest priority) specifies the quantity for any of the materials in the plan group.
1. Repeat the previous step for each substitute material.

## Shelf life and item substitution

When using material substitution with products that have a limited shelf-life, master planning always ensures that the shelf life of all materials is respected.

For example, a formula item could be set up as follows:

- **Material A:**
    - Quantity: 10
    - Plan group: Organic oils
    - Priority: 1
    - Available on-hand: 4, with expiry date of today + 5 days
    - Lead time: 1 day
- **Material B (Substitute for material A):**
    - Quantity: 0
    - Plan group: Organic oils
    - Priority: 2
    - Available on-hand: 0
    - Existing purchase order: Qty 6, with an expected receipt date of today + 6 days, with 10 negative days

Master planning first selects material A with its available quantity 4. Because the required quantity is 10, and there isn't enough of material A, so master planning checks to see if it can use the existing purchase order for the substitute (material B) for the remaining quantity. However, because the available receipt date of the substitute is later than the expiry date of the on-hand inventory of material A, the substitute won't be used. Instead, master planning creates a planned order for quantity 6 of material A to fulfill the rest of the material needed.
