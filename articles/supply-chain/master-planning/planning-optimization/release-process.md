---
title: Planning Optimization release process and release history
description: This topic provides information about the release process and release history for Planning Optimization.
author: crytt
ms.date: 09/02/2021
ms.topic: article
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-07-28
ms.dyn365.ops.version: 10.0.21
---

# Planning Optimization release process and release history

[!include [banner](../../includes/banner.md)]

Microsoft updates Planning Optimization on a monthly basis. However, based on business requirements, we occasionally release additional updates between the scheduled releases.

Each release is published to the individual regions where Planning Optimization is available. The process typically takes three days.

While Planning Optimization is being updated, master planning might run a bit more slowly than usual.

Environments that use Planning Optimization automatically receive the latest release. No user action is required: the service is automatically updated. However, no breaking-change functionality is ever automatically pushed to environments. By default, any changes that are considered breaking are turned off and must be explicitly turned on by using [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Therefore, those changes won't appear in environments until you choose to enable them.

Because notifications aren't shown when Planning Optimization is updated in your environment, you can review the release notes in the following table to determine when changes were released and what functionality they introduced. This table shows the changes that were released for Planning Optimization, whether those changes are associated with a feature from feature management, and the date of the release.

| Changes | Feature management details | Release dates |
|---|---|---|
| General performance, quality, and stability improvements. | No feature management is required. | August 25–30, 2021 |
| <p>Added **Lead time** field to planned orders.</p><p>General performance, quality, and stability improvements.</p> | No feature management is required. | August 12–17, 2021 |
| <p>Added resource type requirements for infinite capacity scheduling.</p><p>Improved resource efficiency and calendar efficiency for infinite capacity scheduling.</p><p>For more information, see [Scheduling with infinite capacity](infinite-capacity-planning.md). | <p>Available in feature management as of version 10.0.20.</p><p>Feature name: *Infinite capacity scheduling for Planning Optimization*</p> | July 6–12, 2021 |
| General quality improvements. | No feature management is required. | July 6–12, 2021 |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
