--- 
title: Shipment for load was confirmed, but no lines are posted 
description: Shipment confirmation doesn't affect posting. It just updates the shipment and load status. Posting must occur in a separate process. 
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
# Shipment for load has been confirmed, but no lines are posted

## Symptoms

When working with outbound warehouse operations, you may receive the following message:

> The shipment for load 1% has been confirmed.

However, no further posting occurred.

## Resolution

This is by design. Shipment confirmation doesn't affect posting. It just updates the shipment and load status. Posting must occur in a separate process.
