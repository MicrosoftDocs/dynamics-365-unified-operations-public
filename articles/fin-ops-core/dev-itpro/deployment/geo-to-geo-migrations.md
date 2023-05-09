---
title: Geo-to-geo migrations
description: This article provides an overview of how to move between geographies.
author: matapg007
ms.author: matgupta
ms.reviewer: johnmichalak
ms.service: dynamics-365-finance
ms.topic: how-to
ms.date: 04/30/2023
ms.custom:
---
##  Geo to geo migration overview

To support data residency, Microsoft Dynamics 365 finance and operations apps and Lifecycle Services (LCS) are generally available in specific geographies. Customers can migrate their workload from one geography to another. This article provides and overview of the process and the considerations.

Moving between geographies involve two separate processes:

- [Finance and operations apps environment migration](environment-migration-process.md) - this feature lets you move your finance and operations environments that are in a single tenant from one geography (or geo) to another. No changes to the user interface or version occur as part of the move.
- [LCS project migration manager](../lifecycle-services/project-migration-manager.md) - this feature lets you move your Lifecycle Services project data from one geography to another geography that meets your requirements.
 

Start planning the migration by assessing whether you want to migrate only environments, only LCS project or both.

##  General considerations

Organizations looking to migrate environments and data from one geography to another need to consider various aspects mentioned below before actual migration.

### Feature parity

Make sure you review the [availability of features in the selected target geography](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/deployment/deployment-options-geo#feature-availability-in-local-geographies) before deciding on which geography to deploy into. If certain features are not available in target geo, associated functionality will not work in target geo after migration so plan migration activity accordingly.

Commerce isn't available in all target geographies. If you have Commerce components enabled, your LCS project migration won't be scheduled if you're migrating to one of the target geographies where Commerce isn't available.

### Sovereign data resident geographies

Migrations into or out of a sovereign cloud environment (for example, US Government Community Cloud [GCC] and China) aren't supported.

## LCS project migration considerations

Refer to [LCS project migration manager - Considerations](../lifecycle-services/project-migration-manager.md#considerations) to learn details.

## Environment migration considerations

Refer to [Finance and operations apps environment migration - Considerations](environment-migration-process.md#considerations) to learn details.
