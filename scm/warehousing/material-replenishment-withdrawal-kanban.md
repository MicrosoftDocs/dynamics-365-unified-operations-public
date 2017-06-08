---
# required metadata

title: Replenishment with withdrawal kanbans | Microsoft Docs
description: This topic describes how the withdrawal kanban is used for material replenishment for manufacturing activities.
author: johanhoffmann
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

keywords: KanbanBoardTransferJob, KanbanFlow, KanbanRules
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 121
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.industry: Manufacturing
ms.author: johanhoffmann
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Replenishment with withdrawal kanbans

[!include[banner](../includes/banner.md)]

This topic describes how the withdrawal kanban is used for material replenishment for manufacturing activities.

## Workflow for material replenishment that uses the withdrawal kanban
-------------------------------------------------------------------

The withdrawal kanban can be used to move a kanban of a single item between warehouses and production locations where the material is consumed. The withdrawal kanban supports a pull-based solution for material replenishment, where a pull signal is required in order to trigger supply for a specific demand. 

The following scenario shows a pull-based replenishment system where a pull signal triggers the creation of a kanban to replenish material for a production process. 

[![Pull signal triggers the creation of a kanban to replenish material for a production process](./media/material-replenishment-with-withdrawal-kanban.png)](./media/material-replenishment-with-withdrawal-kanban.png)

1.  Withdrawal kanban
2.  Kanban “from” location and put location for warehouse work
3.  Kanban “to” location and production input location
4.  Manufacturing process
5.  Warehouse work for kanban picking
6.  Warehouse locations for raw material
7.  Material warehouse
8.  Manufacturing warehouse

In this scenario, a manufacturing process (4) consumes material from a production input location (3) in the manufacturing warehouse (8). When a handling unit of the material (kanban) is consumed, it’s registered as empty. A replenishment signal is created for the item origin, and a new kanban (1) is created. In this case, the item origin consists of locations in the material warehouse (7). The material for the kanban is picked and put to a location (2) in the same warehouse. When the material is picked, it’s ready to be transferred from location 2 to the production input location (3) in the manufacturing warehouse (8).

## Configure warehouse work for kanban picking for the withdrawal kanban

To enable raw material picking for the withdrawal kanban, configure wave templates, work templates, and location directives for the **Kanban picking** work order type. This work order type doesn’t just support the picking process for the withdrawal kanban. It also supports the picking process for the manufacturing kanban. However, you can configure a separate picking process for each type of kanban by separating the wave templates, work templates, and location directives. To separate the wave templates, work templates, and location directives, set criteria on the activity type (**Process** or **Transfer**) in the queries for those entities.

## Configure the withdrawal kanban

The transfer activity that is used for the withdrawal kanban is configured as part of an activated activity plan in a Lean production flow. As part of the configuration of the transfer activity, you specify the “from” and “to” locations for the transfer. After you configure the transfer activity, you can assign it to a kanban rule of the **Withdrawal** type. The kanban rule sets the policies and configurations for the withdrawal kanban. The quantity of the kanban defines how many units of the handling unit the kanban carries during the transfer process. The fixed kanban quantity is used when the Fixed replenishment strategy is selected. This quantity defines how many kanbans that are required in order to prevent stock or build inventory from running out at the source of demand. The fixed quantity can be calculated based on actual demand, historical demand, and service levels. The following two scenarios describe how you can manage material replenishment that uses the withdrawal kanban.

## Scenario 1: Replenish a production input location by using a fixed withdrawal kanban

A manufacturing process consumes a purchased raw material from a production input location that is in the production warehouse. When the raw material is received from the vendor, it’s stored in locations in the material warehouse. Because the demand for the material is considered stable over a period, it’s set up to supply the production in a fixed quantity kanban flow. When a kanban is consumed at the production input location, an empty signal is registered, and a new kanban of the same type is added to the flow. 

The empty signal can be configured to occur automatically when a kanban is completed. Alternatively, the empty signal can be set up as a manual interaction that is given either from the Kanban transfer board or from a menu on the hand-held device. The Kanban transfer board is the workspace where all activities in the kanban life cycle are managed. 

When the kanban is created, a wave line for the raw material is added to a kanban wave for the material warehouse. In the picking list section of the Kanban transfer board, the status of the material and related warehouse processes can be monitored from wave creation to work creation, until the material is on-hand in the “transfer from” location and is ready to be transferred to the production input locations. The kanban can be completed either from the Kanban transfer board or from a menu on the hand-held device. 

In this scenario, the picking work in the material warehouse is processed as one activity. The transfer activity between the material warehouse and the production warehouse is processed as a separate activity. This approach can be useful if, for example, there is a large physical distance between the two warehouses. In this case, the kanban transfer activity can represent a truck load. 

If the distance between the warehouse locations and the production input location is small, it might be more efficient to include the transfer activity in the picking process. Then, after the material is picked, it can be put directly to the production input location. To support this process, you configure the transfer activity so that it’s automatically completed when the pick work of the withdrawal kanban is processed.

## Scenario 2: Automatically complete the transfer activity when kanban picking work is processed

In the following scenario, the transfer activity of the withdrawal kanban is configured to transfer between two locations in the same warehouse. The transfer activity of the withdrawal kanban is set up so that it’s completed automatically. 

[![Transfer activity is automatically completed when kanban picking work is processed](./media/transfer-activities-when-processing-kanban-picking.png)](./media/transfer-activities-when-processing-kanban-picking.png)

1.  Shared warehouse for raw materials and production
2.  Warehouse locations for raw materials
3.  Kanban “from” location and put location for warehouse work
4.  Withdrawal kanban
5.  Production input location
6.  Manufacturing process

After a kanban is consumed at the production input location, the kanban is reported as empty, and a new kanban is added to the flow. When the kanban is created, a wave line is added to a kanban wave. When the kanban wave is processed, warehouse work for kanban picking is created. The warehouse worker processes the work for kanban picking and is directed by the work to pick the material for the kanban in a warehouse location. As this warehouse worker confirms the pick, the kanban is automatically completed, and the warehouse worker is guided to the put the material to the production input location.

