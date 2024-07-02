---
# required metadata

title: Commerce database index compression
description: This article provides an overview of Microsoft Dynamics 365 Commerce database index compression features.
author: aneesmsft
ms.date: 07/01/2024
ms.topic: article
audience: IT Pro
ms.reviewer: johnmichalak
ms.search.region: global
ms.search.industry: Retail
ms.author: aneesa
ms.search.validFrom: 2024-07-01

---

# Commerce database index compression

[!include[banner](../includes/banner.md)]

Index compression helps reduce the database size and can be used with both [offline-enabled point-of-sale (POS) devices](pos-offline-functionality.md) and [self-hosted Commerce Scale Units (CSUs)](retail-store-system-begin.md).

When index compression is enabled the database will be queried for non-compressed and non-clustered indexes that are either greater than 100 MB, or at least 1% of the total database size. If any indexes are found that meet this criteria, compression will start for the largest index in the list. Once an index is compressed, the process will be paused for 10 minutes before proceeding to compress the next largest index. This process will be repeated until all of the selected indexes have been compressed. When no indexes to be compressed remain or are found, the process will be paused for 30 minutes before checking again.

Index compression can be resource intensive based on the number of indexes and their sizes. To ensure that the framework schedules index compression outside of store hours [configuring store hours](store-hours.md) is highly recommended. If store hours are not configured, index compression can happen at varying times during the day. The feature table below outlines the details.

## Index compression features
The table below lists the database index compression features available.

| Feature name | Description |
|--------------|-------------|
| Offline database compression | This feature enables index compression to help reduce the size of the offline database for [offline-enabled point-of-sale (POS) devices](pos-offline-functionality.md) running the [Store Commerce app](store-commerce.md).<br/><br/>If [store hours are configured](store-hours.md), index compression will happen outside of store hours. If store hours are not configured, index compression can happen at any time in the day when the offline database is not being used. <br/><br/>To use this feature, go to the [**Feature management workspace**](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and enable **POS offline database compression**. After the feature has been enabled, run the **1070** distribution schedule job. <br/><br/>This feature is available in Commerce release 10.0.29 and later.|
| On-premises CSU database compression | This feature enables index compression to help reduce the size of the database on [self-hosted Commerce Scale Units (CSUs)](retail-store-system-begin.md). <br/><br/>If [store hours are configured](store-hours.md), index compression will happen outside of store hours. If store hours are not configured, index compression will happen between 1 AM and 6 AM of the local machine time. <br/><br/>To use this feature, go to **Retail and Commerce > Headquarters setup > Parameters > Commerce scheduler parameters** and enable **On-premises CSU database compression**. After the feature has been enabled, run the **1110** distribution schedule job. <br/><br/>This feature is available in Commerce release 10.0.41 and later and can only be used with SQL Server Express. |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
