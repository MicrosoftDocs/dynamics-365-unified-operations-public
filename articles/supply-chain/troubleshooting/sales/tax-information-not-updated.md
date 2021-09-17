--- 
title: Tax information not updated if sales order location is changed 
description: If the site, warehouse, or delivery address is changed on a sales order header, the case tax information isn't updated on the lines. You must do this manually. 
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form: 
audience: Application User 
ms.reviewer: kamaybac
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Tax information isn't updated if location on a sales order header is changed

## Symptoms

If the site, warehouse, or delivery address is changed on a sales order header, the case tax information isn't updated on the lines.

## Resolution

This behavior is by design. The issue occurs because the delivery address, site, and warehouse aren't automatically changed at the line level. You must update them manually.
