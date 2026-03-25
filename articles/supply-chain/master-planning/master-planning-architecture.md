---
title: Master planning system architecture
description: Learn about the system architecture used to process master plans in Supply Chain Management, including outlines on architecture and data flow.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: ReqCreatePlanWorkspace
ms.topic: how-to
ms.date: 03/23/2026
ms.custom: 
  - bap-template
---

# Master planning system architecture

[!include [banner](../../includes/banner.md)]
[!INCLUDE [lcs-freeze-banner](../../includes/lcs-freeze-banner.md)]

In Supply Chain Management, the Planning Optimization Add-in for Microsoft Dynamics 365 Supply Chain Management manages master planning. This add-in enables master planning calculation to occur outside Dynamics 365 Supply Chain Management and the related SQL database. The benefits of the Planning Optimization functionality include improved performance and minimal impact on the SQL database during master planning runs. You can run quick planning runs even during office hours, so that planners can immediately react to demand or parameter changes.

To use Planning Optimization, install the Planning Optimization Add-in from your project in Microsoft Dynamics Lifecycle Services and turn on the Planning Optimization functionality in Supply Chain Management. Learn more in [Get started with master planning](planning-optimization/get-started.md).

The following illustration shows the advantage of running Planning Optimization during office hours.

:::image type="content" source="media/PlanningOptimization1.png" alt-text="Advantage of running Planning Optimization during office hours." lightbox="media/PlanningOptimization1.png":::

## Performance

You can use Planning Optimization in scenarios that involve long-running master plans. It's specifically designed for very fast calculations that involve very large volumes of data. Because it's built as a hyper-scalable multitenant service, multiple instances can work together simultaneously to calculate the plan. Additionally, the planning service removes the load of master planning from your system and works with a data stream that minimizes the server load.

Planning Optimization can help you achieve the following goals:

- Improve planning performance through a shorter runtime.
- Reduce the impact on other processes during the master planning run.
- Do more frequent planning runs. (You're not limited to daily runs.)
- Be confident that future business growth won't overload the planning system.

## Architecture and data flow

When you install the Planning Optimization Add-in from Lifecycle Services, you establish a secure connection to the Planning Optimization service. The service is located in the same data center country or region as the related Supply Chain Management instance. After you set up Planning Optimization, when you run master planning, Supply Chain Management sends master data and transactional data to the Planning Optimization service.

If you uninstall the Planning Optimization Add-in, the system removes all related data in the Planning Optimization service.

### High-level data flow for regeneration runs

1. The Supply Chain Management client sends a signal to request a planning run from Planning Optimization.
2. Planning Optimization requests the required data through the integrated connector.
3. The SQL database sends the requested information about setup, master, and transactional data to Planning Optimization through the connector. The connector translates information between Supply Chain Management and the Planning Optimization service.
4. The Planning Optimization service holds planning-related data in memory and performs the required calculations.
5. The planning result is sent to the Supply Chain Management database through the connector. The results include information such as planned orders and pegging information. Planning Optimization sends a signal to Supply Chain Management to indicate that the planning run is complete. It also sends any relevant messages and warnings.

The following illustration shows the data flow.

:::image type="content" source="media/PlanningOptimization2.png" alt-text="Diagram of Finance and Operations data flow showing client, database, connector, and Planning Optimization service interactions." lightbox="media/PlanningOptimization2.png":::
