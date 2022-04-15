---
# required metadata

title: Planning Optimization overview
description: This topic provides an overview of the Planning Optimization functionality.
author: t-benebo
ms.date: 10/31/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: AX 10.0.5

---
# Planning Optimization overview

[!include [banner](../../includes/banner.md)]

The Planning Optimization Add-in for Microsoft Dynamics 365 Supply Chain Management enables master planning calculation to occur outside Dynamics 365 Supply Chain Management and the related SQL database. The benefits that are associated with the Planning Optimization functionality include improved performance and minimal impact on SQL database during master planning runs. Quick planning runs can be done even during office hours, so that planners can immediately react to demand or parameter changes.

To use Planning Optimization, you must install the Planning Optimization Add-in from your project in Microsoft Dynamics Lifecycle Services (LCS) and turn on the Planning Optimization functionality in Supply Chain Management. For more information, see [Get started with Planning Optimization](get-started.md).

The following illustration shows the advantage of running Planning Optimization during office hours.

![Advantage of running Planning Optimization during office hours.](media/PlanningOptimization1.png)

## Improved performance

Planning Optimization can be used in scenarios that involve long-running master plans. It's specifically designed for very fast calculations that involve very large volumes of data. Because it's built as a hyper-scalable multitenant service, multiple instances can work together simultaneously to calculate the plan. Additionally, the planning service removes the load of master planning from your system and works with a data stream that minimizes the server load.

Planning Optimization can help you achieve the following goals:

- Improve planning performance through a shorter runtime.
- Reduce the impact on other processes during the master planning run.
- Do more frequent planning runs. (You aren't limited to daily runs.)
- Be confident that future business growth won't overload the planning system.

## Architecture and data flow

When the Planning Optimization Add-in is installed from LCS, a secure connection to the Planning Optimization service is established. The service is located in the same data center country or region as the related Supply Chain Management instance. After Planning Optimization is set up, when master planning is run, master data and transactional data are sent from Supply Chain Management to the Planning Optimization service.

If the Planning Optimization Add-in is uninstalled, all related data in the Planning Optimization service is removed.

### High-level data flow for regeneration runs

1. The Supply Chain Management client sends a signal to request a planning run from Planning Optimization.
2. Planning Optimization requests the required data via the integrated connector.
3. The SQL database sends the requested information about setup, master, and transactional data to Planning Optimization via the connector. The connector translates information between Supply Chain Management and the Planning Optimization service.
4. The Planning Optimization service holds planning-related data in memory and does the required calculations.
5. The planning result is sent to the Supply Chain Management database via the connector. The results include information such as planned orders and pegging information. Planning Optimization sends a signal to Supply Chain Management to indicate that the planning run has been completed. It also sends any relevant messages and warnings.

The following illustration shows the data flow.

![Data flow for regeneration runs.](media/PlanningOptimization2.png)

## Related resources

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)

[View plan history and planning logs](plan-history-logs.md)

[Apply filters to a plan](plan-filters.md)

[Cancel a planning job](cancel-planning-job.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]