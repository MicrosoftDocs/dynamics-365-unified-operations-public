--- 
title: Delivery note correction can't be processed
description: If you try to correct a delivery note after it's posted, you receive an error. This page explains how to correct posted packing slips for items enabled for WMS. 
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
# Delivery note correction can't be processed

## Symptoms

After you post a delivery note, you can't cancel it because the **Cancel** button is unavailable. You also can't correct the delivery note. If you try, you receive the following error message:

> The delivery note correction can't be processed. The delivery note only contains items that are subject to warehouse management processes, as these are not supported by Delivery Note correction.

## Resolution

To correct posted packing slips for items that are enabled for advanced warehouse management (WMS), you must do the posting from the load, not directly from the order.
