---
title: Purchase requisitions
description: Learn about purchase requisitions, including outlines and step-by-step processes for enabling master plans to include requisitions and approved time fences.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 01/04/2021
ms.custom: 
ms.reviewer: kamaybac
ms.search.form: ReqPlanSched, ReqGroup
---

# Purchase requisitions

[!include [banner](../../includes/banner.md)]

Master planning can replenish approved purchase requisitions. Therefore, to cover purchase requisitions, users don't have to use a workflow to create purchase orders. Instead, purchase requisitions can be covered by master planning. Because of this functionality, a purchase requisition can produce a purchase order, a transfer order, or a production order, depending on the **Planned order type** value that is set for the related product.

## Enable master plans to include requisitions

To include requisitions during the coverage calculation for a master plan, follow these steps.

1. Go to **Master planning** \> **Setup** \> **Plans** \> **Master plans**.
1. Create or select a master plan.
1. On the **General** FastTab, set the **Include requisitions** option to *Yes*.
1. Repeat steps 2 and 3 for each additional master plan where you want to include requisitions.

## Approved requisitions time fence

The *approved requisitions time fence* establishes how far back (in days) a master plan will include demand from approved replenishment requisitions. You can set an approved requisitions time fence at both the coverage group level and the master plan level.

### Set the approved requisitions time fence for a coverage group

1. Go to **Master planning** \> **Setup** \> **Coverage** \> **Coverage groups**.
1. Create or select a coverage group.
1. On the **Other** FastTab, set the **Approved requisitions time fence (days)** field to the number of days to include in the time fence.
1. Repeat steps 2 and 3 for each additional coverage group where you want to set an approved requisitions time fence.

### Set the approved requisitions time fence for individual master plans

When you set an approved requisitions time fence for an individual master plan, the setting overrides the time fence setting for any applicable coverage group.

1. Go to **Master planning** \> **Setup** \> **Plans** \> **Master plans**.
1. Create or select a master plan.
1. On the **TIme fences in days** FastTab, set the **Approved requisitions time fence (days)** field to the number of days to include in the time fence.
1. Repeat steps 2 and 3 for each additional master plan where you want to set an approved requisitions time fence.

> [!IMPORTANT]
> Approved requisitions time fences aren't supported for Planning Optimization. Until they are supported, all values that you enter in the **Approved requisitions time fence (days)** field will be ignored.

## Independent supply, regardless of coverage code

Purchase requisitions are always covered by independent planned orders, regardless of the coverage code. This behavior ensures clear traceability and workflows between purchase requisitions and replenishment orders.

### Example 1

A product is set up so that it has a **Coverage code** value of *Min/max*. It has the following inventory and requisition statuses:

- Inventory on-hand quantity = 10.
- Minimum inventory quantity = 15.
- Maximum inventory quantity = 20.
- A purchase requisition for one piece exists. It has a requested date of today.

When master planning runs, two planned orders are created: one for 10 pieces to replenish inventory to the maximum quantity, and one for one piece to replenish the purchase requisition.

### Example 2

A product is set up so that it has a **Coverage code** value of *Min/max*. It has the following inventory and requisition statuses:

- Inventory on-hand quantity = 17.
- Minimum inventory quantity = 15.
- Maximum inventory quantity = 20.
- A purchase requisition for one piece exists. It has a requested date of today.

When master planning runs, one planned order for one piece is created to replenish the purchase requisition.

### Example 3

A product is set up so that it has a **Coverage code** value of *Period* and a period length of seven days. It has the following inventory, sales order, and requisition statuses:

- Inventory on-hand quantity = 0.
- A sales order for five pieces exists. It has an expected ship date of today plus one day.
- A purchase requisition for three pieces exists. It has a requested date of today plus three days.

When master planning runs, two planned orders are created: one for three pieces to replenish the purchase requisition and one for five pieces to replenish sales order demand.

> [!NOTE]
> After a planned order that is pegged to a purchase requisition is firmed, the planning engine keeps the pegging to the purchase requisition. If the firmed order is later found to be missing some quantity that is required to fulfill the purchase requisition, the system will create a new planned order for the difference.

For more information about purchase requisitions, see [Purchase requisition overview](../../procurement/purchase-requisitions-overview.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]