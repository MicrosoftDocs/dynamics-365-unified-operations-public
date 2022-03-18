--- 
title: Direct delivery unable to process for WMS-enabled warehouse 
description: If the warehouse has WMS enabled, it doesn't support direct delivery. To use direct delivery, you must select a non-WMS item and warehouse. 
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
# Direct delivery not able to process for WMS-enabled warehouse

## Symptoms

If an item is added to a sales line for direct delivery from a warehouse that's enabled for warehouse management (WMS), you receive the following error message when the sales line is updated:

> Direct delivery is not able to process for warehouse 1% as it has warehouse management enabled. Please specify another warehouse that is not enabled for warehouse management.

## Resolution

Microsoft has evaluated this issue and has determined that it's a feature limitation. Currently, WMS doesn't support direct delivery. Therefore, to use direct delivery, you must select a non-WMS item and warehouse.
