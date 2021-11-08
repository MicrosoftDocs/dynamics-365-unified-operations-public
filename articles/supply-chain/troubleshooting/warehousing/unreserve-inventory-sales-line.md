--- 
title: Can't unreserve inventory on a sales order line 
description: If there's open work against a sales line and you try to unreserve inventory on the line, you receive an error. Complete or delete work to free the reservation. 
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
# Can't unreserve inventory on a sales order line

## Symptoms

If there's open work against a sales order line and you attempt to unreserve inventory on that line, you receive the following error message:

> Reservations cannot be removed because there is work created which relies on the reservations.

## Resolution

Investigate whether open packing group work exists to bring the item from a packing station to another location (such as *Baydoor*). Review the records on the **Work creation history log** and **Work details** pages to determine what is physically reserving the inventory, and then complete or delete the work to free up the reservation.
