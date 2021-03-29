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

For topics that are related to batch and serial number registrations, see [Troubleshoot warehouse batch and serial reservation hierarchies](troubleshoot-warehouse-batch-and-serial-reservation-hierarchies.md).

## I receive the following error message: "Reservations cannot be removed because there is work created which relies on the reservations."

### Issue description

You can't unreserve inventory on a sales line, because there is open work against the line.

### Issue resolution

Investigate whether open packing group work exists to bring the item from a packing station to another location (such as *Baydoor*). Review the records on the **Work creation history log** and **Work details** pages to determine what is physically reserving the inventory, and then complete or delete the work to free up the reservation.

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


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
