---
# required metadata

title: Batch job to handle SQL index defragmentation
description: This topic describes a system batch job that is used to rebuild fragmented indexes.
author: sarvanisathish
manager: AnnBe
ms.date: 01/28/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: sarvanis
ms.search.validFrom: 2018-12-31 
ms.dyn365.ops.version: Platform update 22 
---

# Batch job to handle SQL index defragmentation  - Turned off [Effective: January 28 2021]

[!include[banner](../includes/banner.md)]


Starting January 28 2021, the system batch job to rebuild database indexes has been turned off in all environments of type Tier2 through Tier5 Sandbox and Production. Going forward, the index maintenance will be performed by Microsoft. The index management service will operate continuously without impacting the regulare user workloads. Customers no longer need to schedule and monitor this batch job.
