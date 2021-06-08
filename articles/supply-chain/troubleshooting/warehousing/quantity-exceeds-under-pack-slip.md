---
title: Quantity exceeds under-delivery percentage during packing slip generation
description: When you are generating a packing slip, the outbound load contains a quantity that exceeds the under-delivery percentage.
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

# Quantity exceeds under-delivery percentage during packing slip generation

Error code: SYS24921

## Symptoms

When you are generating a packing slip, the outbound load contains a quantity that exceeds the under-delivery percentage.

When you try to generate a packing slip, the system shows the following error message:

> Underdelivery of line is %1 percent, but the allowed underdelivery is only %2 percent.

Therefore, you can't generate the packing slip for the load.

## Cause

The picked quantity of the load or shipment is less than ordered quantity and is not within the range of under-delivery percentage.

## Resolution

The load or shipment is currently in a state where packing slip generation fails.

To fix this issue, complete one of the following tasks:

- Adjust under delivery percentage.
- Reverse and make adjustments.

### Adjust under delivery percentage

Use the following procedure to adjust the under-delivery percentage:

1. Go to **Accounts receivable \> Orders \> All orders**.
1. Select the sales order for which you can't post a packing slip for the load.
1. Open the **Sales order lines** tab and select the sales order line for the item that exceeds the under-delivery percentage.
1. Open the **Line details** tab and, select **Delivery**.
1. In the **Underdelivery** field, set the percentage to a larger value that can accommodate the quantity picked against the load quantity, which will allow packing slip generation to proceed.

### Reverse and make adjustments

Reverse everything that has been posted (including but not limited to packing slip, shipment confirmation, work) for the load, make sales order adjustments, rerelease the order to the warehouse and complete the shipment procedure.

Use the following procedure to cancel a packing slip:

1. Go to **Warehouse management \> Loads \> All loads**.
1. On the Action Pane, open the **Ship and receive** tab and, from the **Reverse** group, select **Cancel packing slips**.

Use the following procedure to reverse a shipment confirmation:

1. Go to **Warehouse management \> Loads \> All loads**.
1. On the Action Pane, open the **Ship and receive** tab and, from the **Reverse** group, select **Reverse shipment confirmation**.

Use the following procedure to reverse work:

1. Go to **Warehouse management \> Loads \> All loads**.
1. On the Action Pane, open the **Loads** tab and, from the **Work** group, select **Reverse work**.
