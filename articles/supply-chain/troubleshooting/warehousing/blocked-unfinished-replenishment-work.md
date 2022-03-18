--- 
title: Picking work blocked due to unfinished replenishment work 
description: Picking work may be blocked because of dependent replenishment work. Complete the replenishment work and then process the picking work. 
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
# Picking work can't be unblocked because of unfinished replenishment work

## Symptoms

When using wave demand replenishment, picking work can be blocked because of dependent replenishment work. If a picking location must be replenished to fulfill the source order demand, the system creates both the replenishment work and the picking work. However, it blocks the picking work until the replenishment work is completed and you receive the following error message:

> Work %1 cannot be unblocked because it has unfinished replenishment work.

## Resolution

This behavior is intentional because the picking location won't have enough inventory unless the replenishment work is completed. Complete the replenishment work and then process the picking work.
