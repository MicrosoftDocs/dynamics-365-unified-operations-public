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

## Inventory quantity -XXXX could not be updated due to insufficient inventory transactions for item XXXX with dimensions Size=XXXX, Color=XXXX, Additions=XXXX, Site=XXXX, Warehouse=XXXX, Location=XXXX, Inventory status=Available, License plate=XXXX, Batch number=XXXX for reference Id XXXX on Lot Id XXXX.
<!-- KFM: This heading is much too long. Let's put a summary here and quote the error in the body text. -->
**Issue:** Cannot update an inventory quantity due to insufficient inventory transactions with the specified dimensions.

**Fix:** Ensure that there are no inventory transactions which are physically reserving the quantity - could be an open quality order, an inventory blocking record, or an output order, for example.

## Physical on-hand Site=XXXX, Warehouse=XXXX, Inventory status=Available, Batch number=XXXX, Owner=XXXX: XXXX cannot be reserved because only 0.00 are available in the inventory.
<!-- KFM: This heading is not quite as bad, but almost. Let's put a summary here and quote the error in the body text. -->

**Issue:** Cannot update an inventory quantity due to insufficient inventory transactions with the specified dimensions.

**Fix:** Seems to be due to open work. Either complete work or receive without work creation. Ensure that there are no inventory transactions which are physically reserving the quantity - could be an open quality order, an inventory blocking record, or an output order, for example.

## How to make a partial reservation of a load from load planning workbench form.

### Issue description

When using an item with batch above hierarchy the Release to warehouse from Load Planning Workbench for partial quantity doesn't work. The following error will appear, and no work gets created for the partial quantity.

Error: "To be assigned to wave, load lines must specify the dimensions above the location. To assign these dimensions, reserve and recreate the load line."

If we use an item with batch below reservation hierarchy instead of batch above, then the release of a load from Load Planning Workbench for partial quantity works fine.

### Issue resolution

This is by design. If you place a dimension above the location in the reservation hierarchy, then it must be specified prior to Release To Warehouse. Microsoft has evaluated this issue and determined it to be a feature limitation when releasing to warehouse from load planning workbench. It is not possible to release partial quantities when not all dimensions above location are specified.
