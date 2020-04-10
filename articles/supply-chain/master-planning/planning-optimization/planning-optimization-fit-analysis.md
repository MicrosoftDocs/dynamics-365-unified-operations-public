---
# required metadata

title: Planning Optimization fit analysis
description: This topic explains how to verify your current setup and data against the capabilities of the Planning Optimization functionality. 
author: ChristianRytt
manager: tfehr
ms.date: 10/30/2019
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
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: AX 10.0.5

---
# Planning Optimization fit analysis

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

To see how compatible your current setup and data are with the Planning Optimization functionality, go to **Master planning** \> **Setup** \> **Planning Optimization fit analysis**, and then select **Run analysis**. If the analysis finds any inconsistencies, they are listed on the same page. (The analysis can take a few minutes to run.)

> [!NOTE]
> If inconsistencies are found, you can still use Planning Optimization. The results of the fit analysis just show places where the planning service won't honor your current setup. In other words, they show places where some processes might be ignored or might not be supported.

## Analysis results: Example 1

- **Feature:** Production
- **Issue:** Items with BOM level greater than zero: 56
- **Explanation:** The fit analysis found 56 items that have a bill of materials (BOM) setup for production. Because the current version of Planning Optimization doesn't support production, Planning Optimization will generate planned purchase orders instead of planned production orders. It will also show a warning that lists the affected items.

### Analysis results: Example 2

- **Feature:** Actions
- **Issue:** Coverage groups with actions calculation enabled: 6
- **Explanation:** The fit analysis found six coverage groups where action calculation is turned on. Because the current version of Planning Optimization doesn't support actions, no actions will be generated during master planning.

## Related resources

[Planning Optimization overview](planning-optimization-overview.md)

[Get started with Planning Optimization](get-started.md)

[View plan history and planning logs](plan-history-logs.md)

[Apply filters to a plan](plan-filters.md)

[Cancel a planning job](cancel-planning-job.md)
