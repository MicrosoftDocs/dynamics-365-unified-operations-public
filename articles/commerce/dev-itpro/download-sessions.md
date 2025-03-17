---
title: Download sessions overview
description: Get an overview of the download sessions used with Commerce Data Exchange (CDX) in Microsoft Dynamics 365 Commerce.
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

# Download sessions overview

[!include[banner](../includes/banner.md)]

This article provides an overview of the download sessions that are used with Commerce Data Exchange (CDX) in Microsoft Dynamics 365 Commerce.

[CDX](define-retail-channel-communications-cdx.md) is used to make master data from [Dynamics 365 Commerce headquarters](commerce-architecture.md#dynamics-365-commerce-headquarters) available in various channels. For example, it distributes customer, product, and pricing data to online stores or brick-and-mortar stores.

To distribute master data, CDX periodically creates download sessions. A download session can be full (all data) or incremental (new and updated data only). As part of each download session, one or more jobs are run. Each job has a specific purpose, such as distributing customer data or product data. Successful completion of these download sessions and jobs is critical for store operations.

Administrators can view and monitor download activity by using the **Download sessions** form in headquarters. This form shows detailed information, including the job name, channel database, session number, and status. It also helps administrators ensure that data is being successfully synchronized with [Commerce Scale Units (CSUs)](../../fin-ops-core/dev-itpro/deployment/Initialize-Retail-Channels.md), and that point-of-sale (POS) devices are offline-ready to handle network or service disruptions.

## Enhanced download sessions

Many organizations that use Dynamics 365 Commerce have multiple channels together with corresponding channel databases and offline-enabled POS devices. As download sessions run at frequent scheduled intervals for each channel and device, the list of download sessions often becomes long. Therefore, it can be difficult for administrators to proactively monitor and troubleshoot issues that might be affecting download sessions and the offline readiness of devices and stores.

The Enhanced download sessions feature provides multiple improvements to help administrators proactively and productively monitor download sessions. Administrators can enable the **Enhanced download sessions** feature flag in the headquarters [Feature management workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md#the-feature-management-workspace) at **Systems administration** \> **Workspaces** \> **Feature management**.

When the Enhanced download sessions feature is enabled, the **Download sessions** form shows a summary to help administrators quickly identify issues that might be affecting multiple channels and devices, and the offline readiness of stores. For example, the summary includes the top failing jobs, top suspended jobs, and top errors. The summary also provides inline filters so that administrators can quickly view the affected jobs.

For each failed job, the grid provides an associated error ID. Error IDs are dynamically generated and are automatically linked to relevant articles. Therefore, administrators can easily access up-to-date documentation and troubleshooting guides to address the issues.
