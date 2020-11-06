---
# required metadata

title: Troubleshoot reservations in warehouse management
description: This topic describes how to fix common issues that you might encounter while working with warehouse reservations in Dynamics 365 Supply Chain Management.
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

This topic describes how to fix common issues that you might encounter while working with warehouse reservations in Dynamics 365 Supply Chain Management.

## I receive an error "Reservations cannot be removed because there is work created which relies on the reservations."

### Issue description

You can't unreserve inventory on a sales line because there is open work against the line.

### Issue resolution

Please investigate if open packing group work exists to bring item from a packing station to another location (e.g., Baydoor). Review the **Work creation history log** and **Work details** to verify what is physically reserving the inventory, then complete or delete the work to free up the reservation.

## I receive an error "Inventory quantity -%1 could not be updated due to insufficient inventory transactions for item %2 with ..."

### Issue description

This issue may occur when the system can't update an inventory quantity due to insufficient inventory transactions with the specified dimensions. The full error message is:

> Inventory quantity -%1 could not be updated due to insufficient inventory transactions for item %2 with dimensions Size=%3, Color=%4, Additions=%5, Site=%6, Warehouse=%7, Location=%8, Inventory status=Available, License plate=%9, Batch number=%10 for reference ID %11 on Lot ID %12.

### Issue resolution

Ensure that there are no inventory transactions that are physically reserving the quantity. It could be an open quality order, an inventory blocking record, or an output order, for example.

## I receive the error "Physical on-hand ... cannot be reserved because only 0.00 are available in the inventory."

### Issue description

This issue may occur when the system can't update an inventory quantity due to insufficient inventory transactions with the specified dimensions. The full error message is:

> Physical on-hand Site=%1, Warehouse=%2, Inventory status=Available, Batch number=%3, Owner=%4: %5 cannot be reserved because only 0.00 are available in the inventory.

### Issue resolution

This is probably be due to open work. Either complete work or receive without work creation. Ensure that there are no inventory transactions that are physically reserving the quantity. It could be an open quality order, an inventory blocking record, or an output order, for example.

## I receive the error "To be assigned to wave, load lines must specify the dimensions above the location. To assign these dimensions, reserve and recreate the load line."

### Issue description

When using an item with batch above hierarchy, the **Release to warehouse** command from the **Load planning workbench** for a partial quantity doesn't work. The error will appear, and no work is created for the partial quantity.

If we use an item with batch below reservation hierarchy instead of batch above, then the release of a load from the **Load planning workbench** for partial quantity works fine.

### Issue resolution

This is by design. If you place a dimension above the location in the reservation hierarchy, then it must be specified prior to release to warehouse. Microsoft has evaluated this issue and determined it to be a feature limitation when releasing to warehouse from the load planning workbench. It isn't possible to release partial quantities when not all dimensions above location are specified.

For more information, see [Flexible warehouse-level dimension reservation policy](flexible-warehouse-level-dimension-reservation.md).
