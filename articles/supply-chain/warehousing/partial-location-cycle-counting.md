---
# required metadata

title: Partial location cycle counting 
description: Cycle count plans guide the actual counting operations. You can request that only specific products and product variants be counted instead of all on-hand inventory in a location.
author: perlynne
ms.date: 09/02/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSCycleCountPlan, WHSWorkLineCycleCount, WHSWorkTemplateLineGroup, WHSWorkTemplateTable, WHSRFMenuItemCycleCount, WHSCycleCountPlanListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Partial location cycle counting

[!include [banner](../includes/banner.md)]

Cycle count plans guide the actual counting operations. You can request that only specific products and product variants be counted instead of all on-hand inventory in a location.

By using cycle count plans to create counting work, you can guide the actual counting operations. You can request that only specific products and product variants be counted instead of all on-hand inventory in a location. By filtering on specific products, the warehouse manager can reduce review overhead, avoid consolidation mistakes, and save time.

## How to configure partial location cycle counting

When you use the warehouse work process for counting operations, a work header is created for each location. When you define the cycle count plan, you can use the **Select locations** query to limit the cycle counting work that is created. When you select products for the cycle count plan, you can select both product and product variant queries to refine what is counted.

You can associate a **work template** with a cycle count plan to define how the cycle count work should be created. The work template for counting operations is directly referenced from the cycle count plan.

When you define the work template details, you can use the **Work line breaks** option to specify whether the counting work lines must be grouped by item number or product variant number. This setup is required if you want to count on-hand inventory only for specific products in a location. The cycle counting work lines that are created will have the level of information that you define here, and the guided counting operation will be handled based on this level.

If you associate cycle count plans with work templates by using the **Work lines breaks** option, the **Partial cycle count** field is selected for the cycle counting work that is created, and multiple cycle counting work lines will be created based on the definition of the work template.

Before partial cycle count work can be processed, you must, at a minimum, select **Display item number** for the mobile device menu item as part of the cycle counting setup. The warehouse operator will be asked to record only counting information that is related to the counting lines (item numbers and product dimensions). All other on-hand inventory will be ignored for this counting process.

For the partial cycle count process, the **Last cycle count** date/time won’t be updated for the location, even though all the items on hand at a given location are counted. The partial cycle count doesn't consider the parameter **Days between cycle counting** on  the **Cycle count plans** page. Partial cycle count doesn't support simultaneous counting of multiple items at the same location. Partial cycle count functionality may result in the same location being counted multiple times for an item when **Process cycle counting plan** is run. To avoid that scenario, specify filters in the **Select locations** field.

> [!NOTE]
> The Warehouse Management mobile app doesn't provide the **Add LP or item** button when you use the partial cycle count process.

## Example

For this example, only item number A0001 must be counted in warehouse 61.

1. A new work template for cycle counting is created. The **Work line breaks** option is used to group counting work lines by item number. Therefore, the cycle counting work that is created will have lines per item number. You can also group the lines by product variant number.
1. A new cycle counting plan is created that references the newly created work template. The cycle counting plan includes all locations in warehouse 61 (**Select locations** query) that hold inventory for item number A0001. The selection of specific products is defined in the **Cycle count product selections** section.
1. You can select products for cycle counting plans by setting the **Empty locations** field to **Exclude empty**. When the cycle counting plan is processed, partial cycle count work for item number A0001 is created. The actual counting process can be performed by using a mobile device menu item for guided cycle counting.

## Additional resources

[Cycle counting](cycle-counting.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]