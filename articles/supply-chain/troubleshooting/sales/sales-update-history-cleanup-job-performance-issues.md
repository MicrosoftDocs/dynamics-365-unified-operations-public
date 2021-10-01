---
title: Sales update history cleanup job fails or has performance issues
description: 'The "Sales history cleanup" job may fail or take very long if there is large amount of sales update data. In this case, you should enable the "Sales history cleanup performance improvement" feature.'
author: myvakalo
ms.date: 29/09/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: myvakalo
ms.search.validFrom: 2021-09-29
ms.dyn365.ops.version: 10.0.18
---

# Sales update history cleanup job fails or has performance issues

## Symptoms

The *Sales update history cleanup* periodic cleanup job fails or has performance issues.  

## Cause

This can occur when your system includes a large number of sales updates, which can result in a large amount of sales update data. The cleanup job attempts to clean all of this data in one transaction. As a result, the job may take a very long time or even fail.

## Resolution

A new version of the *Sales update history cleanup* job is available for Supply Chain Management version 10.0.19 and higher, but it isn't enabled by default. For details about how it works and how to enable it in feature management, see [Sales history cleanup performance improvements](../../sales-marketing/sales-update-history-cleanup-performance-improvements.md).

After enabling the feature, the *Sales update history cleanup* job (**Sales and marketing \> Period tasks \> Cleanup \> Sales update history cleanup**) will run as it did before, but with better performance and for a maximum of 2 hours. This means it might need to run several times to clean up all the data for a specific retention time frame.

<!-- KFM: I removed the details from here that were duplicated in the topic linked above.  -->