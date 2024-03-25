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

You can use substitute materials only during planning for items that use formulas. You can't use them during planning for items that use a bill of materials (BOM).

Consider the following scenario: A food manufacturing company is making an item from a formula that has 20 ingredients. One of the ingredients in the formula can be replaced by one of two other ingredients. However, because those two ingredients are more expensive than the preferred ingredient, substitution is used only when the preferred ingredient is out of stock.

For this scenario, the material that can be replaced (the preferred ingredient) is named ingredient A. The two materials that can replace it are named ingredient B and ingredient C.

To set up the substitution, create a formula line for each of the three ingredients, and associate all three lines with the same plan group. Because ingredient A is the preferred ingredient, assign it the highest priority (lowest number). Assign each of the other ingredients (ingredient B and ingredient C) a priority that matches its relative level of preference. (The higher the number, the lower the preference.)

If you have a demand for the finished item, master planning determines whether the demand for ingredient A can be covered. If it can't, master planning looks at ingredients B and C in order of priority. If one of these ingredients is on hand, it's used (according to its priority) when a batch order is firmed for the formula. If none of the ingredients are on hand, master planning creates a planned order for the preferred ingredient (ingredient A).

## Prerequisites

Before you can use substitution in planning for formulas, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.39 or later.
- The feature that's named *Item substitution (Plan group) support for Planning Optimization* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up item substitution

Follow these steps to set up item substitution for a formula:

1. Go to **Product information management** \> **Bills of materials and formulas** \> **Formulas**.
1. Open the formula that you want to set up substitution for.
1. Find the formula line for the material that you want to replace. Set the following fields for it:

    - **Plan group** – Enter a locally unique name that identifies the group of items that can serve as substitutes for this material.
    - **Priority** – Enter a number that indicates the priority of this material in the plan group. The lower the number, the higher the priority. Therefore, the most preferred material should have the lowest number.

1. Find or add a formula line for the lower-priority substitute material. Set the following fields for it:

    - **Plan group** – Enter the same name that you entered for the preferred material.
    - **Priority** – Enter a number that indicates the priority of this material in the plan group. The lower the number, the higher the priority. Each material in the plan group must have a unique priority number.
    - **Quantity** – Enter *0*. This field isn't used for substitutes. The quantity of the preferred material (that is, the one that has the lowest priority) defines the quantity for all the materials in the plan group.

1. Repeat the previous step for each additional substitute material.

## Shelf life and item substitution

When material substitution is used with products that have a limited shelf life, master planning always ensures that the shelf life of all materials is respected.

For example, a formula item is set up in the following way:

- **Material A:**

    - **Quantity:** 10
    - **Plan group:** Organic oils
    - **Priority:** 1
    - **Available on-hand:** 4, with an expiry date of today \+ 5 days
    - **Lead time:** 1 day

- **Material B (Substitute for material A):**

    - **Quantity:** 0
    - **Plan group:** Organic oils
    - **Priority:** 2
    - **Available on-hand:** 0
    - **Existing purchase order:** Qty 6, with an expected receipt date of today \+ 6 days, with 10 negative days

Master planning first selects material A, which has an available quantity of *4*. Because the required quantity is *10*, and there isn't enough of material A, master planning checks whether it can use the existing purchase order for the substitute (material B) for the remaining quantity. However, because the available receipt date of the substitute is later than the expiry date of the on-hand inventory of material A, the substitute isn't used. Instead, master planning creates a planned order for a quantity of *6* of material A to fulfill the remaining material that's required.
