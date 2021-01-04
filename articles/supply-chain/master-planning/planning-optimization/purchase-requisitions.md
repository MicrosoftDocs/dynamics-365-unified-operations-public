---
# required metadata

title: Purchase requisitions
description: This topic describes how purchase requisitions are supported in Planning Optimization. 
author: ChristianRytt
manager: tfehr
ms.date: 01/04/2021
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
ms.search.validFrom: 2021-01-04
ms.dyn365.ops.version: 10.0.16

---
# Purchase requisitions

Master planning can replenish approved purchase requisitions. Instead of having users create purchase orders with a workflow, purchase requisitions can be covered by master planning. This means that a purchase requisition can result in a purchase order, transfer order, or production order, depending on the **Planned order type** setup on the related product.

## Enable master plans to include requisitions

To include requisitions during coverage calculation for a master plan, do the following steps:

1. Go to **Master planning** > **Setup** > **Plans** > **Master plans**.
1. Create or select a master plan.
1. On the **General** FastTab, set **Include requisitions**  to *Yes*.
1. Repeat from step 2 for each master plan where you want to included requisitions.

## Approved requisitions time fence

The *approved requisitions time fence* establishes how far back (in days) a master plan will include demand from approved replenishment requisitions. You can set an approved requisitions time fence at the both the coverage group and master plan levels.

### Set the approved requisitions time fence for a coverage group

To set the approved requisitions time fence for a coverage group:

1. Go to **Master planning** > **Setup** > **Coverage** > **Coverage group**.
1. Create or select a coverage group.
1. On the **Other** FastTab, set **Approved requisitions time fence (days)** to the number of days to include in the time fence.
1. Repeat from step 2 for each coverage group where you want to set up an approved requisitions time fence.

### Set the approved requisitions time fence for individual master plans

When you set an approved requisitions time fence for an individual master plans, that setting will override the time fence setting for the applicable coverage group (if any). To do so:

1. Go to **Master planning** > **Setup** > **Plans** > **Master plans**.
1. Create or select a master plan.
1. On the **TIme fences in days** FastTab, set **Approved requisitions time fence (days)** to the number of days to include in the time fence.
1. Repeat from step 2 for each master plan where you want to set up an approved requisitions time fence.

> [!IMPORTANT]
> **Coming soon**: Approved requisitions time fence isn't yet supported for Planning Optimization. Until it's supported, all values that are entered for **Approved requisitions time fence** will be ignored.

## Independent supply regardless of coverage code

Purchase requisitions will always be covered with independent planned orders regardless of the coverage code. This is done to ensure clear traceability and workflow between purchase requisitions and replenishment orders.

### Example 1

A product is set up with a **Coverage code** of *Min/max* and has the following inventory and requisition statuses:

- Inventory on hand quantity = 10
- Minimum inventory quantity = 15
- Maximum inventory quantity = 20
- Purchase requisition for 1 piece exists with a requested date of today

When master planning runs, two planned orders are created: one for 10 pieces to replenish to maximum, and one for 1 piece to replenish the purchase requisition.

### Example 2

A product is set up with a **Coverage code** of *Min/max* and has the following inventory and requisition statuses:

- Inventory on hand quantity = 17
- Minimum inventory quantity = 15
- Maximum inventory quantity = 20
- Purchase requisition for 1 piece exists with a requested date of today

When master planning runs, one planned order is created for one piece to replenish the purchase requisition.

### Example 3

A product is set up with a **Coverage code** of *Period* with a period length of 7 days, and has the following inventory, sales order, and requisition statuses:

- Inventory on hand quantity = 0
- Sales order for 5 pieces exists with expected ship date of today plus one day.
- Purchase requisition for three pieces exists with requested date of today plus three days.

When master planning runs, two planned orders are created: one to replenish the purchase requisition of 3 pieces and one to replenish sales order demand of 5 pieces.

> [!NOTE]
> Once a planned order that is pegged to a purchase requisition is firmed, the planning engine will keep the pegging to the purchase requisition. If the firmed order is later found to be missing some quantity to fulfill the purchase requisition, the system will create a new planned order for the difference.

For additional information about purchase requisitions, see [Purchase requisition overview](../../procurement/purchase-requisitions-overview.md).
