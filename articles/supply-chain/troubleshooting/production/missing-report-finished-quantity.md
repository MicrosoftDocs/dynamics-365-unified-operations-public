--- 
title: Report as finished update fails with missing quantity error 
description: If you try to end a production order while reporting the error quantity but not the time or material quantity, the report as finished update will fail.  
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
 
# Report as finished update fails with a missing quantity error

## Symptoms

You try to report a production order as finished while reporting the error quantity, but not while reporting the time or material quantity. The report as finished update fails when you try to end the production order, and you receive the following error message:

> Missing report as finished quantity.

## Resolution

If you report the error quantity on a production order, you must also report the good quantity.
