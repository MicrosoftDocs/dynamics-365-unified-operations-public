---
# required metadata

title: Access and security
description: Access list hierarchy and security role determine what menu items and data a user is granted access to in Cost accounting. This topic focuses on what a cost object controller role is.  
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

## Cost object controller role 

[!include[banner](../includes/banner.md)]

The **Cost control** workspace is a central point were managers can see performance of their cost objects. This means that the managers can consume Cost accounting data without being cost accountants. For security reasons, the managers should only be allowed to see the Cost accounting data that is related to the specific cost objects for which they are responsible.

There are four unique roles in Cost accounting. This topic focuses on how to assign a **Cost object controller** role to a manager. 

| Role name               | License      |
|-------------------------|--------------|
| Cost accounting manager | Activity     |
| Cost accountant         | Operations   |
| Cost accountant clerk   | Operations   |
| Cost object controller  | Team members |

When a **Cost object controller** role is assigned to a manager, the manager can:

-   Access the **Cost control** workspace (Client)

    -   Drill through and have view access to the pages that support the drill-through experience.

-   Access the **Cost control** workspace (Mobile application)


> [!NOTE]
> The **Cost object controller** role does control which cost objects the user can access and see data for. Row-level security is obtained via **Dimension hierarchies** and **Access list hierarchy**.

## Grant access to a user 
Here is an example of how a dimension hierarchy can look like.

Dimension hierarchy details

| Dimension hierarchy name | Dimension    | Dimension hierarchy type name      | Access list hierarchy |
|--------------------------|--------------|------------------------------------|-----------------------|
| Organization             | Cost centers | Dimension classification hierarchy | **Yes**               |

You can use the **Users** FastTab in the hierarchy designer to insert one or several User IDs on each node.

|              | **Users**        | Dimension member ranges |                     |
|--------------|------------------|-------------------------|---------------------|
| Nodes        | User ID          | From dimension member   | To dimension member |
| Organization | Benjamin, Claire |                         |                     |
| &nbsp;&nbsp;Admin              | April            |                         |                     |
| &nbsp;&nbsp;&nbsp;&nbsp;Finance             | Alicia           | CC002                   | CC003               |
|              |                  | CC007                   | CC007               |
| &nbsp;&nbsp;&nbsp;&nbsp;HR              | Arnie            | CC001                   | CC001               |
| &nbsp;&nbsp;Production             | David            |                         |                     |
| &nbsp;&nbsp;&nbsp;&nbsp;Packaging    Ellen            | CC005                   | CC005               |
| &nbsp;&nbsp;&nbsp;&nbsp;Assembly     | Chris            | CC006                   | CC006               |

> [!NOTE] 
> Cost accountants should be assigned to the top level of the hierarchy so they can see all entries in Cost accounting.

Before the **Access list hierarchy** and its security settings can be applied, the parameter **Enable view access for cost object dimension members** on **Cost accounting/Setup/Parameters/General** must be set to **Yes**.

The **Access list hierarchy** settings are used to control data displayed in following areas.

-   **Cost control** workspace (Client)

    -   Data on the pages that are used to drill through

-   **Cost control** workspace (Mobile application)

    -   Balances in cards

-   Microsoft Power BI

    -   Data displayed in Power BI visualizations

    -   Data Power BI visualizations embedded into Microsoft Dynamics 365 for Finance and Operations, Enterprise edition client

> [!IMPORTANT] 
> Before **Access list hierarchy** can affect data in Power BI, **Access list hierarchy** and **Row-level security** in Power BI need to be paired. For more informaiton, see [Set up security for Cost accounting content pack](/dynamics365/operations/dev-itpro/analytics/setup-security-cost-accounting-content-pack).

> [!IMPORTANT] 
> This topic shows the prerequisites that must be in place before you use the **Cost control** workspace.  

For more information, see [Dimension hierarchy](dimension-hierarchy.md). 



