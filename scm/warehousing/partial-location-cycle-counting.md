---
# required metadata

title: Partial location cycle counting 
description: Cycle count plans guide the actual counting operations. You can request that only specific products and product variants be counted instead of all on-hand inventory in a location.
author: perlynne
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

keywords: WHSCycleCountPlan, WHSWorkLineCycleCount, WHSWorkTemplateLineGroup, WHSWorkTemplateTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Partial location cycle counting

[!include[banner](../includes/banner.md)]


Cycle count plans guide the actual counting operations. You can request that only specific products and product variants be counted instead of all on-hand inventory in a location.

By using cycle count plans to create counting work, you can guide the actual counting operations. You can request that only specific products and product variants be counted instead of all on-hand inventory in a location. By filtering on specific products, the warehouse manager can reduce review overhead, avoid consolidation mistakes, and save time.

## How to configure partial location cycle counting
When you use the warehouse work process for counting operations, a work header is created for each location. When you define the cycle count plan, you can use the **Select locations** query to limit the cycle counting work that is created. When you select products for the cycle count plan, you can select both product and product variant queries to refine what is counted. 

You can associate a **work template** with a cycle count plan to define how the cycle count work should be created. The work template for counting operations is directly referenced from the cycle count plan. 

When you define the work template details, you can use the **Work line breaks** option to specify whether the counting work lines must be grouped by item number or product variant number. This setup is required if you want to count on-hand inventory only for specific products in a location. The cycle counting work lines that are created will have the level of information that you define here, and the guided counting operation will be handled based on this level. 

If you associate cycle count plans with work templates by using the **Work lines breaks** option, the **Partial cycle count** field is selected for the cycle counting work that is created, and multiple cycle counting work lines will be created based on the definition of the work template. 

Before *partial cycle count* work can be processed, you must, at a minimum, select **Display item number** for the mobile device menu item as part of the cycle counting setup. The warehouse operator will be asked to record only counting information that is related to the counting lines (item numbers and product dimensions). All other on-hand inventory will be ignored for this counting process. 

For the partial cycle count process, the **Last cycle count** date/time won’t be updated for the location.

## Example
For this example, only item number A0001 must be counted in warehouse 61.

1.  A new work template for cycle counting is created. The **Work line breaks** option is used to group counting work lines by item number. Therefore, the cycle counting work that is created will have lines per item number. You can also group the lines by product variant number.
2.  A new cycle counting plan is created that references the newly created work template. The cycle counting plan includes all locations in warehouse 61 (**Select locations** query) that hold inventory for item number A0001. The selection of specific products is defined in the **Cycle count product selections** section.
3.  You can select products for cycle counting plans by setting the **Empty locations** field to **Exclude empty**.When the cycle counting plan is processed, partial cycle count work for item number A0001 is created. The actual counting process can be performed by using a mobile device menu item for guided cycle counting.



See also
--------

[Cycle counting](cycle-counting.md)

