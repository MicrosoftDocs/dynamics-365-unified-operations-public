--- 
title: Can't release load for partial quantity with batch-above hierarchy 
description: When using an item with the batch-above reservation hierarchy, load lines must specify dimensions above the location in order for inventory to be allocated. 
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
# Can't release a load for partial quantity with batch-above reservation hierarchy

## Symptoms

When you use an item that has a *batch-above* reservation hierarchy, the **Release to warehouse** command on the **Load planning workbench** page doesn't work if you try to release a load for a partial quantity. You receive the following error message:

> To be assigned to wave, load lines must specify the dimensions above the location. To assign these dimensions, reserve and recreate the load line.

However, when you use an item that has a *batch-below* reservation hierarchy, you can release a load for a partial quantity from the **Load planning workbench** page.

## Cause

When a dimension is above the **Location** dimension in the reservation hierarchy, it must be specified before the release to the warehouse. Inventory can be successfully allocated only if there are no gaps in the dimensions above location.

## Resolution

Ensure that all dimensions above **Location** have been assigned by reserving and recreating the load line.
