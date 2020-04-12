---
# required metadata

title: Prepare to maintain standard costs for manufactured items
description: This topic describes the steps for preparing to maintain costs for manufactured items. 
author: AndersGirke
manager: tfehr
ms.date: 01/17/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventStdCostConv 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.industry: Manufacturing 
ms.author: aevengir
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---


# Prepare to maintain standard costs for manufactured items

[!include [banner](../includes/banner.md)]

This topic describes the steps for preparing to maintain costs for manufactured items. The steps for manufactured items differ slightly from the steps for purchased items.

Policies that are assigned to manufactured items can affect the cost calculations for the parent manufactured items. To prepare to maintain costs for manufactured items, follow these steps.

1. Assign an item model group to the manufactured item. 

   The item model group identifies that standard costs will be used.

2. Assign an item group to the manufactured item. 

   The item group contains ledger accounts that apply to the manufactured item. The ledger accounts for a manufactured item that has a standard cost inventory model include several production variances, the cost change variance, and the inventory cost revaluation.

3. Assign the inventory unit of measure to the item. 

   The item's costs are always expressed in the item's inventory unit of measure.

4. Don't assign a cost group to the manufactured item unless the item will be treated as a purchased item.

5. Assign a bill of materials (BOM) calculation group to the manufactured item. 

   The item's BOM calculation group defines warning conditions that apply. In that way, when a BOM calculation is done, warning messages can be generated about possible sources of calculation errors. For example, a warning message can identify when an active BOM or route doesn't exist. The BOM calculation group contains a stop explosion policy that indicates when a manufactured item should be treated as a purchased item.

6. If the manufactured item has constant costs, assign a standard order quantity to it. 

   The standard order quantity is an accounting lot size for amortizing constant costs. Examples of constant costs include setup times in routing operations and a constant component quantity in the BOM.

7. Define the BOM for the manufactured item. 

   One or more BOM versions can be defined for the manufactured item. Verify that the versions that you want have been marked as approved and active, and that they have the effective dates that you want. The BOM version can be company-wide or site-specific.

8. Define the routing for the manufactured item. 

   One or more route versions can be defined for the manufactured item. Verify that the versions that you want have been marked as approved and active, and that they have the effective dates that you want. The route version must be site-specific.

If you want to use routing information for costing purposes, additional preparation steps are required. For example, the cost categories that are assigned to routing operations must be correct and completed.

Related topics
--------

[Amortize constant costs for a manufactured item](amortize-constant-costs-manufactured-item.md)

[Set up products that can be produced or procured](manufactured-items-treated-as-purchased-items.md)

