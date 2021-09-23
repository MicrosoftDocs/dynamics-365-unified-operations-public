---
title: The quantity can't be reduced when a sales order is canceled
description: The quantity can't be reduced when a sales order is canceled.
author: hja-ms
ms.date: 5/17/2021
ms.topic: troubleshooting
ms.search.form: SalesTable_SalesCancelOrder, SalesTableListPage_SalesCancelOrder
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: hja
ms.search.validFrom: 2021-05-17
ms.dyn365.ops.version: 10.0.18
---

# The quantity can't be reduced when a sales order is canceled

Error code: SYS138831

## Symptoms

The system shows the following error message:

> The quantity cannot be reduced. The number of inventory transactions on order is too low because the quantity or part of it is referenced by an output order or a production order or is marked against other transactions.

## Cause

If work is associated with a sales order, you can't cancel the sales order until the work is canceled and reversed. This requirement applies even if the work that is associated with the sales order is closed.

## Resolution

To fix this issue, complete the following tasks:

1. Cancel open work.
1. Delete the load.
1. Reduce the picked quantity.

### Cancel open work

To cancel open work, follow these steps.

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the ID of the work that you want to cancel, and that currently has a **Work status** value of *Open*, *In progress*, *Canceled*, *Combined*, or *Closed*.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

### Delete the load

To delete a load, follow these steps.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Open the relevant sales order.
1. On the **Sales order lines** FastTab, select **Warehouse \> Work details**.
1. On the **Work** page, on the Action Pane, on the **Work** tab, in the **Work** group, select **Cancel work**.
1. Confirm that the **Work status** field is set to *Canceled*.
1. Close the **Work** page.
1. On the sales order details page, on the **Sales order lines** FastTab, select **Warehouse \> Load details**.
1. On the Action Pane, select **Delete**.
1. Select **Yes** to confirm that you want to delete the load.
1. Close the **Load** page.

### Reduce the picked quantity

After all work has been canceled, follow these steps to reduce the picked quantity.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Open the relevant sales order.
1. On the **Sales order lines** FastTab, select **Update line \> Pick** from the toolbar.
1. On the **Pick** page, in the **Transactions** section, select the line where the **Issue status** field is set to *Picked*.
1. In the **Transactions** section, select **Add picking line** from the toolbar.
1. In the **Picking lines** section, select **Confirm pick all** from the toolbar.
1. Close the **Pick** page.
1. On the sales order details page, on the Action Pane, on the **Sales order** tab, in the **Maintain** group, select **Cancel**.
1. Select **Yes** to confirm that you want to cancel the sales order.
