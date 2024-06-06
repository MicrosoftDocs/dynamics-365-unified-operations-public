---
title: Build OData metadata cache when the AOS starts
description: Learn about how to build an OData metadata cache when the AOS starts, when your metadata cache needs to be quickly built.
author: hasaid
ms.author: hasaid
ms.topic: article
ms.date: 03/25/2020
ms.custom: 
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-01-01
ms.search.form: 
ms.dyn365.ops.version: Platform update 13
---

# Build OData metadata cache when the AOS starts

[!include [banner](../includes/banner.md)]


With the release of Platform update 32, we have introduced the ability to build OData metadata cache when the Application Object Server (AOS) starts, instead of when the first OData request is made. This significantly decreases the response time for the first OData call after an AOS process restart.

This option is useful if your business process can't wait for the OData metadata cache to be built each time that the AOS process restarts. Follow these steps to turn on this feature. 

1. Go to **System administration** \> **Setup** \> **System parameters**.
2. On the **General Tab**, select **Build metadata cache when AOS starts**, and then select **Save**.

> [!NOTE]
> When you enable this functionality, the AOS should already be running and should have served one OData request. This means that the cache is already built. This new functionality will take effect during the next AOS restart.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
