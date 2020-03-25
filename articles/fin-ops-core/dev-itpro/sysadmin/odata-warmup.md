---
# required metadata

title: Build an Odata metadata cache when the AOS starts
description: This topic provides information about how to build an Odata metaata cache when the AOS starts.
author: hasaid
manager: AnnBe
ms.date: 03/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2020-01-01
ms.dyn365.ops.version: Platform update 13

---

# Build an Odata metadata cache when the AOS starts

[!include [banner](../includes/banner.md)]


With the release of Microsoft Dynamics 365 Platform Update 32, we have introduced the ability to build an Odata metadata cache when the AOS starts as opposed to when the first Odata request is made. This significantly decreases the response time for the first Odata call after an AOS process restart.

This option is useful when your business process can't wait for the Odata metadata cache to be built each time the AOS process restarts.

1. Go to **System administration** \> **Setup** \> **System parameters**.
2. On the **General Tab**, select **Build metadata cache when AOS starts**. and then select **Save**.

> [!NOTE]
> When you enable this functionality, the AOS should already be running and will have served one OData request. This means that the cache is already built. This new functionality will take effect during the next AOD restart.
