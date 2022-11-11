---
title: Channel-side calculation frequently asked questions
description: This article describes the channel-side calculation frequently asked questions.
author: rickwyang
ms.date: 11/10/2022
ms.topic: article
ms.prod:
ms.technology:
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2022-11-10
ms.dyn365.ops.version: Release 10.0.10
ms.custom:
ms.assetid:
---
# Channel-side calculation frequently asked questions

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about the channel-side calculation feature.

## Why are my products available on Commerce headquarters, but showed as out-of-stock on e-commerce?

- Please make sure you follow [How to use channel-side inventory calculation](./commerce-how-to-use-channel-side-calculation.md) to push latest inventory snapshot to channel database.
- Unposted transactions are only visible on Commerce Scale Unit before uploading to Commerce headquarters, which could cause discrepancies. Please double check after uploading transactions, see [Optimize your inventory data](commerce-optimize-inventory-availability-data) for more details.

## Why are my products out-of-stock on Commerce headquarters, but showed as available on e-commerce?

- Please make sure you follow [How to use channel-side inventory calculation](./commerce-how-to-use-channel-side-calculation.md) to push latest inventory snapshot to channel database.
- Non-stocked products are always treated as always available, please check the item model group settings of products. Run Distribution schedule job 1040 (Product) after changing.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
