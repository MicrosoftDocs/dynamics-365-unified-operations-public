---
# required metadata

title: Environment lifecycle operations - Core concepts
description: This article explains the core concepts for environment lifecycle operations when finance and operations apps are connected to Microsoft Dataverse by using Power Platform Integration.
ms.author: laswenka
author: laneswenka
ms.date: 05/02/2023
ms.topic: overview
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: johnmichalak
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.search.region: Global
# ms.search.industry:
ms.search.validFrom: 2021-10-13
ms.dyn365.ops.version: 10.0.0
---
# Environment lifecycle operations - Core concepts

[!INCLUDE[banner](../includes/banner.md)]

Every day, administrators perform lifecycle operations on their environments. These operations include common activities such as backing up and restoring data and refreshing sandbox environments with new transactions from production instances. This article provides an overview of core concepts for environment lifecycle operations and includes links to more detailed scenario articles.

To learn more about Power Platform Integration, watch our TechTalk on the [Microsoft Dynamics 365 Community](https://www.youtube.com/@MSD365Community) YouTube channel.

> [!VIDEO https://www.youtube.com/embed/HmJIuHhx3Hg]

## Terminology differences between Lifecycle Services and Power Platform admin center

For environment lifecycle operations, there are some terminology and technical differences between similar activities that admins perform in the two admin portals, Microsoft Dynamics Lifecycle Services and Power Platform admin center. The follow table is a quick reference for each operation type and explains any nuances between the two experiences.

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

When Power Platform Integration is enabled, the finance and operations apps instance is connected to a Dataverse instance. Therefore, your conceptually whole environment has two halves that you must consider. For example, a sandbox will consist of two environments: one environment in Lifecycle Services and one connected environment in Power Platform admin center.

This duality of each conceptual environment has an impact on the lifecycle operations that are listed in the previous section. The following subsection lists each end-to-end scenario and links to detailed articles that walk through each one.

### Additional resources

The following list of continually updated scenario articles provides a walkthrough for administrators:

- [Connect finance and operations apps with a new Microsoft Dataverse instance](./environment-lifecycle-connect-finops-new-dv.md)
- [Connect finance and operations apps with an existing Microsoft Dataverse instance](./environment-lifecycle-connect-finops-existing-dv.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
