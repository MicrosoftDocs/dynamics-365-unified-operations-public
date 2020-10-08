---
# required metadata

title: Troubleshoot Master Planning
description: This topic describes how to fix issues that you might encounter while working with Master Planning.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
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
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Master Planning

This topic describes how to fix issues that you might encounter while working with Master Planning.

## BOM explosion behaves differently when a production order is firmed and when work is created manually and the production order is estimated
### Issue description
If a BOM is exploded when the Production order is firmed, the items are not exploded. If a work order is created manually and the Production order is estimated, the items are exploded.

### Issue Resolution
This is working as expected, because the explosion when the production order is firmed would point to the planned order, that in this case seems not to be firmed at that point. In the case of doing it when the production order is estimated, the explosion is triggered from the released production order where no planned order exists.

## No updates on "Delay" after rescheduling a planned order
In order to update the delay for planned orders, ensure that the "Perform explosion after re-scheduling" is enabled, it is under the Explosion fast-tab when rescheduling.

## Production scheduling does not consider safety margins set on item coverage for pegged supply
Master planning considers the safety margins but when scheduling planned production orders ignores the safety margins.

### Resolution/Workaround
This is working as expected. Margins are only considered during master planning, not during manual scheduling. Expectation is that these margins act as a buffer during the planning phase to give some "margin" for the actual process. 

To get the desired result, the margin can be removed and the route must be updated to include the desired time e.g. as queue time. This way both master planning and manual scheduling should provide the same result.

##  Planned orders are generated despite having items in stock and Production orders already exist for the items
A potential way to resolve this could be setting the Positive days on the coverage group, since this will determine if onhand can be used for the demand. Then new planned order will not be generated for the items that are in stock.

## Master planning doesn’t seem to respect capacity limitations and is scheduling more than the available capacity
Master planning doesn’t seem to respect capacity limitations. Operation reserved is showing higher than capacity. 

### Resolution/Fix
When using operation scheduling with finite capacity and where a mix of requirements for both resource group and individual resources is specified on the route, there is a slight chance of overbooking due to the way the algorithm checks for capacity conflicts. This overbooking can happen when running master planning with helpers and is most dominant if there is a lot of jobs with a relatively short runtime. If it is essential that no overbooking happens for operations scheduling then there is an option to basically make the scheduling part of master planning single threaded, by turning on the "Accurate finite capacity for Operation Scheduling" flag on the master planning parameters. This option has to be added manually to the form by personalization as shown below. Note that if using this option scheduling will run slower due to the lack of parallelism.  




