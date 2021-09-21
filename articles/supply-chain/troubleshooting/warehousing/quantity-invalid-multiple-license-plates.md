---
title: Quantity not valid for picking work with multiple LPs 
description: When there is picking work with multiple license plates in one location, the quantity is not valid for unit ea. Verify that the following fields are correct. 
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
# Quantity not valid when there's picking work with multiple LPs in one location

## Symptoms

When there is picking work with multiple license plates in one location, the quantity is not valid for the *ea* unit and you receive the following error message:

> The quantity is not valid for unit 1%.

## Resolution

Verify that the **Unit sequence group ID** and **Unit conversions** fields on the released product or product variant are set correctly.

Note that the error message has been improved in version 10.0.15 to show the expected quantity (see [KB 4581627](https://fix.lcs.dynamics.com/Issue/Details/?bugId=486531)). The new error message is:

> The quantity is not valid. Expected %1 %2.
