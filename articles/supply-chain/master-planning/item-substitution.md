---
title: Item substitution for formulas
description: Learn how to set up item substitution for formulas in master planning, including an outline and process on setting up item substitution.
author: t-benebo
ms.author: benebotg
ms.topic: how-to
ms.date: 03/07/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: ReqDemPlanImportForecastDialog
---

# Item substitution for formulas and bills of materials

[!include [banner](../includes/banner.md)]

You can use substitute materials during planning for items that use formulas or bills of materials (BOMs). When you set up item substitution for a formula or BOM, you can specify a group of items that can serve as substitutes for a particular material. You can also specify the priority of each substitute material in the group. When master planning runs, it uses the preferred material if it's available. If the preferred material isn't available, master planning uses the substitute material that has the highest priority and is available. If no substitute materials are available, master planning creates a planned order for the preferred material.

## Prerequisites

Before you can use substitution in planning for formulas, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.39 or later.
- The feature that's named *Item substitution (Plan group) support for Planning Optimization* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.43, this feature is turned on by default.

Before you can use substitution in planning for BOMs, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.40 or later.
- The feature that's named *Item substitution for bill of materials in Planning optimization* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## <a name="plan-groups"></a>Set up plan groups

Before you can set up item substitution for formulas or BOMs, you must set up the plan groups that you need.

A plan group is a group of items that can be substituted for a particular material in a formula or BOM. Each plan group record establishes a name and a description, but it doesn't include any items. You assign items and their relative priorities to each plan group when you set up item substitution for a specific formula or BOM. You can reuse plan groups across multiple formulas and/or BOMs.

To set up plan groups, follow these steps.

1. Go to **Product information management** \> **Setup** \> **Bills of materials and formulas** \> **Plan groups**.
1. Use the buttons on the Action Pane to add, remove, or edit plan groups as required. For each plan group, set the following fields:

    - **Plan group** – Specify a unique name for the plan group.
    - **Description** – Enter a short description of the plan group.

1. Continue to work until you finish setting up all the plan groups that you need.
1. On the Action Pane, select **Save**.

## Item substitution for formulas

### Example scenario: Substituting ingredients in a formula

A food manufacturing company is making an item from a formula that has 20 ingredients. One of the ingredients in the formula can be replaced by one of two other ingredients. However, because those two ingredients are more expensive than the preferred ingredient, substitution is used only when the preferred ingredient is out of stock.

For this scenario, the ingredient that can be replaced (the preferred ingredient) is named *ingredient A*. The two materials that can replace it are named *ingredient B* and *ingredient C*.

To set up the substitution, create a formula line for each of the three ingredients, and associate all three lines with the same plan group. Because ingredient A is the preferred ingredient, assign it the highest priority (lowest number). Assign each of the other ingredients (ingredient B and ingredient C) a priority that matches its relative level of preference. (The higher the number, the lower the preference.)

If you have a demand for the finished item, master planning determines whether the demand for ingredient A can be covered. If it can't, master planning looks at ingredients B and C in order of priority. If one of these ingredients is on hand, it's used (according to its priority) when a batch order is firmed for the formula. If none of the ingredients are on hand, master planning creates a planned order for the preferred ingredient (ingredient A).

### Set up item substitution for formulas

Follow these steps to set up item substitution for a formula:

