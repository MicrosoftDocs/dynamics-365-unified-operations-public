---
title: Environment lifecycle operations - Core concepts
description: Learn about the core concepts for environment lifecycle operations when finance and operations apps are connected to Microsoft Dataverse.
author: laneswenka
ms.author: laswenka
ms.topic: overview
ms.date: 02/23/2024
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-10-13
ms.search.form:
ms.dyn365.ops.version: 10.0.0
---
# Environment lifecycle operations - Core concepts

[!INCLUDE[banner](../includes/banner.md)]

Every day, administrators perform lifecycle operations on their environments. These operations include common activities such as backing up and restoring data and refreshing sandbox environments with new transactions from production instances. This article provides an overview of core concepts for environment lifecycle operations and includes links to more detailed scenario articles.

To learn more about Power Platform Integration, watch our TechTalk on the [Microsoft Dynamics 365 Community](https://www.youtube.com/@MSD365Community) YouTube channel.

> [!VIDEO https://www.youtube.com/embed/HmJIuHhx3Hg]

## Terminology differences between Lifecycle Services and Power Platform admin center

For environment lifecycle operations, there are some terminology and technical differences between similar activities that admins perform in the two admin portals, Microsoft Dynamics Lifecycle Services and Power Platform admin center. The following table is a quick reference for each operation type and explains any nuances between the two experiences.

| Lifecycle operation | Lifecycle Services terminology | Power Platform admin center terminology | Comments |
| ------------------- | ------------------------------ | --------------------------------------- | -------- |
| Create | Deploy | Provision | |
| Copy | Database Refresh | Copy | |
| Backup | Database Export | Backup (Custom or System-defined) | |
| Restore | Point-in-time restore | Restore (Custom or System-defined) | |
| Reset | Not applicable | Reset | This operation is blocked for connected Dataverse instances, because finance and operations apps have no equivalent. |
| Convert to Production | Not applicable | Convert to Production | |
| Delete | Deallocate/Delete | Delete | This operation is blocked for connected Dataverse instances until finance and operations apps are removed. |

## Scenarios supported when Power Platform Integration is enabled

When Power Platform Integration is enabled, the finance and operations apps instance is connected to a Dataverse instance. Therefore, your conceptually whole environment has two halves that you must consider. For example, a sandbox consists of two environments: one environment in Lifecycle Services and one connected environment in Power Platform admin center.

This duality of each conceptual environment has an impact on the lifecycle operations that are listed in the previous section. The following subsection lists each end-to-end scenario and links to detailed articles that walk through each one.

### Additional resources

The following list of continually updated scenario articles provides a walkthrough for administrators:

- [Connect finance and operations apps with a new Microsoft Dataverse instance](./environment-lifecycle-connect-finops-new-dv.md)
- [Connect finance and operations apps with an existing Microsoft Dataverse instance](./environment-lifecycle-connect-finops-existing-dv.md)
- [Change the type of connected environments](./environment-lifecycle-change-env-type-dv.md)
- [Database and environment movements when Power Platform Integration is enabled](./environment-lifecycle-database-movements.md)
- [Set up developer cloud-hosted environments by using Power Platform Integration](./environment-lifecycle-development-environments.md)
- [Edit the properties of connected Dataverse environments](./environment-lifecycle-edit-properties-dv.md)
- [Delete environments when Power Platform Integration is enabled](./environment-lifecycle-delete-env.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
