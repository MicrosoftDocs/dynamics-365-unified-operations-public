--- 
title: Can't make inventory reservations because 0.00 are available 
description: You receive an error saying the system can't make reservations because only 0.00 are available in the inventory. This issue is probably caused by open work. 
author: perlynne 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form:  
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: perlynne 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# System can't make reservations because 0.00 are available in the inventory

## Symptoms

This issue can occur if the system can't update an inventory quantity because there aren't enough inventory transactions that have the specified dimensions. You will receive the following error message:

> Physical on-hand Site=%1, Warehouse=%2, Inventory status=Available, Batch number=%3, Owner=%4: %5 cannot be reserved because only 0.00 are available in the inventory.

## Resolution

This issue is probably caused by open work. Either complete the work or receive without work creation. Make sure that no inventory transactions are physically reserving the quantity. For example, these transactions might be open quality orders, inventory blocking records, or output orders.