1. Go to **Product information management** \> **Bills of materials and formulas** \> **Formulas**.
1. Open the formula that you want to set up substitution for.
1. Find the formula line for the material that you want to be able to substitute. Set the following fields for it:

    - **Plan group** – Select the [plan group](#plan-groups) name that you want to use to identify the group of items that can serve as substitutes for this material.
    - **Priority** – Enter a number that indicates the priority of this material in the plan group. The lower the number, the higher the priority. Therefore, the most preferred material should have the lowest number.
    - **Quantity** – Specify the quantity of the preferred material that's required in the formula. This quantity applies to whichever material from the plan group is used.

1. Find or add a formula line for the lower-priority substitute material. Set the following fields for it:

    - **Plan group** – Select the same plan group name that you selected for the preferred material.
    - **Priority** – Enter a number that indicates the priority of this material in the plan group. The lower the number, the higher the priority. Each material in the plan group must have a unique priority number.
    - **Quantity** – Enter *0*. This field isn't used for substitutes. The quantity of the preferred material (that is, the one that has the lowest priority) defines the quantity for all the materials in the plan group.

1. Repeat the previous step for each additional substitute material.
1. Repeat this procedure for each plan group that you want to set up for the current formula.

### Shelf life and item substitution for formulas

When material substitution is used with products that have a limited shelf life, master planning always ensures that the shelf life of all materials is respected.

For example, a formula item is set up in the following way:

- **Material A:**

    - **Quantity:** 10
    - **Plan group:** Organic oils
    - **Priority:** 1
    - **Available on-hand:** 4, with an expiry date of today \+ five days
    - **Lead time:** One day

- **Material B (Substitute for material A):**

    - **Quantity:** 0
    - **Plan group:** Organic oils
    - **Priority:** 2
    - **Available on-hand:** 0
    - **Existing purchase order:** Qty 6, with an expected receipt date of today \+ six days, with 10 negative days

Master planning first selects material A, which has an available quantity of *4*. Because the required quantity is *10*, there isn't enough of material A. Therefore, master planning determines whether it can use the existing purchase order for the substitute (material B) for the remaining quantity. However, because the available receipt date of the substitute is later than the expiry date of the on-hand inventory of material A, the substitute isn't used. Instead, master planning creates a planned order for a quantity of *6* of material A to fulfill the remaining material that's required.

## Item substitution for BOMs

### Example scenario: Substituting components in a BOM

A manufacturing company is making an item from a BOM that has 20 components. One of the components in the BOM can be replaced by other components. It can even be replaced by the same item under a different item number.

For this scenario, the material that can be replaced (the preferred component) is named *material A*. The two materials that can replace it are named *material B* and *material C*.

To set up the substitution, create a BOM line for each of the three materials, and associate all three lines with the same plan group. Because material A is the preferred material, assign it the highest priority (lowest number). Assign each of the other materials (material B and material C) a priority that matches its relative level of preference. (The higher the number, the lower the preference.)

If you have a demand for the finished item, master planning determines whether the demand for material A can be covered. If it can't, master planning looks at materials B and C in order of priority. If one of these materials is on hand, it's used (according to its priority) when a batch order is firmed for the BOM. If none of the materials are on hand, master planning creates a planned order for the preferred material (material A).

### Set up item substitution for BOMs

Follow these steps to set up item substitution for a BOM.

1. Go to **Product information management** \> **Bills of materials and formulas** \> **Bill of materials**.
1. Open the BOM that you want to set up substitution for.
1. Find the BOM line for the material that you want to be able to substitute. Set the following fields for it:

    - **Plan group** – Select the [plan group](#plan-groups) name that you want to use to identify the group of items that can serve as substitutes for this material.
    - **Priority** – Enter a number that indicates the priority of this material in the plan group. The lower the number, the higher the priority. Therefore, the most preferred material should have the lowest number.
    - **Quantity** – Specify the quantity of the preferred material that's required in the BOM. This quantity applies to whichever material from the plan group is used.

1. Find or add a BOM line for the lower-priority substitute material. Set the following fields for it:

    - **Plan group** – Select the same plan group name that you selected for the preferred material.
    - **Priority** – Enter a number that indicates the priority of this material in the plan group. The lower the number, the higher the priority. Each material in the plan group must have a unique priority number.
    - **Quantity** – Enter *0*. This field isn't used for substitutes. The quantity of the preferred material (that is, the one that has the lowest priority) defines the quantity for all the materials in the plan group.

1. Repeat the previous step for each additional substitute material.
1. Repeat this procedure for each plan group that you want to set up for the current BOM.
