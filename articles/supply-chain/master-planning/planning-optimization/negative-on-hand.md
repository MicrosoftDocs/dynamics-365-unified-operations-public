---
# required metadata

title: Planning with negative on-hand
description: This topic explains how negative on-hand is handled when the Planning Optimization functionality is used. 
author: ChristianRytt
manager: AnnBe
ms.date: 02/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2020-02-18
ms.dyn365.ops.version: AX 10.0.5

---

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

# Negative on-hand is treated as zero on-hand
In case system on-hand quantity is negative, the planning engine will assume zero to avoid over supply. First Planning Optimization aggregates on-hand to the lowest level of coverage dimensions (e.g. aggregate on the warehouse level if location is not a coverage dimension). Then, if the on-hand on the lowest level of coverage dimensions is still negative, the system will assume that on-hand is zero.

## Example 1
**Coverage code** is **Min./Max.**, **Minimum** is 15 pcs and **Maximum** is 25 pcs for Warehouse 13.
The lowest level of coverage dimensions is warehouse and we have the following on-hand recorded on location level.
-	On-hand is 20 pcs on Site 1, Warehouse 13, Location 1  
-	On-hand is -8 pcs on Site 1 Warehouse 13, Location 2

The aggregated on-hand for Warehouse 13 is 20 pcs - 8 pcs = 12 pcs
In this case the planning engine will use the aggregated on-hand of 12 pcs for Warehouse 13.
Result will be a planned order of 25 pcs - 12 pcs = 13 pcs, to refill from 12 pcs to 25 pcs

## Example 2
**Coverage code** is **Min./Max.**. **Minimum** is 15 pcs and **Maximum** is 25 pcs for Warehouse 13.
The lowest level of coverage dimensions is warehouse and we have the following on-hand recorded on location level.
-	On-hand is 4 pcs on Site 1, Warehouse 13, Location 1  
-	On-hand is -8 pcs on Site 1 Warehouse 13, Location 2

The aggregated on-hand for Warehouse 13 is 4 pcs - 8 pcs = -4 pcs (less than 0)
In this case the planning engine will assume on-hand is 0 pcs (zero) and not -4 pcs for Warehouse 13.
Result will be a planned order of 25pcs – 0 pcs = 25 pcs, to refill from 0 pcs to 25 pcs

> [!NOTE]
> It’s important to highlight that the planning system can only be as precise as the input data. If the input data is inaccurate, negative on-hand records indicate that the inventory information in Supply Chain Management is out of sync with the real world,  then the planning result will be flawed. So minimizing the negative on hand records is critical for getting a precise planning result.

## Related resources

[Planning Optimization overview](planning-optimization-overview.md)

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)

[View plan history and planning logs](plan-history-logs.md)

[Cancel a planning job](cancel-planning-job.md)
