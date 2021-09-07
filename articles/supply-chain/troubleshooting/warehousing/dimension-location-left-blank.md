--- 
title: Dimension location can't be blank if serial number is set 
description: If you receive this error when confirming a shipment after creating a transfer order for a serial item, the Default receipt location field is blank. 
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
# Error when confirming shipment after creating a transfer order for a serial item

## Symptoms

If you create a transfer order for a serial item by using a warehouse that's enabled for advanced warehouse management (WMS), and then after work is completed try to confirm the shipment, you receive the following error message:

> Dimension location can't be left blank if dimension serial number is set.

## Cause

This occurs because the **Default receipt location** field is blank for a transit warehouse of the "from" warehouse.

## Resolution

To fix this issue, specify a default receipt location in the transit warehouse. Make sure that this location is license plate-controlled.
