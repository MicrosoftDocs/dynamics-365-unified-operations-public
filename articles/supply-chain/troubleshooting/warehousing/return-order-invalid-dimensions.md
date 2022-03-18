--- 
title: Can't create load line due to invalid inventory dimensions 
description: When trying to release a return sales order to the warehouse, you might receive an error about invalid inventory dimensions. Remove these from the order line. 
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
# Can't create load line for return sales order due to invalid inventory dimensions

## Symptoms

When trying to release a return sales order to the warehouse, you might receive the following error message:

> You can't create a load line for this order line because it contains inventory dimensions that are invalid. You can't reference inventory dimensions that are located below the location dimension in the reservation hierarchy. Remove the invalid dimensions from the order line.

## Resolution

Unfortunately, the product doesn't support load processing for a sales return process. Therefore, you can't release the return sales order to the warehouse.

On sales order transactions, you can't reference inventory dimensions that are located below the **Location** dimension in the reservation hierarchy. The resolution is to remove the invalid dimensions from the order line.
