---
title: The quantity cannot be reduced when canceling sales order
description: The quantity cannot be reduced when canceling sales order
author: hja@microsoft.com
ms.date: 5/17/2021
ms.topic: troubleshooting
ms.search.form: SalesTable_SalesCancelOrder, SalesTableListPage_SalesCancelOrder
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: hja@microsoft.com
ms.search.validFrom: 2021-05-17
ms.dyn365.ops.version: 10.0.18
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

To cancel work, follow these steps:

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the ID of the work that you want to cancel, and that currently has a **Work status** value of *Open*, *In progress*, *Canceled*, *Combined*, or *Closed*.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

### Delete the load

Do the following steps:

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Open the relevant sales order.
1. On the **Sales order lines** FatTab toolbar, select**Warehouse \> Work details**.
1. The **Work** page opens. On the Action Pane, open the **Work** tab and, from the **Work** group, select **Cancel work**.
1. Confirm that the **Work status** is set to *Canceled*.
1. Close the **Work** page.
1. You return to the sales order details page. On the **Sales order lines** FatTab toolbar, select **Warehouse \> Load details**.
1. On the Action Pane, select **Delete**.
1. Select **Yes** to confirm that you want to delete the load.
1. Close the **Load** form.

### Reduce picked quantity

When all work is canceled, follow these steps:

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Open the relevant sales order.
1. On the **Sales order lines** FatTab toolbar, select**Update line \> Pick**.
1. The **Pick** page opens. In the **Transactions** section, select the line with **Issue status** set to *Picked*.
1. On the **Transactions** toolbar, select the **Add picking line**.
1. On the **Picking lines** toolbar, select the **Confirm pick all**.
1. Close the **Pick** page.
1. You return to the sales order details page. On the Action Pane, open the **Sales order** tab and, from the **Maintain** group, select **Cancel**.
1. Select **Yes** to confirm that you want to cancel the sales order.
