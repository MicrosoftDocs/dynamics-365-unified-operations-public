---
title: Release process for Planning Optimization
description: This topic provides information about the release process for Planning Optimization.
author: crytt
ms.date: 7/28/2021
ms.topic: article
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-07-28
ms.dyn365.ops.version: 10.0.20
---

# Release process for Planning Optimization

[!include [banner](../../includes/banner.md)]

Microsoft updates Planning Optimization on a monthly basis. However, based on business needs, ad-hoc releases are sometimes be processed between the regular releases.

Each release is published into the individual regions in which Planning Optimization is available. The process normally takes three days.

Note that during the release, master planning may run a bit slower than usual.

Environments that use Planning Optimization automatically get the latest release. No user action is needed, the service is updated automatically. However, no breaking-change functionalities are ever pushed to environments automatically. If a change is considered to be a breaking change, it will be turned off by default, and must be explicitly enabled using [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Therefore, these changes will not appear on environments until you choose to enable them.

Because notifications are not displayed when Planning Optimization is updated on your environment, you can use the following release notes to review when changes were released and what functionality was introduced.

## Release notes

The following table provides information about changes that were released for Planning Optimization, whether those changes are associated with a feature from feature management, and the date of the release.

| Changes | Feature management details | Release date |
| --- | --- | --- |
| Resource type requirements for infinite capacity scheduling<br><br>Resource efficiency and calendar efficiency for infinite capacity scheduling<br><br>See also: [Scheduling with infinite capacity](infinite-capacity-planning.md) | Available in feature management from version 10.0.20.<br><br>Feature name: *Infinite capacity scheduling for Planning Optimization* | July 6, 2021 |
| General quality improvements | No feature management required. | July 6, 2021 |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]