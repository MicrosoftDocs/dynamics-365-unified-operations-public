---
# required metadata

title: Picked quantity is not sufficient to update throughout Packing slip generation
description: Picked quantity is not sufficient to update throughout Packing slip generation
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

# Picked quantity is not sufficient to update throughout Packing slip generation

Error code: SYS54073

The system displays the followign error message:
	SYS54073

As part of the packing slip generation, the outbound load contains the picked quantity that doesn't match the created work quantity on the load line.

## Symptoms
When you try to generate a packing slip, the system shows the following error message:

As %1 have been picked, it is not sufficient to update %2, when, subsequently, the remainder must be %3.

Therefore, you can't generate the packing slip for the load.

## Cause
The packing slip can't be generated in its current state because one of the following conditions might exist:

- The related work hasn't yet been picked and moved to the final shipping location.
- The picked work quantity doesn't match the created work quantity on the load line.
- Load line quantity, work created quantity, picked quantity don’t match.

## Resolution
Load or shipment is currently in a state where packing slip generation fails. 
To fix this issue, complete one of the following tasks:
- Check your load lines to make sure that all the related work has been completed at the final shipping location, and that the quantities match
- Adjust the load line quantity
- Reserve all pick registrations and re-do picking
 
### Check your load lines to make sure that all the related work has been completed at the final shipping location, and that the quantities match

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the shipment can't be confirmed for.
1. On the **Load lines** FastTab, select the load line.
1. Make a note of the value of the *Work created quantity* field.
1. On the Action Pane, on the *Loads* tab, in the **Related information** group, select **Work**.
1. Verify that the work has been completed at the final shipping location, and that the picked work quantity matches the created work quantity on the load line.
1. Repeat this procedure for all load lines to make sure that all criteria are met.

### Adjust the load line quantity  
1. Go to **Warehouse management \> Loads \> All loads**. 
1. Select the load that  the packing slip can't be generated for.
1. On the Action Pane, open the **Ship and receive** tab and, from the **Reverse** group, select **Reverse shipment confirmation**.
1. Open the **Load lines** tab and select the load line for the item that exceeds the over delivery.
1. Select **Reduce picked quantity** button to adjust the picked quantity.
1. Mark **Reduce load line** field to reflect adjustments on the load line. 

### Reserve all pick registrations and re-do picking
It might be the case that load line has been closed without work by using Pick registration, and then it causes this issue.



