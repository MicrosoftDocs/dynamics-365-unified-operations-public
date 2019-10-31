---
# required metadata

title: Planning Optimization fit analysis
description: This topic explains how to check your current setup and data against the capabilities of Planning Optimization. 
author: ChristianRytt
manager: AnnBe
ms.date: 1030/2019
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
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: AX 10.0.5

---

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

# Planning optimization fit analysis

You can check your current setup and data to see how compatible it is with Planning Optimization. To do so, go to **Master planning** > **Setup** > **Planning Optimization fit analysis**,  and click **Run analysis**. If the analysis finds any inconsistencies, they will be listed on the same page (it can take a few minutes to run). 

> [!NOTE]
> Issues that are found will not prevent you from using Planning Optimization. Rather, they define where the planning service will not honor your current setup, in other words, where some processes might be ignored or not supported.

## Analysis results: example 1

- **Feature**: Production

- **Issue**: Items with BOM level greater than zero: 56

- **Explanation**: Because production is not supported in the current version of Planning Optimization, the issue shows that the fit analysis found 56 items with a BOM setup for production. The consequence of this inconsistency is that Planning Optimization will generate planned purchase orders and not planned production orders, and give a warning that lists the impacted items.

### Analysis results: example 2

- **Feature** : Actions

- **Issue** : Coverage groups with actions calculation enabled: 6

- **Explanation**: The analysis found 6 coverage groups where actions calculation is enabled. As actions currently are not supported by Planning Optimization, actions will not be generated during master planning.

## Related resources

[Planning Optimization overview](planning-optimization-overview.md)

[Get started with Planning Optimization](get-started.md)

[View plan history and planning logs](plan-history-logs.md)

[Apply filters to a plan](plan-filters.md)

[Cancel a planning job](cancel-planning-job.md)
