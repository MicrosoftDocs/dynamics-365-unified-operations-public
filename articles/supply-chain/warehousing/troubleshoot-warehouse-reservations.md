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

## Reservations cannot be removed because there is work created which relies on the reservations.

**Issue:** Cannot unreserve inventory due to reliant work to complete.

**Fix:** Please investigate if open packing group work exists to bring item from packing station to baydoor. Review the transactions to verify what is physically reserving the inventory and complete or delete the work to free up the reservation.

## The error "Inventory quantity -%1 could not be updated due to insufficient inventory transactions for item %2 with dimensions Size=%3, Color=%4, Additions=%5, Site=%6, Warehouse=%7, Location=%8, Inventory status=Available, License plate=%9, Batch number=%10 for reference ID %11 on Lot ID %12" is shown.

**Issue:** This issue may occur when the system can't update an inventory quantity due to insufficient inventory transactions with the specified dimensions.

**Fix:** Ensure that there are no inventory transactions which are physically reserving the quantity - could be an open quality order, an inventory blocking record, or an output order, for example.

## The error "Physical on-hand Site=%1, Warehouse=%2, Inventory status=Available, Batch number=%3, Owner=%4: %5 cannot be reserved because only 0.00 are available in the inventory" is shown.

**Issue:** This issue may occur when the system can't update an inventory quantity due to insufficient inventory transactions with the specified dimensions. 

**Fix:** Seems to be due to open work. Either complete work or receive without work creation. Ensure that there are no inventory transactions which are physically reserving the quantity - could be an open quality order, an inventory blocking record, or an output order, for example.

## How to make a partial reservation of a load from load planning workbench form.

### Issue description
<!-- KFM: Note that because we have several paragraphs in the description, I added subheadings for this entry. -->
When using an item with batch above hierarchy the Release to warehouse from Load Planning Workbench for partial quantity doesn't work. The following error will appear, and no work gets created for the partial quantity:

> To be assigned to wave, load lines must specify the dimensions above the location. To assign these dimensions, reserve and recreate the load line.

If we use an item with batch below reservation hierarchy instead of batch above, then the release of a load from Load Planning Workbench for partial quantity works fine.

### Issue resolution

This is by design. If you place a dimension above the location in the reservation hierarchy, then it must be specified prior to release to warehouse. Microsoft has evaluated this issue and determined it to be a feature limitation when releasing to warehouse from load planning workbench. It is not possible to release partial quantities when not all dimensions above location are specified.
