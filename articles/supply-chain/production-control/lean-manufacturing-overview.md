---
# required metadata

title: Lean manufacturing overview
description: This article provides an overview and description of the lean manufacturing features in Dynamics 365 Supply Chain Management.
author: johanhoffmann
ms.date: 06/20/2017
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: KanbanBoardTransferJob, KanbanBoardWorkCell, KanbanJobSchedulingListPage, LeanProductionFlow, Kanban, KanbanQuantityOverview, KanbanAssignCard, KanbanCirculatingCards, KanbanRules, WHSKanbanWaveTableManagePickingListPool
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 026c5605-6be7-4fdb-a6f2-8e37a806796c
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Lean manufacturing overview

[!include [banner](../includes/banner.md)]

This article provides an overview and description of the lean manufacturing features in Dynamics 365 Supply Chain Management.

Lean manufacturing offers tools that you can use to model lean operations. These tools support and promote the following concepts and business activities:
-   Create a lean manufacturing foundation by modeling manufacturing and logistics processes as production flows.
-   Implement a lean pull system by using kanbans to signal demand requirements.
-   Monitor and maintain kanban jobs.

The lean manufacturing architecture consists of production flows, activities, and kanban rules. These structures are fully integrated with Supply Chain Management processes. You can use lean manufacturing in a mixed-mode manufacturing environment that combines various supply, production, and sourcing strategies. These strategies include production orders, batch orders for process industries, purchase orders, and transfer orders.

| **Important**                                                                                                                                                                                                                                                                |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| You can use Supply Chain Management to support the implementation of lean manufacturing with kanbans. However, a successful implementation of lean principles depends on the internal business processes that you use, and the actual production conditions and environment. |

## Modeling manufacturing and logistics processes as production flows
To create a lean manufacturing foundation, model the manufacturing and logistics processes as production flows. This activity consists of the following tasks:
1.  Identify the processes for which you want to implement a lean replenishment strategy, and then model these processes as production flows. You can then analyze and streamline the processes. One of the goals of a lean implementation is to reduce waste by improving the flow of material and information.
2.  Define a production flow as a sequence of activities that describes the flow of material. A transfer activity defines the movement of a product or products from one location to another. A process activity defines a value-added operation that is applied to a product.
3.  Create a version of the production flow that defines the requirements for takt time. These requirements are used to calculate the cycle times of each activity in the production flow. You can create multiple versions of production flows, and then use these versions to improve processes.

## Using kanbans to signal demand requirements
A pull system produces goods only when goods are needed. This practice reduces delivery lead times and excess inventory. You can use kanbans to plan, track, and process requirements that are based on production flows. To create a kanban framework, create kanban rules that define when kanbans are created, and how the requirements are fulfilled. You can create two types of kanban rules. Manufacturing rules create process kanban jobs, and withdrawal kanban rules create transfer kanban jobs. You can set up the following replenishment strategies:
-   **Fixed quantity** kanban rules are related to a fixed number of handling units, which means that the numbers of active kanbans are constant. Whenever all the products from a Kanban are consumed and the handling units are manually emptied, a new kanban of the same type is created. When you create fixed quantity kanban rules, you can calculate the optimal kanban quantities and the product quantities that are used. The calculation takes into account forecast, actual demand from open orders, lead time to replenish items, and historical demands.
-   **Scheduled** kanban rules replenish requirements that are calculated by master planning. Master planning generates planned kanbans that can be firmed to kanbans.
-   **Event** kanban rules replenish requirements that originate from sales order lines, production BOM lines, kanban lines, or minimum inventory settings. When event kanbans are generated, they are pegged to the source requirements.

When kanbans are created, one or more kanban jobs are generated based on the kanban flow activities that are defined in the kanban rules.

## Monitoring and maintaining kanban jobs
Lean manufacturing provides visibility into the current status of manufacturing and logistics activities that are governed by the kanban rules. As a result, you can plan and prioritize the following tasks:

-   Gain an overview of the current kanban job schedule.
-   Plan and reschedule kanban jobs.
-   Track and register the status of kanban jobs.

The following list describes the specialized kanban boards:
-   Kanban job scheduling – Provides an overview of the kanban jobs. The board displays kanban jobs and their status for one or multiple work cells. The jobs are listed according to the planning periods (days or weeks) that are defined in the production flow model. The board also displays the capacity consumption for each planning period, so that you can monitor the scheduled load. You can change the status of kanban jobs, reschedule kanban jobs to different planning periods, and perform other tasks.
-   Kanban board for transfer jobs – This board provides an overview of the current transfer jobs. You can update and register picking lists, start and complete transfer jobs, and perform other tasks.
-   Kanban board for process jobs – This board is designed to support the normal production flow and give an overview of the current situation in one or multiple work cells. From this board Kanbans can be prioritized, picked, or manufactured. The board is also designed to support bar code scanning for the reporting of Kanbans.

## Kanban jobs and integration with Supply Chain Management processes
Kanban jobs are fully integrated with current processes for inventory transactions in Supply Chain Management.
-   You can perform picking activities to replenish material that is used to fulfill the requirements of kanban jobs.
-   You can print kanban cards, circulating kanban cards, and picking lists to support the use of kanbans. These documents are used to represent, track, and register kanban jobs in the warehouse and on the production floor.
-   You can register the picking and transfer activities in inventory by scanning bar codes.

In addition, lean manufacturing supports the purchasing and invoicing processes for services that are referenced by subcontracted activities.
-   You can assign purchase agreement lines and services to subcontracted activities.
-   You can create periodic purchase orders and receipt advices to support the purchase and invoicing of the services.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]