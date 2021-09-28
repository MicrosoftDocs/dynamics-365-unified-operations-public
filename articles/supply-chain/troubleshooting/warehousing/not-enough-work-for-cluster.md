---
title: Not enough work found for cluster after configuring profile
description: If you configure a cluster profile, you may receive an error message that says not enough work can be found. Edit the profile and set Activate positions to No.
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
# Not enough work found for cluster when using System directed cluster picking

## Symptoms

When using the *System directed cluster picking* process, if you configure a cluster profile where, for example, 10 positions can be picked, the process works as planned when there is enough work to pick to 10 positions. However, if there are only eight positions to pick, you receive the following error message:

> Not enough work can be found for cluster.

## Resolution

To fix this issue, edit the cluster profile and set the **Activate positions** option to *No*.
