--- 
title: License plate must be specified for this location 
description: If you receive this error after creating a transfer order for a WMS-enabled warehouse, the Default receipt location is blank for a transit warehouse. 
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
# License plate specification error when confirming shipment for a transfer order

## Symptoms

If you create a transfer order by using a warehouse that's enabled for advanced warehouse management (WMS), and then try to confirm the shipment after work is completed, you may receive the following error message:

> License plate must be specified for this location.

## Cause

This occurs because the **Default receipt location** field is blank for a transit warehouse of the "from" warehouse.

## Resolution

To fix this issue, specify a default receipt location in the transit warehouse. Make sure that this location is license plate-controlled.
