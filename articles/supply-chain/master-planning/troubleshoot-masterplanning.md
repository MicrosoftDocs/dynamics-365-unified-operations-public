---
# required metadata

title: Troubleshoot master planning
description: This topic describes how to fix issues that you might encounter while working with  master planning.
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

This topic describes how to fix issues that you might encounter while working with  master planning.

## Bill of materials explosion behaves differently for a firmed production order compared to an estimated production order for manually created work.

### Issue description

When you explode a bill of materials (BOM) when a production order is firmed, the items are not exploded, but when you create a work order manually and then estimate the production order, the items are exploded.

### Issue resolution

The system is working as expected because the explosion when the production order is firmed would point to the planned order, which in this case seems not to be firmed at that time. If you do this when the production order has been estimated, the explosion is triggered from the released production order where no planned order exists.

## The "Delay" value doesn't update when I reschedule a planned order.

To update the delay for planned orders, open the **Rescheduling** dialog box for the planned order. Then open the **Explosion** FastTab and make sure that **Perform explosion after rescheduling** is set to *Yes*.

## Production scheduling doesn't consider the safety margins set on item coverage for pegged supply.

### Issue description

Master planning considers the safety margins but when scheduling planned production orders ignores the safety margins.

### Issue resolution

Margins are only considered during master planning, not during manual scheduling. Margins are designed to act as a buffer during the planning phase to give some "margin" for the actual process.

To get the desired result, the margin can be removed and the route must be updated to include the desired time (for example, as queue time). This way, both master planning and manual scheduling should provide the same result.

## Planned orders are generated even though we have items in stock and production orders already exist for them.

One way to resolve this could be to increase the **Positive days** setting for the relevant groups on the **Coverage group** page. This setting will cause the system to determine whether on-hand can be used for the demand. Then a new planned order won't be generated for the items that are in stock.

## Master planning doesn’t seem to respect capacity limitations and is scheduling more than the available capacity.

### Issue description

When using operation scheduling with finite capacity, and where the route specifies a mix of requirements for both resource group and individual resources, there is a slight chance of overbooking due to the way the algorithm checks for capacity conflicts. This overbooking can happen when running master planning with helpers and is most dominant if there are many jobs with a relatively short runtime.

### Issue resolution

If it is essential that no overbooking happens for operations scheduling, then you can make the scheduling part of master planning single threaded by turning on the **Accurate finite capacity for Operation Scheduling** flag on the **Master planning parameters** page. This option isn't available by default, so you must add it manually to the page using personalization features. When you use this option, scheduling will run slower due to the lack of parallel processing.  
