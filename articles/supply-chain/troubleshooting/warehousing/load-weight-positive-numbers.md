--- 
title: Load weight can only contain positive numbers 
description: When processing work between locations, you may receive an error regarding load weight and your update being canceled. Follow these steps to fix the issue. 
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
# Load weight error and update canceled when processing work between locations

## Symptoms

If there's open work when you process work from packing locations to staging locations, or from staging to docking locations, you may receive the following error:

> Field 'Load weight'(=-%1) can only contain positive numbers. Update has been canceled.

## Resolution

To fix this issue, go to **System administration \> Periodic tasks \> Database \> Consistency check**, and run the process for **Warehouse load weight consistency check**.
