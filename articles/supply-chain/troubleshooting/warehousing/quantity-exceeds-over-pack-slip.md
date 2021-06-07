---
title: Quantity exceeds over-delivery percentage throughout packing slip generation
description: When you are generating a packing slip, the outbound load contains a quantity that exceeds the over-delivery percentage
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
# Quantity exceeds over-delivery percentage during packing slip generation

Error code: SYS24920

## Symptoms

When you are generating a packing slip, the outbound load contains a quantity that exceeds the over-delivery percentage.

When you try to generate a packing slip, the system shows the following error message:

> Overdelivery of line is %1 percent, but the allowed overdelivery is only %2 percent.

Therefore, you can't generate the packing slip for the load.

## Cause

The picked quantity for the load or shipment is larger than the ordered quantity and is not within the range of over-delivery percentage.

## Resolution

The load or shipment is currently in a state where packing slip generation fails. To fix this issue, complete one of the following tasks:

- Adjust the load line quantity.
- Adjust the over-delivery percentage.
- Reverse and make adjustments.

### Adjust the load line quantity  

Use the following procedure to adjust the load line quantity:

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the packing slip can't be generated for.
1. On the Action Pane, open the **Ship and receive** tab and, from the **Reverse** group, select **Reverse shipment confirmation**.
1. Open the **Load lines** tab and select the load line for the item that exceeds the over-delivery percentage.
1. Select **Reduce picked quantity** to adjust the picked quantity.
1. Open the **Line details** tab and, select **Order**.
1. In the **Quantity** field, set the value to the picked quantity (**Work created quantity** field), which will allow packing slip generation to proceed. 

### Adjust the over-delivery percentage

Use the following procedure to adjust the over-delivery percentage:

1. Go to **Accounts receivable \> Orders \> All orders**.
1. Select the sales order for which you can't post a packing slip for the load.
1. Open the **Sales order lines** tab and select the sales order line for the item that exceeds the over delivery.
1. Open the **Line details** tab and, select **Delivery**.
1. In the **Overdelivery** field, set the percentage to a larger value that can accommodate the quantity picked against the load quantity, which will allow packing slip generation to proceed.

### Reverse and make adjustments

Reverse everything that has been posted (including but not limited to packing slip, shipment confirmation, work) for the load, make sales order adjustments, rerelease the order to the warehouse and complete the shipment procedure. 

Use the following procedure to cancel a packing slip:

1. Go to **Warehouse management \> Loads \> All loads**.
1. On the Action Pane, open the **Ship and receive** tab and, from the **Reverse** group, select **Cancel packing slips**.

Use the following procedure to reverse a shipment confirmation:

1. Go to **Warehouse management \> Loads \> All loads**.
1. On the Action Pane, open the **Ship and receive** tab and, from the **Reverse** group, select **Reverse shipment confirmation**.

Use the following procedure to reverse a work:

1. Go to **Warehouse management \> Loads \> All loads**.
1. On the Action Pane, open the **Loads** tab and, from the **Work** group, select **Reverse work**.