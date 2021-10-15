--- 
title: Auto-reservation prompt is shown with available inventory 
description: When you use an item in a warehouse that hasn't enabled warehouse processes, the auto-reservation prompt is shown. Specify all the dimensions above Location.
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

# Auto-reservation prompt for batch number is shown even with available inventory

## Symptoms

When you use an item that has a *batch-above* reservation hierarchy in a warehouse that hasn't enabled warehouse processes, and automatic reservation is enabled, the auto-reservation prompt for a batch number is shown even if only one batch is available for picking.

However, when you use the same item in a warehouse where warehouse processes are enabled, the auto-reservation prompt isn't shown.

## Resolution

If a reservation hierarchy is defined as *batch-above* or *serial-above*, the referenced dimension (**Batch number** or **Serial number**) must always be specified on demand orders. Warehouse processes might be able to complete the information if a single batch or serial number is available. However, because the warehouse isn't enabled for warehouse processes, the user must always specify all the dimensions above **Location**.
