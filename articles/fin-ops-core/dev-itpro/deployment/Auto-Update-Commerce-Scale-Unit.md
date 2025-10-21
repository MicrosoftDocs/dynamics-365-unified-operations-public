---
title: Auto-update for Commerce Scale Unit (cloud)
description: Learn about auto-updates for Commerce Scale Unit (cloud), including limitations and an overview of downtime duration and impact.
author: johnmichalak
ms.author: johnmichalak
ms.topic: overview
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.validFrom: 2020-07-13
ms.custom: 
  - bap-template
---

# Auto-update for Commerce Scale Unit (cloud)

[!include[banner](../includes/banner.md)]

This feature currently applies to cloud-hosted Commerce Scale Unit (CSU). Self-hosted CSU isn't included and must be self-updated.

CSU updates are a part of [One Version](../lifecycle-services/oneversion-overview.md) auto-update. All One Version processes, policies, and schedules apply to auto-update for CSU.

[Auto-update configurations](../lifecycle-services/configure-service-updates.md) for environments also apply to CSUs. To [pause auto-updates](../lifecycle-services/pause-service-updates.md), CSUs must be on the current release (N) or the previous one (N-1). Releases older than N-1 must be updated to be compliant. 

## Limitations

The following limitations currently exist. Microsoft plans to resolve them in upcoming updates.v

- In-app notifications aren't available.
- Auto-update for CSU isn't currently available for First Release customers, and isn't currently applicable for Preview builds.

## Downtime duration and impact

Updates to Commerce headquarters and CSU (cloud) are applied sequentially. Downtime duration is typically one hour, but varies by data volume and region. To estimate downtime duration in your production environment, you can either self-update a CSU in your sandbox user acceptance testing (UAT) environment, or review the total update duration for both Commerce headquarters and CSU in Lifecycle Services (LCS).

> [!NOTE]
> Downtime duration varies for each update and data volume. To estimate a realistic downtime duration, ensure that your sandbox UAT environment has the same data as your production environment by following the steps in [Refresh database](../database/database-refresh.md). You also need to apply the same update in the sandbox UAT environment that you plan to estimate the downtime duration for.

For retailers with a business need for redundancy, Modern POS offline capability allows core POS operations to be available for use while disconnected from the internet, or while the cloud environment is updated. Stores operating with CSU continue to operate with support for core POS operations during cloud maintenance windows. For more information, see [Online and offline point of sale (POS) operations](../../../commerce/pos-operations.md).

## Version support and backward compatibility

All in-store components must run released software that is less than 12 months old to maintain support. Customers are responsible for updating self-hosted components such as components installed in stores or in privately managed datacenters, and ensuring that the installed versions of these components are actively supported.

Updates to components hosted in the cloud continue to preserve backward compatibility with component versions that are self-hosted by the retailer such as Modern Point of Sale, CSU, and Hardware Station for 12 months after the release date for that version. Self-hosted components don't need to be updated at the same time as cloud-hosted components and can be updated on a separate cadence, allowing time to roll out updates to stores.

## Updating in-store components

You can choose to update self-hosted components manually at each store or use mass update tools such as Microsoft System Center Configuration Manager or Microsoft Intune.

With auto-update for CSU, updates to in-store components can still be rolled-out in phases using the following controls:

- **Screen layout designer** – Most visual elements in POS are configured and centrally managed by an administrative user in the customer organization. This means that new POS operations aren't automatically displayed on POS unless explicitly configured for inclusion in corresponding screen layouts. Screen layouts are configured using Screen layout designer and can be specific to a store or POS device. For more information, see [POS user interface visual configurations](../../../commerce/pos-screen-layouts.md).
- **Functionality profiles, POS permissions, Commerce parameters** – Many elements of POS functionality are typically configurable by the user. These elements can be configured through functionality profiles, POS permissions, Commerce parameters, or other controls which allow for device, register, store, or user-level functionality control in applicable scenarios.
- **Modern Point of Sale and Commerce Scale Unit** – Because Modern Point of Sale and CSU are self-hosted by the retailer, topologies which include either of these components enable roll out of updates at a separate (and slower) cadence, and in a more granular fashion than with cloud-only topologies.
- **Feature flags** - Feature flags, configurable in Commerce headquarters, provide additional controls to selectively turn features on/off.
