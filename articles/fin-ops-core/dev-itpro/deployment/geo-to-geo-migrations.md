---
title: Geo to geo migration overview
description: This article provides an overview of the process for moving between geographies.
author: matapg007
ms.author: matgupta
ms.reviewer: johnmichalak
ms.service: dynamics-365-finance
ms.topic: how-to
ms.date: 05/10/2023
ms.custom:
---
# Geo to geo migration overview

To support data residency, Microsoft Dynamics 365 finance and operations apps and Microsoft Dynamics Lifecycle Services are generally available in specific geographies. Customers can migrate their workload from one geography to another. This article provides an overview of the process and the considerations.

Movement between geographies involves two separate processes:

- [Finance and operations apps environment migration](environment-migration-process.md) – Use this feature to move your finance and operations apps environments between geographies.
- [Lifecycle Services project migration manager](../lifecycle-services/project-migration-manager.md) – Use this feature to move your Lifecycle Services project data between geographies.

To start planning for the migration, assess whether you want to migrate only environments, only Lifecycle Services projects, or both.

## General considerations

Organizations that want to migrate environments and data from one geography to another must consider the following aspects before actual migration.

### Feature parity

Be sure to review the [availability of features in the selected target geography](deployment-options-geo.md#feature-availability-across-geographies) before you decide which geography to deploy in. If any features aren't available in the target geography, associated functionality won't work in that geography after migration. Therefore, plan the migration activity accordingly.

Dynamics 365 Commerce isn't available in all target geographies. If you have Commerce components enabled, your Lifecycle Services project migration won't be scheduled if you're migrating to one of the target geographies where Commerce isn't available.

### Sovereign data resident geographies

Migrations into or out of a sovereign cloud environment (for example, US Government Community Cloud \[GCC\] and China) aren't supported.

### Lifecycle Services project migration considerations

For more information, see [Lifecycle Services project migration manager - Considerations](../lifecycle-services/project-migration-manager.md#considerations).

## Environment migration considerations

For more information, see [Finance and operations apps environment migration - Considerations](environment-migration-process.md#considerations).
