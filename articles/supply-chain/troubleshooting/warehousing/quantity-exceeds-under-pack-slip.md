---
title: Quantity exceeds under-delivery percentage throughout Packing slip generation
description: When you are generating a packing slip, the outbound load contains a quantity that exceeds the under-delivery percentage.
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
<!-- KFM: What do you mean by "throughout"? -->
# Quantity exceeds under-delivery percentage throughout packing slip generation

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

Reverse everything that has been posted for the load, make sales order adjustments, and repeat the steps. <!-- KFM: How do we reverse everything? Repeat which steps? -->
