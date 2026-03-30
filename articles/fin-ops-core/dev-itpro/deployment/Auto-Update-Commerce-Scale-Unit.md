---
title: Autoupdate for Commerce Scale Unit (cloud)
description: Learn about autoupdates for Commerce Scale Unit (cloud), including limitations and an overview of downtime duration and impact.
author: johnmichalak
ms.author: johnmichalak
ms.topic: overview
ms.date: 03/09/2026
ms.reviewer: johnmichalak
ms.search.validFrom: 2020-07-13
ms.custom: 
  - bap-template
---

# Autoupdate for Commerce Scale Unit (cloud)

[!include[banner](../includes/banner.md)]

This feature currently applies to cloud-hosted Commerce Scale Unit (CSU). Self-hosted CSU isn't included and must self-update.

CSU updates are part of [One Version](../lifecycle-services/oneversion-overview.md) autoupdate. All One Version processes, policies, and schedules apply to autoupdate for CSU.

[Autoupdate configurations](../lifecycle-services/configure-service-updates.md) for environments also apply to CSUs. To [pause autoupdates](../lifecycle-services/pause-service-updates.md), CSU must be on the current release (N) or the previous one (N-1). Releases older than N-1 must be updated to be compliant.

## Limitations

The following limitations currently exist. Microsoft plans to resolve them in upcoming updates.

- In-app notifications aren't available.
- Autoupdate for CSU isn't currently available for first release customers, and isn't currently applicable for preview builds.

## Downtime duration and impact

Updates to Commerce headquarters and CSU are applied sequentially. Downtime duration is typically one hour, but it varies by data volume and region. To estimate downtime duration in your production environment, you can either self-update a CSU in your sandbox user acceptance testing (UAT) environment or review the total update duration for both Commerce headquarters and CSU in Lifecycle Services.

> [!NOTE]
> Downtime duration varies for each update and data volume. To estimate a realistic downtime duration, ensure that your sandbox UAT environment has the same data as your production environment by following the steps in [Refresh database](../database/database-refresh.md). You also need to apply the same update in the sandbox UAT environment that you plan to estimate the downtime duration for.

For retailers with a business need for redundancy, Modern POS offline capability core POS operations are available for use while disconnected from the internet, or while the cloud environment is updated. Stores operating with CSU continue to operate with support for core POS operations during cloud maintenance windows. For more information, see [Online and offline point of sale (POS) operations)](../../../commerce/pos-operations.md).

## Version support and backward compatibility

To maintain support, all in-store components must run released software that's less than 12 months old. Customers are responsible for updating self-hosted components, such as components installed in stores or in privately managed datacenters, and ensuring that the installed versions of these components are actively supported.

Updates to components hosted in the cloud continue to preserve backward compatibility for 12 months after the release date with component versions that retailers self-host, such as Modern Point of Sale, CSU, and Hardware Station. You don't need to update self-hosted components at the same time as cloud-hosted components. You can update them on a separate cadence, which gives you time to roll out updates to stores.

## Updating in-store components

You can choose to update self-hosted components manually at each store or use mass update tools such as Microsoft System Center Configuration Manager or Microsoft Intune.

By using autoupdate for CSU, you can still roll out updates to in-store components in phases by using the following controls:

- **Screen layout designer** – An administrative user in the customer organization configures and centrally manages most visual elements in POS. This configuration means that new POS operations don't automatically display on POS unless you explicitly configure them for inclusion in corresponding screen layouts. You configure screen layouts by using Screen layout designer and can make them specific to a store or POS device. For more information, see [POS user interface visual configurations](../../../commerce/pos-screen-layouts.md).
- **Functionality profiles, POS permissions, Commerce parameters** – Users typically configure many elements of POS functionality. Configure these elements through functionality profiles, POS permissions, Commerce parameters, or other controls. These controls allow for device, register, store, or user-level functionality control in applicable scenarios.
- **Modern Point of Sale and Commerce Scale Unit** – Because retailers self-host Modern Point of Sale and CSU, topologies that include either of these components enable you to roll out updates at a separate (and slower) cadence, and in a more granular fashion than with cloud-only topologies.
- **Feature flags** - Feature flags, configurable in Commerce headquarters, provide more controls to selectively turn features on or off.
