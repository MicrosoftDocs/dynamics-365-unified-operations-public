---
title: Auto-update for Commerce Scale Unit (cloud)
description: This article describes auto-updates for Commerce Scale Unit (cloud).
author: jashanno
ms.date: 05/03/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: jashanno
ms.search.validFrom: 2020-07-13
ms.dyn365.ops.version: 8
---

# Auto-update for Commerce Scale Unit (cloud)
[!include[banner](../includes/banner.md)]


This feature currently applies to cloud-hosted Commerce Scale Unit. Self-hosted Commerce Scale Unit is not included and must be self-updated.

Auto-update for Commerce Scale Unit enables [One Version](../lifecycle-services/oneversion-overview.md) auto-update. All existing One Version processes, policies, and schedules apply to Auto-update for Commerce Scale Unit.


>[!Note]
> Auto-update for Commerce Scale Unit is being incrementally rolled-out to customers and is expected to be available to all customers by end of 2021.

## Limitations
The following limitations currently exist and are planned to be resolved in upcoming updates:

- In-app notifications are not available.
- If you have multiple Commerce Scale Units in a sandbox UAT environment, Commerce Scale Unit will only be auto-updated based on the first Commerce Scale Unit in that environment (alphabetically). The remaining Commerce Scale Units in each sandbox UAT environment will need to be self-updated.
- Auto-update for Commerce Scale Unit is not currently available for First Release customers, and is not currently applicable for Preview builds.

## Downtime duration and impact

Updates to Commerce HQ and Commerce Scale Unit (cloud) are applied sequentially. Downtime duration is typically one hour, but varies by data volume and region. To estimate downtime duration in your production environment, you can either self-update a Commerce Scale Unit in your sandbox UAT environment, or review the total update duration for both Commerce HQ and Commerce Scale Unit in Lifecycle Services (LCS).

> [!NOTE]
> Downtime duration will vary for each update and data volume. To estimate a realistic downtime duration, ensure that your sandbox UAT environment has the same data as your production environment. To do this, follow the steps in [Refresh database](../database/database-refresh.md). You also need to apply the same update in the sandbox UAT environment that you plan to estimate the downtime duration for.

For retailers with a business need for redundancy, Modern POS offline capability allows core POS operations to be available for use while disconnected from the internet or while the cloud environment is being updated. Stores operating with Commerce Scale Unit will also continue to operate with support for core POS operations during cloud maintenance windows. For more information, see [Online and offline point of sale (POS) operations](../../../commerce/pos-operations.md).

## Version support and backward compatibility
All in-instore components must be running released software that is less than 12 months old in order to maintain support. Customers are responsible for updating self-hosted components (such as components installed in stores or in privately managed datacenters) and ensuring that the installed versions of these components are actively supported.

Updates to components hosted in the cloud will continue to preserve backward compatibility with component versions self-hosted by the retailer (such as components installed in stores or in privately managed datacenters - Modern Point of Sale, Commerce Scale Unit, and Hardware Station) for 12 months after the release date for that version. Self-hosted components do not need to be updated at the same time as cloud-hosted components and can be updated on a separate cadence, allowing time to roll out updates to stores.

## Updating in-store components
You can choose to update self-hosted components manually at each store or use mass update tools such as Microsoft System Center Configuration Manager or Microsoft Intune.

With auto-update for Commerce Scale Unit, updates to in-store components can still be rolled-out in phases. The following controls are available to achieve this:

- **Screen layout designer** – Most visual elements in POS are configured and centrally managed by an administrative user in the customer organization. This means that new POS operations will not automatically be displayed on POS unless explicitly configured for inclusion in corresponding screen layouts. Screen layouts are configured using Screen layout designer and can be specific to a store or POS device. For more information, see [POS user interface visual configurations](../../../commerce/pos-screen-layouts.md).
- **Functionality profiles, POS permissions, Commerce parameters** – Many elements of POS functionality are typically configurable by the user. This can be configured through functionality profiles, POS permissions, Commerce parameters, or other controls which allow for device, register, store, or user-level functionality control in applicable scenarios.
- **Modern Point of Sale and Commerce Scale Unit** – Because Modern Point of Sale and Commerce Scale Unit are self-hosted by the retailer, topologies which include either of these components enable roll out of updates at a separate (and slower) cadence, and in a more granular fashion than with cloud-only topologies.
- **Feature flags** - Feature flags, configurable in Commerce HQ, provide additional controls to selectively turn features on/off.
