---
title: Commerce database index compression
description: This article provides an overview of the database index compression features in Microsoft Dynamics 365 Commerce.
author: aneesmsft
ms.date: 07/05/2024
ms.topic: overview
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2024-07-01
ms.custom: 
  - bap-template
---

# Commerce database index compression

[!include[banner](../includes/banner.md)]

This article provides an overview of the database index compression features in Microsoft Dynamics 365 Commerce.

Index compression helps reduce the database size and can be used with both [offline-enabled point-of-sale (POS) devices](pos-offline-functionality.md) and [self-hosted Commerce Scale Units (CSUs)](retail-store-system-begin.md).

When index compression is enabled, the database is queried for noncompressed and nonclustered indexes that are either larger than 100 megabytes (MB) or at least 1 percent of the total database size. If any indexes meet this criterion, compression starts for the largest index in the list. After that index is compressed, the process pauses for 10 minutes and then resumes for the next-largest index. This process is repeated until all the selected indexes are compressed. After the last index in the list is compressed, the process pauses for 30 minutes and then checks again.

Index compression can be resource-intensive, depending on the number of indexes and their size. We strongly recommend that you [configure store hours](store-hours.md). In this way, you can ensure that the framework schedules index compression only outside of store hours. If store hours aren't configured, index compression can occur at varying times during the day. For more information, see the feature table in the next section.

## Index compression features

The following table describes the database index compression features that are available.

| Feature name | Description |
|--------------|-------------|
| Offline database compression | <p>This feature enables index compression to help reduce the size of the offline database for [offline-enabled POS devices](pos-offline-functionality.md) that run the [Store Commerce app](store-commerce.md).</p><p>If [store hours are configured](store-hours.md), index compression occurs outside of store hours. If store hours aren't configured, index compression can occur at any time of the day when the offline database isn't being used.</p><p>To use this feature, in Commerce headquarters, open the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), and enable **POS offline database compression**. After the feature is enabled, run the **1070** distribution schedule job.</p><p>This feature is available starting in Commerce version 10.0.29.</p> |
| On-premises CSU database compression | <p>This feature enables index compression to help reduce the size of the database on [self-hosted CSUs](retail-store-system-begin.md).</p><p>If [store hours are configured](store-hours.md), index compression occurs outside of store hours. If store hours aren't configured, index compression occurs between 1 AM and 6 AM, according to local machine time.</p><p>To use this feature, in headquarters, go to **Retail and Commerce** \> **Headquarters setup** \> **Parameters** \> **Commerce scheduler parameters**, and enable **On-premises CSU database compression**. After the feature is enabled, run the **1110** distribution schedule job.</p><p>This feature is available starting in Commerce version 10.0.41. It can be used only with SQL Server Express.</p> |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
