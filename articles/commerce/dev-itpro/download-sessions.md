---
title: Download sessions
description: This article provides an overview of the download sessions used with Commerce Data Exchange in Microsoft Dynamics 365 Commerce.
author: aneesmsft
ms.date: 03/18/2025
ms.topic: overview
ms.search.form:
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2025-02-06
ms.custom: 
  - bap-template
---

# Download sessions

[!include[banner](../includes/banner.md)]

This article provides an overview of the download sessions used with Commerce Data Exchange (CDX) in Microsoft Dynamics 365 Commerce.

Master data, such as customer, product, and pricing from [Dynamics 365 Commerce headquarters](commerce-architecture.md#dynamics-365-commerce-headquarters) is made available in various channels, such as online stores or brick-and-mortar stores using [CDX](define-retail-channel-communications-cdx.md). 

To distribute master data, CDX periodically creates download sessions. A download session can be full (all data) or incremental (new and updated data). One or more jobs are run as part of each download session. Each job has a specific purpose such as distributing customer or product data. Successful completion of these download sessions and jobs is critical for store operations. 

Administrators can view and monitor download activity using the **Download sessions** form in headquarters. This form displays detailed information including the job name, channel database, session number, and status. The form also helps administrators ensure that data is being successfully synchronized with [Commerce Scale Units (CSUs)](../../fin-ops-core/dev-itpro/deployment/Initialize-Retail-Channels.md), and point-of-sale (POS) devices are offline-ready to handle network or service disruptions.

## Enhanced download sessions

Many organizations using Dynamics 365 Commerce have multiple channels with corresponding channel databases and offline-enabled POS devices. With download sessions running at frequent scheduled intervals for each of these channels and devices, the list of download sessions often becomes long. This long list of download sessions makes it difficult for administrators to proactively monitor and troubleshoot issues that may be impacting download sessions and the offline readiness of devices and stores.

The Enhanced download sessions feature provides multiple improvements to help administrators proactively and productively monitor download sessions. Administrators can enable the **Enhanced download sessions** feature flag in the headquarters [Feature management workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md#the-feature-management-workspace) at **Systems administration \> Workspaces \> Feature management**.

When administrators enable the Enhanced download sessions feature, the **Download sessions** form displays a summary to help quickly identify issues that may be affecting multiple channels and devices and impacting the offline readiness of stores. These issues include top failing jobs, top suspended jobs, and top errors. The summary also provides inline filters to quickly view the impacted jobs.

For each failed job, the table provides an associated Error ID. Error IDs are dynamically generated and automatically link to relevant articles, allowing administrators to easily access up-to-date documentation and troubleshooting guides to address the issues.

