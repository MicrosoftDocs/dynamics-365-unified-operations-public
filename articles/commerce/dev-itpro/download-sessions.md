---
# required metadata

title: Download sessions
description: This article describes download sessions.
author: aneesmsft
ms.date: 02/06/2025
ms.topic: how-to
ms.search.form: RetailCDXDownloadSessionDataStore
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2025-02-06
ms.custom: 
  - bap-template
---

# Download sessions

Master data, such as customer, product, and pricing from [Headquarters](commerce-architecture.md#dynamics-365-commerce-headquarters) is made available in various channels, such as online stores or brick-and-mortar stores using [Commerce Data Exchange (CDX)](define-retail-channel-communications-cdx.md). To distribute master data, CDX periodically creates download sessions. A download session can be full (downloading all the data) or incremental (downloading new or updated data). As a part of each download session one or more jobs are run. Each job has a specific purpose such as distributing the customer data or the product data. 

Successful completion of these download sessions and jobs is critical for store operations. 

The download sessions form helps administrators view and monitor this download activity. 
