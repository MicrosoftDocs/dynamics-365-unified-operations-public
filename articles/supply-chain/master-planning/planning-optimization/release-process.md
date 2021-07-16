---
title: Release process for Planning Optimization
description: This topic provides information about the release process for Planning Optimization.
author: crytt
ms.date: 7/16/2021
ms.topic: article
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-07-16
ms.dyn365.ops.version: 10.0.20
---

# Release process for Planning Optimization

[!include [banner](../../includes/banner.md)]

Microsoft releases changes to the Planning Optimization monthly. However, based on business needs, an ad-hoc release can be processed between the regular releases.

Each release is published into the individual regions in which Planning Optimization is available. The process normally takes three days.

Note that during the release, master planning may run longer than usual.

Environments that use Planning Optimization automatically get the latest release. No user action is needed, the service is updated on its own. It is important to note that no breaking change functionalities are pushed to environments automatically. If a change is considered a breaking change, it will be associated with a feature in Feature management and therefore these changes will not appear on environments until they are enabled in Feature Management. 
 
Since notifications are not displayed when Planning Optimization is updated on your environment, you can use the following release notes to review when changes were released and what functionality was introduced.

## Release notes

The table below provides information about changes that was released to Planning Optimization, whether changes are associated with a feature from Feature Management, and the date of the release.

| Changes | Release date |
| --- | --- |
| Resource type requirement support by infinite capacity scheduling. For details about infinite capacity scheduling, see [Scheduling with infinite capacity](infinite-capacity-planning.md).<br> Available in Feature management from version 10.0.20: Infinite capacity scheduling for Planning Optimization | July 6, 2021 |
| Resource efficiency and calendar efficiency support by infinite capacity scheduling. For details about infinite capacity scheduling, see [Scheduling with infinite capacity](infinite-capacity-planning.md).<br> Available in Feature management from version 10.0.20: Infinite capacity scheduling for Planning Optimization | July 6, 2021 |
| General quality improvements | July 6, 2021 |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]