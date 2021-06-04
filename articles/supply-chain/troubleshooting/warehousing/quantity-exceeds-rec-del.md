---
title: Quantity that you are trying to update exceeds the quantity received/delivered.
description: When you are generating a packing slip, the outbound load contains the quantity that is larger than the work quantity that was picked and reserved for the sales order.
author: Henrikan
ms.date: 5/31/2021
ms.topic: troubleshooting
ms.search.form: WHSLoadTable_WHSSalesPackingSlipPost,WHSLoadPlanningListPage_WHSSalesPackingSlipPost,WHSLoadPlanningWorkbench_WHSSalesPackingSlipPost
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: Henrikan
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.18
---

# Quantity that you are trying to update exceeds the quantity received/delivered

Error code: SYS7676

## Symptoms

When you are generating a packing slip, the outbound load contains the quantity that is larger than the work quantity that was picked and reserved for the sales order.

When you try to generate a packing slip, the system shows the following error message:

> The quantity that you are trying to update exceeds the quantity received/delivered.

Therefore, you can't generate the packing slip for the load.

## Cause

The picked work quantity doesn't match the created work quantity on the load line. For example, this issue might occur if one of the following three elements is not accurate: load line quantity, work created quantity, or picked quantity.

## Resolution

Load or shipment is currently in a state where packing slip generation fails. To fix this issue, complete one of the following tasks:

- Check your load lines and make sure that all the related work has been completed at the final shipping location, and that the quantities match.
- Adjust the load line quantity.
- Reserve all pick registrations and redo picking.

### Check your load lines and make sure that all the related work has been completed at the final shipping location, and that the quantities match

Use the following procedure to check your load lines and make sure that all the related work has been completed at the final shipping location, and that the quantities match:

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the shipment can't be confirmed for. <!-- KFM: Are we trying to confirm a shipment or generate a packing slip? -->
1. On the **Load lines** FastTab, select the load line.
1. Make a note of the value of the **Work created quantity** field.
1. On the Action Pane, open the **Loads** tab and, from the **Related information** group, select **Work**.
1. Verify that the work has been completed at the final shipping location, and that the picked work quantity matches the created work quantity on the load line.
1. Repeat this procedure for all load lines to make sure that all criteria are met.

### Adjust the load line quantity  

Use the following procedure to adjust the load line quantity:

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the packing slip can't be generated for.
1. On the Action Pane, open the **Ship and receive** tab and, from the **Reverse** group, select **Reverse shipment confirmation**.
1. Open the **Load lines** tab and select the load line for the item that exceeds the over delivery. <!-- KFM: Is this really about over delivery? -->
1. Select **Reduce picked quantity** button to adjust the picked quantity.
1. Mark **Reduce load line** field to reflect adjustments on the load line.

### Reserve all pick registrations and redo picking

It might be the case that someone has used pick registration to close a load line without work, which can cause this issue.
<!-- KFM: Is something missing here? The content doesn't seem to match the heading. -->