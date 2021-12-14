---
title: Picked quantity isn't sufficient during packing slip generation
description: When you generate a packing slip, the outbound load contains a picked quantity that doesn't match the created work quantity on the load line.
author: GalynaFedorova
ms.date: 5/31/2021
ms.topic: troubleshooting
ms.search.form: WHSLoadTable_WHSSalesPackingSlipPost,WHSLoadPlanningListPage_WHSSalesPackingSlipPost,WHSLoadPlanningWorkbench_WHSSalesPackingSlipPost
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-gfedorova
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.18
---

# Picked quantity isn't sufficient during packing slip generation

Error code: SYS54073

## Symptoms

When you generate a packing slip, the outbound load contains a picked quantity that doesn't match the created work quantity on the load line.

When you try to generate a packing slip, the system shows the following error message:

> As %1 have been picked, it is not sufficient to update %2, when, subsequently, the remainder must be %3.

Therefore, you can't generate the packing slip for the load.

## Cause

The packing slip can't be generated in its current state because one of the following conditions might exist:

- The related work hasn't yet been picked and moved to the final shipping location.
- The picked work quantity doesn't match the created work quantity on the load line.
- The load line quantity, work created quantity, and picked quantity don't match.

## Resolution

The load or shipment is currently in a state where packing slip generation fails. To fix this issue, complete one of the following tasks:

- Review your load lines, and make sure that all the related work has been completed at the final shipping location, and that the quantities match.
- Adjust the load line quantity.
- Reverse all pick registrations, and redo picking.

### Review your load lines, and make sure that all the related work has been completed at the final shipping location, and that the quantities match

Use the following procedure to review your load lines and make sure that all the related work has been completed at the final shipping location, and that the quantities match.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the packing slip can't be generated for.
1. On the **Load lines** FastTab, select the load line.
1. Make a note of the value of the **Work created quantity** field.
1. On the Action Pane, on the **Loads** tab, in the **Related information** group, select **Work**.
1. Verify that the work has been completed at the final shipping location, and that the picked work quantity matches the created work quantity on the load line.
1. Repeat this procedure for all load lines to make sure that all criteria are met.

### Adjust the load line quantity

Use the following procedure to adjust the load line quantity.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the packing slip can't be generated for.
1. On the Action Pane, on the **Ship and receive** tab, in the **Reverse** group, select **Reverse shipment confirmation**.
1. On the **Load lines** tab, select the load line for the item that causes an issue.
1. Select **Reduce picked quantity** to adjust the picked quantity.
1. Set the **Reduce load line** field to reflect adjustments on the load line.

### Reverse all pick registrations, and redo picking

The issue might occur because someone used pick registration to close a load line without work. In this case, manual pick registration must be reversed, and picking must then be completed by using the Warehouse Management mobile app.

Use the following procedure to reverse the pick registration.

1. Go to **Accounts receivable \> Orders \> All orders**.
1. Select the sales order for which you can't post a packing slip for the load.
1. On the **Sales order lines** tab, select the sales order line that pick registration was done for.
1. Select **Update line \> Pick** to unpick the items.
