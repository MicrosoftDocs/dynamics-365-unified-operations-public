--- 
title: One of the lines is already on a load 
description: This page explains why you may have received the error, "One of the lines is already on a load. Unable to release to warehouse," and how to resolve the issue. 
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
# One of the lines is already on a load

## Symptoms

When working with load building and shipments, you may receive the following error message:

> One of the lines is already on a load. Unable to release to warehouse.

If you manually create loads, or if you set up the process so that loads are already created before sales order line entry occurs, the assumption is that the subsequent release will be done manually, and that the route and rating from the load will be used.

In another possible scenario, you're trying to do an automatic release to the warehouse, but the wave process failed to create work. Therefore, an open shipment or load is still created. This open shipment or load then blocks subsequent attempts to automatically release the order until you either delete the open shipment or load, or manually reprocess the wave.

## Resolution

You can release from the sales order page, or an automatic release can be done from the release sales order page, only if no load exists before the release to the warehouse. The load will automatically be created after the wave is processed.
