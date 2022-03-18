--- 
title: Invalid license plate or location error in mobile app 
description: When you scan a license plate ID or location, you may receive an error that it's invalid. Make sure that the license plate ID isn't reserved by something else. 
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
# Invalid license plate or location error when scanning in the mobile app

## Symptoms

When you scan a license plate ID or location, you may receive the following error message:

> The license plate or location is not valid.

## Resolution

Make sure that the license plate ID isn't reserved by something else. This issue used to occur when the value that a user scanned in the Warehouse Management mobile app was both a valid location and a valid license plate ID. However, this issue was resolved in version 10.0.11.
