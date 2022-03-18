--- 
title: Can't select Inventory status change as Work type 
description: You can't create a work template line for Inventory status change because the work type is used only by system processes. Select a different work type. 
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
# Can't select Inventory status change in the Work type column

## Symptoms

When configuring Microsoft Dynamics 365 Supply Chain Management, you may receive the following error message:

> You can't create a work template line for Inventory status change because the work type is not valid. Select a different work type.

## Resolution

This behavior is by design. The *Inventory status change* work type is used only by system processes. It can't be configured. Because the list of work types is fixed as an enumeration, the extra entries can't be filtered out of the **Work type** drop-down menu.
