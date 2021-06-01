---
# required metadata

title: Decimal rounding of the physical updating quantity is incorrect.
description: Decimal rounding of the physical updating quantity is incorrect.
author: v-gfedorova@microsoft.com
manager: tfehr
ms.date: 5/31/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSLoadPlanningListPage,_WHSLoadTable
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

# Decimal rounding of the physical updating quantity is incorrect.

Error code: SYS19589

The system displays the followign error message:
	SYS19589

As part of the packing slip generation, the outbound load contain quantity that doesn't match to the decimal precision defined in the unit.

## Symptoms
When you try to generate a packing slip, the system shows the following error message:

Decimal rounding of the physical updating quantity in the unit %1 is incorrect.

Therefore, you can't generate the packing slip for the load.

## Cause
The system evaluates whether the decimal rounding of the shipping quantity corresponds to the decimal precision defined per shipping unit. If the system finds that the rounded shipping quantity to the specified number of decimal places defined in the unit doesn't match to the shipping unit, you can't generate the packing slip. For example, this issue might occur if sales quantity is 1,75kg, but decimal precision is set to 1.

## Resolution
Load or shipment is currently in a state where packing slip generation fails. 
To fix this issue, complete one of the following tasks:
- Check your load lines to make adjustments that quantity can be cleanly converted without decimal numbers and any other rounding issues
- Check your load lines to make sure that the unit and quantity are aligned with the decimal precision of the unit

### Check your load lines to make adjustments that quantity can be cleanly converted without decimal numbers and any other rounding issues
   
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
1. On the **Load lines** FastTab, select the load line for the item that causes an issue. Make a note of the value of the *Quantity* and *Unit* field.
1. Go to **Organization administration \> Units \> Units**.
1. Select the unit that the packing slip can't be generated for.
1. Adjust the value of the **Decimal precision** as required.



