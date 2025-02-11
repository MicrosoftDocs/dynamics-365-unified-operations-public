---
# required metadata

title: Download sessions
description: This article describes the download sessions used with Commerce Data Exchange
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

Master data, such as customer, product, and pricing from [Headquarters](commerce-architecture.md#dynamics-365-commerce-headquarters) is made available in various channels, such as online stores or brick-and-mortar stores using [Commerce Data Exchange (CDX)](define-retail-channel-communications-cdx.md). 

To distribute master data, CDX periodically creates download sessions. A download session can be full (all data) or incremental (new and updated data). As a part of each download session one or more jobs are run. Each job has a specific purpose such as distributing the customer data or the product data. Successful completion of these download sessions and jobs is critical for store operations. 

Administrators view and monitor this download activity using the Download sessions form in Headquarters. The Download sessions form displays detailed information including the job name, channel database, session number, status, and more. It helps administrators ensure that point-of-sale (POS) devices are offline-ready if there is a network or service disruption.

## Enhanced download sessions

Many organizations using Dynamics 365 Commerce have multiple channels (and corresponding channel databases) and offline-enabled POS devices. With download sessions running at frequent scheduled intervals for each of these channels and devices, the list of download sessions often becomes very long. This makes it difficult for administrators to proactively monitor and troubleshoot issues that may be impacting download sessions and consequently the offline readiness of devices and stores.

The **Enhanced download sessions** feature provides multiple improvements to help administrators proactively and productively monitor download sessions. To enable the “Enhanced download sessions” feature, administrators can use the corresponding feature flag in the headquarters' [Feature Management workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md#the-feature-management-workspace).

When the Enhanced download sessions features is enabled, the Download sessions form will show a summary to help administrators quickly identify issues that may be affecting multiple channels and devices and impacting the offline readiness of stores. This includes top failing jobs, top suspended jobs, and top errors. The summary will also provide inline filters to quickly view the impacted jobs with just a single click.

For each failed job, the table will also provide an associated Error ID. These Error IDs are dynamically generated and automatically linked to relevant articles. This enables administrators to easily access up-to-date documentation and troubleshooting guides to address the issues.

## Download sessions troubleshooting

When a job running as a part of the a download session fails, a dynamic Error ID is generated based on the type of the error. Using the table below administrators can troubleshooot and address issues related to download sessions based on the Error ID.

| Error ID | Description |
|-------|-------------|
| CDX-48B-436F84 | TBD |
| CDX-53A-B40F45 | TBD |




