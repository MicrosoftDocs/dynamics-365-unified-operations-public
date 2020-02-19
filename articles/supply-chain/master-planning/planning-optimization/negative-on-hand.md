---
# required metadata

title: Planning with negative on-hand
description: This topic explains how negative on-hand is handled when you are using planning optimization. 
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
ms.reviewer: kamaybac
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
# Negative on-hand is treated as zero on-hand

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

In cases where the system shows a negative aggregate on-hand quantity, the planning engine will treat it as a quantity of zero to avoid over supply. It works as follows:

1. The planning optimization feature aggregates on-hand quantities at the lowest level of coverage dimensions (for example, if *location* is not a coverage dimension, then it will aggregate at the *warehouse* level ).
1. If the aggregate on-hand quantity on the lowest level of coverage dimensions is negative, the system assumes that the on-hand quantity is actually zero.

> [!IMPORTANT]
> The planning system can only be as precise as the input data. If the input data is inaccurate, negative on-hand records will indicate that the inventory information in Supply Chain Management is out of sync with the real world,  which means that the planning result will be flawed. To get a precise planning result, you should minimize the number of records showing a negative on-hand quantity.

## Example 1

Warehouse 13 is configured as follows:

- **Coverage code**: Min./Max.
- **Minimum**: 15 pcs.
- **Maximum**: 25 pcs.

The lowest level of coverage dimensions is *warehouse* and we have the following on-hand quantities recorded at the *location* level:

- **Site 1, Warehouse 13, Location 1**:  20 pcs.
- **Site 1 Warehouse 13, Location 2**: &minus;8 pcs.

The aggregated on-hand quantity for Warehouse 13 is *20 pcs. &minus; 8 pcs. = 12 pcs*.

In this case, the planning engine will use an aggregated on-hand quantity of 12 pcs. for Warehouse 13.

The result will be a planned order of *25 pcs. &minus; 12 pcs. = 13 pcs.*, thereby refilling from 12 pcs. to 25 pcs.

## Example 2

Warehouse 13 is configured as follows:

- **Coverage code**: Min./Max.
- **Minimum**: 15 pcs.
- **Maximum**: 25 pcs.

The lowest level of coverage dimensions is *warehouse* and we have the following on-hand quantities recorded at the *location* level:

- **Site 1, Warehouse 13, Location 1**:  4 pcs.
- **Site 1 Warehouse 13, Location 2**: &minus;8 pcs.

The aggregated on-hand for Warehouse 13 is *4 pcs. &minus; 8 pcs. = &minus;4 pcs.* (less than zero).

In this case, the planning engine will assume on-hand is 0 pcs. and not &minus;4 pcs. for Warehouse 13.  

The result will be a planned order of *25 pcs. &minus; 0 pcs. = 25 pcs.*, thereby refilling from 0 pcs. to 25 pcs.

## Related resources

[Planning Optimization overview](planning-optimization-overview.md)  
[Get started with Planning Optimization](get-started.md)  
[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)  
[View plan history and planning logs](plan-history-logs.md)  
[Cancel a planning job](cancel-planning-job.md)
