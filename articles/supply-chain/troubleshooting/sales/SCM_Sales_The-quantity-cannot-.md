---
# required metadata

title: The quantity cannot be reduced when canceling sales order
description: The quantity cannot be reduced when canceling sales order
author: hja@microsoft.com
manager: tfehr
ms.date: 5/17/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SalesTable_SalesCancelOrder, SalesTableListPage_SalesCancelOrder
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: hja@microsoft.com
ms.assetid: 
ms.search.region: Global
ms.author: hja@microsoft.com

---

# The quantity cannot be reduced when canceling sales order

Error code: SYS138831

## Symptoms

The system shows the following error message:

> The quantity cannot be reduced. The number of inventory transactions on order is too low because the quantity or part of it is referenced by an output order or a production order or is marked against other transactions.

## Cause

If work is associated with a sales order, you can't cancel the sales order until the work is cancelled and reversed. This requirement applies even if the work that is associated with the sales order is closed.

## Resolution

To fix this issue, complete the following tasks:

- Cancel open work
- Delete the load
- Reduce picked quantity 

### Cancel open work

To cancel work, follow these steps.

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the ID of the work that you want to cancel, and that currently has a **Work status** value of *Open*, *In progress*, *Canceled*, *Combined*, or *Closed*.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

### Delete the load

1. On the sales order details page, on the toolbar, select the **Warehouse** drop down, and then select **Work details**.
1. On the Action Pane, on the **Work** tab, in the **Work** group, select **Cancel work**.
1. Inspect the **Work status** is set to *Canceled*.
1. Close the **Work** form.
1. On the sales order details page, on the toolbar, select the **Warehouse** drop down, and then select **Load details**.
1. On the Action Pane, select **Delete**.
1. Select **Yes** to confirm that you want to delete the load.
1. Close the **Load** form.

### Reduce picked quantity

When all work is canceled, follow these steps.

1. On the sales order details page, on the toolbar, select the **Update line** drop down, and then select **Pick**.
1. On the **Transactions** FastTab, select the line with **Issue status** set to *Picked*.
1. On the Toolbar, select the **Add picking line**.
1. On the **Picking lines** FastTab, on the Toolbar, select the **Confirm pick all**.
1. Close the **Pick** form.
1. On the Action Pane, on the **Maintain** group, select **Cancel**.
1. Select **Yes** to confirm that you want to cancel the sales order.
