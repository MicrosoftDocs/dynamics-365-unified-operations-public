---
# required metadata

title: Troubleshoot reservations in warehouse management
description: This topic describes how to fix common issues that you might encounter while you work with warehouse reservations in Microsoft Dynamics 365 Supply Chain Management.
author: perlynne
manager: tfehr
ms.date: 10/19/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2020-10-19
ms.dyn365.ops.version: 10.0.15
---

# Troubleshoot reservations in warehouse management

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while you work with warehouse reservations in Microsoft Dynamics 365 Supply Chain Management.

## I receive the following error message: "Reservations cannot be removed because there is work created which relies on the reservations."

### Issue description

You can't unreserve inventory on a sales line, because there is open work against the line.

### Issue resolution

Investigate whether open packing group work exists to bring the item from a packing station to another location (such as *Baydoor*). Review the **Work creation history log** and **Work details** to determine what is physically reserving the inventory, and then complete or delete the work to free up the reservation.

## I receive the following error message: "Inventory quantity -%1 could not be updated due to insufficient inventory transactions for item %2...."

### Issue description

This issue can occur if the system can't update an inventory quantity because there aren't enough inventory transactions that have the specified dimensions. Here is the full text of the full error message:

> Inventory quantity -%1 could not be updated due to insufficient inventory transactions for item %2 with dimensions Size=%3, Color=%4, Additions=%5, Site=%6, Warehouse=%7, Location=%8, Inventory status=Available, License plate=%9, Batch number=%10 for reference ID %11 on Lot ID %12.

### Issue resolution

Make sure that no inventory transactions are physically reserving the quantity. For example, these transactions might open quality orders, inventory blocking records, or output orders.

## I receive the following error message: "Physical on-hand...cannot be reserved because only 0.00 are available in the inventory."

### Issue description

This issue can occur if the system can't update an inventory quantity because there aren't enough inventory transactions that have the specified dimensions. Here is the full text of the full error message:

> Physical on-hand Site=%1, Warehouse=%2, Inventory status=Available, Batch number=%3, Owner=%4: %5 cannot be reserved because only 0.00 are available in the inventory.

### Issue resolution

This issue is probably caused by open work. Either complete the work or receive without work creation. Make sure that no inventory transactions are physically reserving the quantity. For example, these transactions might be open quality orders, inventory blocking records, or output orders.

## I receive the following error message: "To be assigned to wave, load lines must specify the dimensions above the location. To assign these dimensions, reserve and recreate the load line."

### Issue description

When you use an item that has a "batch above" reservation hierarchy, the **Release to warehouse** command on the **Load planning workbench** page for a partial quantity doesn't work. You receive this error message, and no work is created for the partial quantity.

However, if you use an item that has a "batch below" reservation hierarchy, you can release a load from the **Load planning workbench** page for a partial quantity.

### Issue resolution

This behavior is by design. If you put a dimension above **Location** in the reservation hierarchy, it must be specified before the release to the warehouse. Microsoft has evaluated this issue and has determined that it's a feature limitation during releases to the warehouse from the load planning workbench. Partial quantities can't be released if some dimensions above **Location** aren't specified.

For more information, see [Flexible warehouse-level dimension reservation policy](flexible-warehouse-level-dimension-reservation.md).
