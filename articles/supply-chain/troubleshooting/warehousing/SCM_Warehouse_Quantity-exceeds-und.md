---
# required metadata

title: Quantity exceeds under delivery percentage throughout Packing slip generation
description: Quantity exceeds under delivery percentage throughout Packing slip generation
author: v-gfedorova@microsoft.com
manager: tfehr
ms.date: 5/31/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSLoadTable,__WHSLoadPlanningListPage,__WHSLoadPlanningWorkbench
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: v-gfedorova@microsoft.com
ms.assetid: 
ms.search.region: Global
ms.author: v-gfedorova@microsoft.com

---

# Quantity exceeds under delivery percentage throughout Packing slip generation

Error code: SYS24921

The system displays the followign error message:
	SYS24921

As part of the packing slip generation, the outbound load contains the quantity that is under the ordered Qty and is not within the range of under delivery percentage.

## Symptoms
When you try to generate a packing slip, the system shows the following error message:

Underdelivery of line is %1 percent, but the allowed underdelivery is only %2 percent.

Therefore, you can't generate the packing slip for the load.

## Cause
The picked quantity of the load or shipment is less than ordered quantity and is not within the range of under delivery percentage.

## Resolution
Load or shipment is currently in a state where packing slip generation fails. 
To fix this issue, complete one of the following tasks:
- Adjust under delivery percentage
- Reverse and make adjustments
 
### Adjust under delivery percentage
1. Go to **Accounts receivable \> Orders \> All orders**. 
1. Select the sales order that packing slip for the load cannot be posted for.   
1. Open the **Sales order lines** tab and select the sales order line for the item that exceeds the under delivery.
1. Open the **Line details** tab and, select **Delivery** .
1. In the **Underdelivery** field set the percentage to a large value, accommodating the quantity picked against the load quantity, allowing packing slip generation to proceed. 

### Reverse and make adjustments
1. Reverse everything that has been posted for the load, make sales order adjustments, repeat all steps all over again.



