---
# required metadata

title: Purchase requisitions
description: This topic describes how purchase requisitions are supported in Planning Optimization. 
author: ChristianRytt
manager: tfehr
ms.date: 12/21/2020
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
ms.search.validFrom: 2020-12-21
ms.dyn365.ops.version: 10.0.16

---
# Purchase requisitions

Master planning can replenish approved purchase requisitions. Instead of having users create purchase orders with a workflow purchase requisitions can be covered by master planning. This means that a purchase requisition can result in a purchase order, transfer order, or production order, depending on the **Planned order type** setup on the related product.

## Enable on Master plan

To include requisitions during coverage calculation for a specific **Master plan** you need to enable **Include requisitions** by setting it to **Yes**. This is done from **Master planning** > **Setup** > **Plans** > **Master plans.**

## Approved requisitions time fence

### Coverage group

On **Master planning** > **Setup** > **Coverage** > **Coverage group** you can define the **Approved requisitions time fence (days).** This controls the number of days in the past during which demand from approved requisitions that have the Replenishment purpose is included in master planning.

### Master plan

The settings from coverage group can be overwritten by on the **Master plan** by setting another value in the **Approved requisitions time fence (days).** This is done from **Master planning** > **Setup** > **Plans** > **Master plans.**

> [!NOTE]
> **Coming soon:** Approved requisitions time fence isn't yet supported for Planning Optimization. Until it's supported, all values that are entered for **Approved requisitions time fence** will be ignored.

## Independent supply regardless of coverage code

Purchase requisitions will always be covered with independent planned orders regardless of the coverage code. This is done to ensure clear traceability and workflow between purchase requisitions and replenishment orders.

### Example 1

Product is setup with coverage code &#39;Min/max&#39;

- Inventory on hand quantity = 10
- Minimum inventory quantity = 15
- Maximum inventory quantity = 20
- Purchase requisition for 1 piece exists with requested date = today

When master planning runs two planned orders are created. One for 10 pieces to replenish to maximum. And one for 1 piece to replenish the purchase requisition.

### Example 2

Product is setup with coverage code &#39;Min/max&#39;

- Inventory on hand quantity = 17
- Minimum inventory quantity = 15
- Maximum inventory quantity = 20
- Purchase requisition for 1 piece exists with requested date = today

When master planning runs one planned order is created for one piece to replenish the purchase requisition.

### Example 3

Product is setup with coverage code &#39;Period&#39; with a period length of 7 days

- Inventory on hand quantity = 0
- Sales order for 5 pieces exists with expected ship date = today + 1 day
- Purchase requisition for 3 pieces exists with requested date = today + 3 days

When master planning runs two planned orders are created. One to replenish the purchase requisition of 3 pieces and one to replenish sales order demand of 5 pieces.

> [!NOTE]
> Note Once a planned order, pegged to a purchase requisition, is firmed – the planning engine will keep the pegging to the purchase requisition. In case the firmed order, at some point, is missing some quantity to fulfill the purchase requisition, a new planned order for the delta will be created.

For additional information about purchase requisitions, see [Purchase requisitions overview](https://docs.microsoft.com/dynamics365/supply-chain/procurement/purchase-requisitions-overview)
