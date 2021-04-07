---
# required metadata

title: View, manage, and approve planned orders
description: This topic provides information about how to view, manage, and approve planned orders planned orders in Planning Optimization. 
author: ChristianRytt
ms.date: 04/07/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2020-08-21
ms.dyn365.ops.version: 10.0.13

---
# View, manage, and approve planned orders

[!include [banner](../../includes/banner.md)]

This topic provides information about how to view, manage, and approve planned orders planned orders in Planning Optimization.

<a name="view-planned-orders"></a>

## View and manage planned orders

You can view and manage planned orders by going to any of the following pages, depending on which kinds of planned orders you want to work with:

- **Master planning \> Master planning**
- **Master planning \> Master planning \> Planned orders**
- **Production control \> Production orders \> Planned production orders**
- **Procurement and sourcing \> Purchase orders \> Planned purchase orders**
- **Inventory management \> Inbound orders \> Planned transfers**
- **Inventory management \> Outbound orders \> Planned transfers**

<!-- KFM: Anything under warehouse management? -->
<!-- KFM: Can we link somewhere that describes how these orders are created and what their many settings are for? -->

## View and edit planned order status values

You can use the **Status** field of each planned order to help track your progress or change how a planned order will be processed. The following **Status** values are available:

- **Unprocessed** – When master planning generates planned orders, they are given this status. Planned orders with this status will be deleted during the next planning run.
- **Completed** – Indicates that the planned order is finished. If you decide not to firm a planned order, you can manually change its status to *Completed*. Note that a status of *Unprocessed* and *Completed* are treated the same by the system.
- **Approved** – Indicates that the planned order is approved for firming. If you want to firm a planned order, you can change the status to *Approved*. If you want to keep edits or are planning to firm a planned order, change the status to *Approved*. Planned orders with *Approved* status are considered as fixed and expected supply by master planning, so they are not modified or deleted during later master planning runs. To achieve this, the planning logic copies the *Approved* planned orders from the old plan version to the new plan version during master planning. Note that *Approved* planned orders are only considered supply within the specific master plan.

To change the status of a single planned order, [open any planned orders list page](#view-planned-orders), open the order and do one of the following:

- Expand the **General** FastTab and edit the **Status** field.
- On the Action Pane, open the **Planned order** tab and, from the **Process** group, select **Change status**.
- On the Action Pane, select **Approve** to mark the order as approved. <!-- KFM: Please confirm. -->

To change the status of several planned orders at once, [open any planned orders list page](#view-planned-orders), mark the check box for each order you want to change and do one of the following:

- On the Action Pane, open the **Planned order** tab and, from the **Process** group, select **Change status**.
- On the Action Pane, select **Approve** to mark the order as approved. <!-- KFM: Please confirm. -->

## Approve planned orders

The approval of planned orders is an optional step on the way to creating a firmed order from a planned order.

The following illustration shows how you can use the **Status** assigned to each planned order to implement an approval workflow. To implement an approval process, manually adjust the **Status** value for each planned order as described in the previous section.

![Planned order flow](media/approved-planned-orders-1.png)

> [!TIP]
> We recommend that you approve any modified planned orders because otherwise the edits will be ignored and overwritten by the next planning run.

<!-- KFM: Any other requirements to implement this? For example, are we assuming the customer is using autofirming for this scenario? -->

## Additional resources

- [Firm planned orders](planned-order-firming.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]