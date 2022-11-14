---
title: Channel-side calculation frequently asked questions
description: This article answers frequently asked questions (FAQs) about the channel-side calculation feature in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 11/14/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2022-11-10

---
# Channel-side calculation frequently asked questions

[!include [banner](../includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article answers frequently asked questions (FAQs) about the channel-side calculation feature in Microsoft Dynamics 365 Commerce.

#### Why do my products show as available in Commerce headquarters, but appear to be out-of-stock on my e-commerce site?

- To push the latest inventory snapshot to the channel database, follow the instructions in [How to use channel-side inventory calculation](use-channel-side-calculation.md).
- Unposted transactions are only visible on Commerce Scale Unit (CSU) before uploading to headquarters, which can cause discrepancies. Double-check after uploading transactions to headquarters. For more information, see [Optimize your inventory data](optimize-inventory-data.md).

#### Why are my products show as out-of-stock in Commerce headquarters, but appear as available on my e-commerce site?

- To push the latest inventory snapshot to the channel database, follow the instructions in [How to use channel-side inventory calculation](use-channel-side-calculation.md).
- Unstocked products are always treated as being available. Check the item model group settings of products, and then run **Distribution schedule job 1040 (Product)** after making any changes.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
