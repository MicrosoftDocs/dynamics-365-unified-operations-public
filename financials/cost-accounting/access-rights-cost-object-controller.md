---
# required metadata

title: Define access rights for cost object controllers
description: This topic provides information about access rights for cost object controllers. 
author: YuyuScheller
manager: AnnBe
ms.date: 06/24/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CAMCostControlWorkspace, CAMParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: YuyuScheller
ms.search.scope:  AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: YuyuScheller
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

## Access rights of a cost object controller

[!include[banner](../includes/banner.md)]

The **Cost control** workspace is a central point where managers can view the performance of their cost objects. This workspace lets managers consume Cost accounting data even though they aren't cost accountants. For security reasons, managers should be allowed to see only the Cost accounting data that is related to the specific cost objects that they are responsible for.

There are four unique roles in Cost accounting.

| Role name               | License      |
|-------------------------|--------------|
| Cost accounting manager | Activity     |
| Cost accountant         | Operations   |
| Cost accountant clerk   | Operations   |
| Cost object controller  | Team members |

This topic explains how to assign the **Cost object controller** role to a manager.

When the **Cost object controller** role is assigned to a manager, the manager can perform the following tasks:

- Access the **Cost control** workspace (in the client).

    - Drill through and have view access to the pages that support the drill-through experience.

- Access the **Cost control** workspace (in the mobile application).

> [!NOTE]
> The **Cost object controller** role doesn't control which cost objects the user can access and view data for. Row-level security is provided via dimension hierarchies and the Access list hierarchy.

## Grant access rights
The following example shows what a dimension hierarchy can look like.

**Dimension hierarchy details**

| Dimension hierarchy name | Dimension    | Dimension hierarchy type name      | Access list hierarchy |
|--------------------------|--------------|------------------------------------|-----------------------|
| Organization             | Cost centers | Dimension classification hierarchy | **Yes**               |

You can use the **Users** FastTab in the hierarchy designer to insert one or more user IDs on each node.

|                                   | Users            | Dimension member ranges   |                         |
|-----------------------------------|------------------|---------------------------|-------------------------|
| **Nodes**                         | **User ID**      | **From dimension member** | **To dimension member** |
| Organization                      | Benjamin, Claire |                           |                         |
| &nbsp;&nbsp;Admin                 | April            |                           |                         |
| &nbsp;&nbsp;&nbsp;&nbsp;Finance   | Alicia           | CC002                     | CC003                   |
|                                   |                  | CC007                     | CC007                   |
| &nbsp;&nbsp;&nbsp;&nbsp;HR        | Arnie            | CC001                     | CC001                   |
| &nbsp;&nbsp;Production            | David            |                           |                         |
| &nbsp;&nbsp;&nbsp;&nbsp;Packaging | Ellen            | CC005                     | CC005                   |
| &nbsp;&nbsp;&nbsp;&nbsp;Assembly  | Chris            | CC006                     | CC006                   |

> [!NOTE]
> Cost accountants should be assigned to the top level of the hierarchy, so that they can see all entries in Cost accounting.

Before the Access list hierarchy and its security settings can be applied, the **Enable view access for cost object dimension members** option must be set to **Yes** on the **General** tab of the **Cost accounting parameters** page (**Cost accounting** > **Setup** > **Parameters**).

The settings for the Access list hierarchy are used to control the data that is shown in following areas:

- **Cost control** workspace (in the client):

    - Data on the pages that are used for drill-through

- **Cost control** workspace (in the mobile application):

    - Balances in cards

- Microsoft Power BI:

    - Data that is shown in Power BI visualizations
    - Data Power BI visualizations that are embedded in the Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, client

> [!IMPORTANT]
> - Before the Access list hierarchy can affect data in Power BI, the Access list hierarchy and row-level security in Power BI must be paired. For more information, see [Set up security for Cost accounting content pack](/dynamics365/operations/dev-itpro/analytics/setup-security-cost-accounting-content-pack).
> - This topic shows the prerequisites that must be in place before you can use the **Cost control** workspace.

For more information, see [Dimension hierarchy](dimension-hierarchy.md).
