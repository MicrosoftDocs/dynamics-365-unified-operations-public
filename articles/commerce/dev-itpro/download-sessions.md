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

Master data, such as customer, product, and pricing stored in Headquarters is made available in various channels, such as online stores or brick-and-mortar stores using [Commerce Data Exchange (CDX)](define-retail-channel-communications-cdx.md). To distribute the master data from Headquarters to each channel, CDX uses jobs. Each job has a specific purpose such as distributing the customer data or the product data. Whenever master data needs to be distributed to a particular channel, CDX creates a download session. As a part of each download session one or more jobs are run that distribute (download) the data to the corresponding channel database. The download session can also be full (downloading all the data) or incremental (downloading only new or updated data).

The download sessions form helps administrators view and monitor this download activity. 
