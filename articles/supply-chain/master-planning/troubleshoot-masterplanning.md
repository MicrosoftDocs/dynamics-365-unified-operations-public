---
# required metadata

title: Troubleshoot master planning
description: This topic describes how to fix issues that you might encounter while you work with master planning.
author: SmithaNataraj
manager: tfehr
ms.date: 11/04/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-11-04
ms.dyn365.ops.version: 10.0.15

---
# Troubleshoot master planning

This topic describes how to fix issues that you might encounter while you work with master planning.

## Bill of materials explosion behaves differently for firmed production orders and for estimated production orders for manually created work.

### Issue description

When a production order is firmed, the items aren't exploded when you explode the bill of materials (BOM). However, when you manually create a work order and then estimate the production order, the items are exploded.

### Issue resolution

The system is working as expected. The explosion that occurs when the production order is firmed will point to the planned order, but it doesn't appear that the planned order is currently firmed in this case. However, if the production order has been estimated, the explosion is triggered from the released production order where no planned order exists.

## The Delay value isn't updated when I reschedule a planned order.

To update the delay for planned orders, open the **Rescheduling** dialog box for the planned order. On the **Explosion** FastTab, make sure that the **Perform explosion after rescheduling** option is set to *Yes*.

## Production scheduling doesn't consider the safety margins that are set on the item coverage for pegged supply.

### Issue description

Master planning considers the safety margins. However, the safety margins are ignored when planned production orders are scheduled.

### Issue resolution

Margins are considered only during master planning, not during manual scheduling. Margins are designed to act as a buffer during the planning phase, to give some "margin" for the actual process.

To get the desired result, you can remove the margin. The route must then be updated so that it includes the desired time (for example, as queue time). Both master planning and manual scheduling should then produce the same result.

## Planned orders are generated even though we have items in stock and production orders already exist for them.

You might be able to fix this issue by increasing the **Positive days** value for the relevant groups on the **Coverage group** page. This change will cause the system to determine whether on-hand inventory can be used for the demand. Then a new planned order won't be generated for the items that are in stock.

## Master planning doesn't seem to respect capacity limitations and is scheduling more than the available capacity.

### Issue description

When you use operation scheduling where there is finite capacity, and where the route specifies a mix of requirements for both a resource group and individual resources, there is a small chance of overbooking because of the way that the algorithm validates for capacity conflicts. This overbooking can occur when you use helpers to run master planning. It's most likely to occur if there are many jobs that have a relatively short runtime.

### Issue resolution

If it's essential that no overbooking occur for operation scheduling, you can make the scheduling part of master planning single-threaded by turning on the **Accurate finite capacity for Operation Scheduling** option on the **Master planning parameters** page. This option isn't available by default. You must manually add it to the page by using personalization features. When you use this option, scheduling will run more slowly because of the lack of parallel processing.

## Planned orders take a long time to update.

### Issue description

When updating the requirement quantity and/or delivery date on a planned order, it typically takes at least 30 seconds per order to save the update.

### Issue resolution

This is a known issue with the built-in master planning engine. It is caused by the underlying auto explosion through the BOM structure during edits. This issue is addressed in Planning Optimization, where a planner can update and approve the relevant orders and, when desired, trigger a planning run to update planned orders for the underlying BOM structure.

One way to improve performance with the built-in master planning engine is to do the following:

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select a plan.
1. Expand the **Time fence in days** FastTab.
1. Set **Explosion** to *Yes*, and set the field below this setting to 0 (zero).

> [!NOTE]
> This will limit the number of explosions performed for this master plan on a single day.
