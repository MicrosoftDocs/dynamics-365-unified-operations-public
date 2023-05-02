---
# required metadata

title: Environment lifecycle operations - Core concepts
description: This article explains the core concepts in respect to environment lifecycle operations when Finance and Operations apps are connected to Microsoft Dataverse using Power Platform Integration. 
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

Every day administrators perform lifecycle operations on their environments. This includes common activities like backup and restore, refreshing sandbox environments with new transactions from Production instances, and more. This article provides an overview for environment lifecycle opeations core concepts, and includes links to more detailed scenario articles.

To learn more about Microsoft Power Platform Integration, watch our TechTalk on the [Microsoft Dynamics 365 Community](https://www.youtube.com/watch?v=HmJIuHhx3Hg) YouTube channel.

> [!VIDEO https://www.youtube.com/embed/HmJIuHhx3Hg]

## Terminology differences between Lifecycle Services and Power Platform admin center

When it comes to environment lifecycle operations, there are some terminology and technical differences between similar activities that admins perform in the two different admin portals. The table below is a quick reference for each operation type and explains any nuances between the two experiences.

| Lifecycle Operation | LCS Terminology | PPAC terminology | Comments |
| ----------- | ----------- |----------- |----------- |
| Create | Deploy | Provision | |
| Copy | Database Refresh | Copy | |
|Backup | Database Export | Backup (Custom or System-defined)| |
| Restore | Point-in-time restore | Restore (Custom or System-defined)| |
| Reset | Not applicable | Reset| This operation is blocked for connected Dataverse instances since Finance and Operations apps has no equivalent |
| Convert to Production | Not applicable | Convert to Production | |
| Delete | Deallocate / Delete | Delete | This operation is blocked for connected Dataverse instances until after Finance and Operations apps is removed |

## Scenarios supported with Power Platform Integration enabled

When Power Platform Integration is enabled, the finance and operations apps instance is connected to a Microsoft Dataverse instance. There are now two halves to consider for your conceptually whole environment. A Sandbox, for example, will consist of two environments, one in Lifecycle Services and another connected environment in Power Platform admin center. 

With this duality of environments for each conceptual environment, there are impacts to the lifecycle operations listed in the previous section. Below find a table of contents with respect to each end to end scenario and links to detailed articles walking through each one.

### Additional resources

The followin list of continually updated scenario articles provides a walkthrough for administrators.

1. [Connect Finance and Operations apps with a new Microsoft Dataverse instance](./environment-lifecycle-connect-finops-new-dv.md)
2. [Connect Finance and Operations apps with an existing Microsoft Dataverse instance](./environment-lifecycle-connect-finops-existing-dv.md)
3. Enable Dual-write applications on a connected environment
4. Delete Finance and Operations apps that are connected to Microsoft Dataverse
5. Delete Microsoft Dataverse instances
6. Correcting differences between Dual-write and Power Platform Integration
7. Go live process with Power Platform Integration involved
8. Refresh sandbox with latest database from Production with Power Platform Integration involved
9. Point in time restore with Power Platform Integration involved
10. Edit environment properties of Microsoft Dataverse when Power Platform Integration is involved
11. Setup developer cloud-hosted environments with Power Platform Integration

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
