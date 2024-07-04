---
title: Commerce database index compression
description: This article provides an overview of the data base index compression features in Microsoft Dynamics 365 Commerce.
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

This article provides an overview of the data base index compression features in Microsoft Dynamics 365 Commerce.

Index compression helps reduce the database size and can be used with both [offline-enabled point-of-sale (POS) devices](pos-offline-functionality.md) and [self-hosted Commerce Scale Units (CSUs)](retail-store-system-begin.md).

When index compression is enabled, the database is queried for noncompressed and nonclustered indexes that are either greater than 100 MB, or at least 1% of the total database size. If any indexes are found that meet this criteria, compression starts for the largest index in the list. Once an index is compressed, the process is paused for 10 minutes before proceeding to compress the next largest index. This process is repeated until all of the selected indexes are compressed. When no indexes to be compressed remain or are found, the process pauses for 30 minutes before checking again.

Index compression can be resource intensive based on the number of indexes and their sizes. To ensure that the framework schedules index compression outside of store hours, [configuring store hours](store-hours.md) is highly recommended. If store hours aren't configured, index compression can happen at varying times during the day. The following feature table outlines the details.

## Index compression features

The following table lists the database index compression features that are available.

| Feature name | Description |
|--------------|-------------|
| Offline database compression | This feature enables index compression to help reduce the size of the offline database for [offline-enabled point-of-sale (POS) devices](pos-offline-functionality.md) running the [Store Commerce app](store-commerce.md).<br/><br/>If [store hours are configured](store-hours.md), index compression happens outside of store hours. If store hours aren't configured, index compression can happen at any time in the day when the offline database isn't being used. <br/><br/>To use this feature, in Commerce headquarters go to the [**Feature management workspace**](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and enable **POS offline database compression**. After the feature is enabled, run the **1070** distribution schedule job. <br/><br/>This feature is available starting in Commerce version 10.0.29.|
| On-premises CSU database compression | This feature enables index compression to help reduce the size of the database on [self-hosted CSUs](retail-store-system-begin.md). <br/><br/>If [store hours are configured](store-hours.md), index compression happens outside of store hours. If store hours aren't configured, index compression happens between 1 AM and 6 AM according to local machine time. <br/><br/>To use this feature, in headquarters go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce scheduler parameters** and enable **On-premises CSU database compression**. After the feature is enabled, run the **1110** distribution schedule job. <br/><br/>This feature is available starting in Commerce version 10.0.41 and can only be used with SQL Server Express. |



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
