--- 
title: Quantity not valid for unit %1 when performing a split pick 
description: When performing a split pick across multiple batches, you may receive an error that the quantity is not valid for unit %1. This page helps resolve the issue. 
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
# Quantity is not valid when performing a split pick across multiple batches

## Symptoms

When you try to perform a *split pick* across multiple batches, you receive the following error message:

> The quantity is not valid for unit %1.

## Resolution

The warehouse worker must use the *short picking* process in the Warehouse Management mobile app. If you're trying to pick multiple batches from the same location, you can also use the **Full** option in the app.
