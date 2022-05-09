---
title: Sales update history cleanup job fails or has performance issues
description: The Sales history cleanup batch job may fail or take very long if there is large amount of sales update data.
author: myvakalo
ms.date: 10/05/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: myvakalo
ms.search.validFrom: 2021-09-29
ms.dyn365.ops.version: 10.0.19
---

# Sales update history cleanup job fails or has performance issues

## Symptoms

The **Sales update history cleanup** batch job fails or has performance issues.  

## Cause

This can occur when your system includes a large number of sales updates, which can result in a large amount of sales update data. The cleanup job attempts to clean all of this data in one transaction. As a result, the job may take a very long time to run or even fail.

## Resolution

A new version of the **Sales update history cleanup** batch job is available for Supply Chain Management version 10.0.19 and higher. This feature is not turned on by default. For details about how it works and how to enable it in feature management, see [Schedule sales history data cleanup](../../sales-marketing/sales-update-history-cleanup-performance-improvements.md).

