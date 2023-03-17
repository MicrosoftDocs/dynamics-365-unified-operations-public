---
title: Channel-side calculation FAQ
description: This article answers frequently asked questions (FAQ) about the channel-side calculation feature in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 01/30/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2022-11-10

---
# Channel-side calculation FAQ

[!include [banner](../includes/banner.md)]

This article answers frequently asked questions (FAQ) about the channel-side calculation feature in Microsoft Dynamics 365 Commerce.

#### Why are my products shown as available in Commerce headquarters but appear to be out of stock on my e-commerce site?

- To push the latest inventory snapshot to the channel database, follow the instructions in [Configure channel-side inventory calculation](channel-side-calculation.md).
- Until they're uploaded to Commerce headquarters, unposted transactions are visible only on Commerce Scale Unit (CSU). This behavior can cause discrepancies. After transactions are uploaded to Commerce headquarters, double-check availability. For more information, see [Optimize your inventory data](optimize-inventory-data.md).

#### Why are my products shown as out of stock in Commerce headquarters but appear as available on my e-commerce site?

- To push the latest inventory snapshot to the channel database, follow the instructions in [Configure channel-side inventory calculation](channel-side-calculation.md).
- Unstocked products are always treated as available. Check the item model group settings of products, and then run **Distribution schedule job 1040 (Product)** after you make any changes.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
