---
# required metadata

title: Physical remaining quantity in the unit must be other than zero.
description: Physical remaining quantity in the unit must be other than zero.
author: v-gfedorova@microsoft.com
manager: tfehr
ms.date: 5/31/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSLoadTable,_WHSLoadPlanningListPage,__WHSLoadPlanningWorkbench
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

# Physical remaining quantity in the unit must be other than zero.

Error code: SYS19591

The system displays the followign error message:
	SYS19591

As part of the packing slip generation, the data supplied to it has a non-zero inventory qty but zero sales qty.

## Symptoms
When you try to generate a packing slip, the system shows the following error message:

Physical remaining quantity in the unit %1 must be other than zero.

Therefore, you can't generate the packing slip for the load.

## Cause
The system evaluates the physical remaining quantity in the inventory unit and physical remaining quantity in the shipping unit. If the system finds that physical remaining quantity in the shipping unit is 0, but physical remaining quantity in the inventory unit is not 0, you can't generate the packing slip. For example, this issue might occur if sales unit and inventory unit for the item are different and conversion between units is not accurate.

## Resolution
Load or shipment is currently in a state where packing slip generation fails. 
To fix this issue, complete one of the following tasks:
- Check your load lines to make sure that all the related work has been completed at the final shipping location, and that the quantities match
- Check your load lines to make adjustments that quantity can be cleanly converted without rounding issues
- Check your load lines to make sure that the unit and quantity are aligned with the decimal precision of the unit
- Check inventory UOM against sales UOM

### Check your load lines to make sure that all the related work has been completed at the final shipping location, and that the quantities match

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the shipment can't be confirmed for.
1. On the **Load lines** FastTab, select the load line.
1. Make a note of the value of the *Work created quantity* field.
1. On the Action Pane, on the *Loads* tab, in the **Related information** group, select **Work**.
1. Verify that the work has been completed at the final shipping location, and that the picked work quantity matches the created work quantity on the load line.
1. Repeat this procedure for all load lines to make sure that all criteria are met.

### Check your load lines to make adjustments that quantity can be cleanly converted without rounding issues
  
1. Go to **Warehouse management \> Loads \> All loads**. 
1. Select the load that  the packing slip can't be generated for.
1. On the Action Pane, open the **Ship and receive** tab and, from the **Reverse** group, select **Reverse shipment confirmation**.
1. Open the **Load lines** tab and select the load line for the item that exceeds the over delivery.
1. Select **Reduce picked quantity** button to adjust the picked quantity.
1. Open the **Line details** tab and, select **Order** 
1. In the **Quantity** field set the value to the picked quantity (**Work created quantity**), allowing Packing slip generation to proceed. 
 
### Check your load lines to make sure that the unit and quantity are aligned with the decimal precision of the unit
 
1. Go to **Warehouse management \> Loads \> All loads**. 
1. Select the load that the packing slip can't be generated for.
1. On the **Load lines** FastTab, select the load line for the item that causes an issue. Make a note of quantity and unit.
1. Go to **Organization administration \> Units \> Units**.
1. Select the unit that the packing slip can't be generated for.
1. Adjust the value of the **Decimal precision** as required.

### Check inventory UOM against sales UOM. 
1. Ensure that Sales UoM is being bigger than the Inventory UoM. Reconsider UOM reconfiguration for the item.



