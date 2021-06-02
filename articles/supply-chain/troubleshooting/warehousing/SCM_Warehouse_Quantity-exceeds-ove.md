---

title: Quantity exceeds over delivery percentage throughout Packing slip generation
description: Quantity exceeds over delivery percentage throughout Packing slip generation
author: Henrikan
ms.date: 5/31/2021
ms.topic: troubleshooting
ms.service: dynamics-ax-applications
ms.search.form: WHSLoadTable_WHSSalesPackingSlipPost,WHSLoadPlanningListPage_WHSSalesPackingSlipPost,WHSLoadPlanningWorkbench_WHSSalesPackingSlipPost
audience: Application User
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
ms.custom: Henrikan
ms.search.region: Global
ms.author: Henrikan

---

# Quantity exceeds over delivery percentage throughout Packing slip generation

Error code: SYS24920

As part of the packing slip generation, the outbound load contains the quantity that is over the ordered Qty and is not within the range of over delivery percentage.

## Symptoms

When you try to generate a packing slip, the system shows the following error message:

> Overdelivery of line is %1 percent, but the allowed overdelivery is only %2 percent.

Therefore, you can't generate the packing slip for the load.

## Cause

The picked quantity of the load or shipment is larger than ordered quantity and is not within the range of over delivery percentage.

## Resolution

Load or shipment is currently in a state where packing slip generation fails. 

To fix this issue, complete one of the following tasks:

- Adjust the load line quantity.
- Adjust over delivery percentage.
- Reverse and make adjustments.
 
### Adjust the load line quantity  

1. Go to **Warehouse management \> Loads \> All loads**. 
1. Select the load that  the packing slip can't be generated for.
1. On the Action Pane, open the **Ship and receive** tab and, from the **Reverse** group, select **Reverse shipment confirmation**.
1. Open the **Load lines** tab and select the load line for the item that exceeds the over delivery.
1. Select **Reduce picked quantity** button to adjust the picked quantity.
1. Open the **Line details** tab and, select **Order**.
1. In the **Quantity** field, set the value to the picked quantity (**Work created quantity**), allowing Packing slip generation to proceed. 
 
### Adjust over delivery percentage

1. Go to **Accounts receivable \> Orders \> All orders**. 
1. Select the sales order that packing slip for the load cannot be posted for.   
1. Open the **Sales order lines** tab and select the sales order line for the item that exceeds the over delivery.
1. Open the **Line details** tab and, select **Delivery** .
1. In the **Overdelivery** field, set the percentage to a large value, accommodating the quantity picked against the load quantity, allowing packing slip generation to proceed. 

### Reverse and make adjustments

Reverse everything that has been posted for the load, make sales order adjustments, repeat steps all over again.
