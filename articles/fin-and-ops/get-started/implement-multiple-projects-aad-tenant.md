---
# required metadata

title: Implement multiple LCS projects and production environments on the same Azure Active Directory tenant
description: 
author: ClaudiaBetz-Haubold 
manager: AnnBe
ms.date: 06/07/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope:  Operations 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-05-30 
ms.dyn365.ops.version: AX 7.0
---

# Implement multiple LCS projects and production environments on the same Azure Active Directory tenant
[!include [banner](../includes/banner.md)]

For a new Microsoft Dynamics for Finance and Operations (cloud) project, one LCS project is instantiated on an AAD tenant which provides access to one production instance. In rare cases, it may be necessary to have multiple production instances in parallel to handle the requirements of a specific implementation. By creating multiple LCS projects against the same AAD tenant, you can have multiple production instances. The most common scenarios where this would occur are:

- Global implementations with data residency, latency, or data volume requirements that can't be met within one instance
- Different business units in an organization that are implementing Finance and Operations separately as independent applications

Creating additional LCS projects on a common AAD tenant requires manual intervention by the Dynamics Service Engineering (DSE) team. This approach should only be pursued if a single instance strategy is truly not feasible. Before one or more additional LCS projects are created, the customer must provide the business case and acknowledge that they understand all implications of the approach. This process should be started as early in the implementation lifecycle as possible. If the customer decides to proceed, they should inform the FastTrack Solution Architect assigned to their project of this requirement. If they do not have a Solution Architect assigned, they should open a support ticket. 

## Licensing requirements
In the case of multiple LCS implementation projects on the same AAD tenant, each LCS implementation project must satisfy the minimum licensing requirements. For example, if there are three implementation projects on the same AAD tenant, the customer must purchase no less than three times the minimum number of subscription licenses. At the time of publishing this article, the minimum license requirement is 
20 full user licenses, resulting in a minimum requirement of 60 licenses if the customer wants to run three LCS implementation projects on the same AAD tenant. 
Because the licenses are associated with the AAD tenant, each LCS project will display the entire number of licenses in the **Subscriptions available** form even though it is only entitled to use the portion of licenses allocated to it. This allocation of license to LCS projects must be documented outside of the system.
Users who access multiple environments in parallel must be separately licensed for each environment. For more licensing information, download the [Licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409). 

## Disadvantages when operating multiple LCS projects
There are some disadvantages to operating multiple LCS projects. These include:
- Master data is not shared.
- Intercompany transactions are not supported.
- Integrations must be configured in each LCS project.
- Separate Bring your own database (BYOD) instances are required for each LCS project.
- User Acceptance Test (UAT) must be conducted on each instance even if the code is the same. This is because of the differences that can occur across the LCS projects, even if the code base is common. One source of differences can be the integration setup and BYOD configuration that needs to be done separately in each LCS project and therefore must be tested in each LCS project. Additionally, there can be data variations, different application configurations per region which might impact functionality, and different data centers that might support a different set of Azure services.
- VSTS must be configured in each LCS project; using the same VSTS project is an option that makes sense when customizations/code is shared.

## Advantages when operating multiple LCS projects
There are also advantages to operating multiple LCS projects. These include:
- Data centers can be selected per LCS project to provide best latency experience
- Data centers can be selected per LCS project to satisfy statutory data residency requirements
- There is more flexibility to schedule servicing operations such as code deployments and upgrades 

## How to request multiple LCS projects on the same AAD tenant
If your solution requires multiple LCS projects on the same AAD tenant, all LCS projects except for the initial one, must be provisioned on demand by the Dynamics Service Engineering (DSE) team. You should raise this requirement as early as possible, ideally during the onboarding of the project. For more information, see [Onboard and Finance and Operations project](../imp-lifecycle/onboard.md). To request additional LCS implementation projects, create a support request by using the Support portal in LCS and provide the following information:

- Business justification
- Enterprise and project structure including 
- Name of the Implementation project
- Licenses breakdown per LCS project
- Customer confirmation that they understand the implications of multiple LCS projects on the same AAD tenant

