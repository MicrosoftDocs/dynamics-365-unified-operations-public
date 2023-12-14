---
# required metadata

title: Human Resources to resource integration
description: This article describes the details on Human resources workers to bookable resource integration. 
author: tulsijhaveri
ms.date: 12/05/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tulsijhaveri
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---


# Human Resource to resource integration

Human Resources to Resource Integration allows organizations to integrate their worker information to enhance resource manager's experience by bringing together worker information including their skills and proficiencies to find the best resources for a requirement. This functionality alleviates the pain of double entry and maintenance of workers and characteristics in Project Operations and other areas that use universal resource scheduling solution for resource scheduling.

This feature enables resource managers to:

- Utilize workers that exist in Human Resources to set up as bookable resources in Project Operations.
- Find or book resources by skills and certificates associated with the worker in Human Resources.

### Integration terminology

| Human Resources | Resource Management |
| --- | --- |
| Worker | Resource |
| Skills | Characteristics |
| Certificates | Characteristics |
| Rating models | Proficiency models |

### Integration dataflow


- _Human Resources_: Workers and related Skill/Certificate is created.
- _Integration App_: Creates new skills/certificate for Resource associated with the worker in Dataverse
- _Project Operations_: Resource Manager reviews updated characteristics (Skills/Certificates)


### Process

Human Resources to resource integration uses Dual-write. For more information, see [Dual-write](/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-overview.md). Dual write infrastructure provides near-real-time integration from Human Resources to Resource management. For more information, see [Guidance for dual-write setup](/fin-ops-core/dev-itpro/data-entities/dual-write/connection-setup.md).

### Prerequisites

Power Platform integration is a feature that's enabled in Microsoft Dynamics Lifecycle Services. It lets administrators link their finance and operations environments with new or existing Microsoft Power Platform–based environments. To learn more, see [Enable Power Platform Integration](/fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration).md

#### Install and connect Dynamics 365 applications
Some of the following Dual-write solutions may be required based on your organization's integration points:

- Dual-write core solution (Required)
- Dual-write Dynamics 365 Human Resources (Required)
- Dual-write Finance
- Dual-write Supply Chain 
- Dynamics 365 Human Resources common tables (Required)
- Finance and operations virtual entity
- Microsoft Dynamics 365 Project Operations

> [!NOTE]
> The Dual-write solution(s) needed depends on the customer's scenario whether using the integration with Field service, Project Operations, or Scheduling.

### Install solution from Power platform admin center 

Follow these steps to install the integration from the Power platform admin center:
1. Go to **Power Platform admin center \> Dynamics 365 apps**.
2. **Install app** - in the **Install Dynamics 365 apps**, select **Dynamics 365 Human Resources Integration to URS**.
3. Click **Next**. Agree to terms of service to install the app.
4. The solution installation is in progress with the **Installing** status.
5. After the solution is installed, the status is **Installed**.

### Install Dual-write packages

The Dual-write Human Resources package contains the solutions and maps that are required to sync Human Resources data. For more information, see [Dual-write Human Resources](/fin-ops-core/dev-itpro/data-entities/dual-write/separated-solutions#dual-write-human-resources).

### Enable dual-write maps

Dual-write is an out-of-box infrastructure that provides near-real-time interaction between customer engagement apps and finance and operations apps. For more information, see [Enable dual-write for existing finance and operations apps](/fin-ops-core/dev-itpro/data-entities/dual-write/enable-dual-write).

### Integration process

Installing and applying the Human Resources to URS Integration enables organizations to integrate the catalog of skills, certificates, and related information in Human Resources to the characteristics table on Dataverse; this also includes mapping for Rating models and rating levels.

In addition to providing dual-write maps, this solution also includes virtual entities. Because this solution takes dependency on virtual entities for skills and certificates, those are automatically generated when the dual-write package completes installing.

Relevant business events are registered in Human Resources and when there are changes to those entities, Dataverse is able to consume those changes.

### Create skills 

You can track your worker's skills in Dynamics 365 Human Resources. You can also specify the skills that are required for a specific job. For more information, see [Create skills](hr-develop-skills).

### Create certificates 

You can track worker's Certificates in Dynamics 365 Human Resources by creating a library of certificate types and certificates. Those certificates can be added to a worker record to indicate what certificates are accredited to the worker. You can also specify the certificates that are required for a specific job.

### Define skills and proficiencies in Project Operations

Skills are resource characteristics that are shared between Dynamics 365 Project Operations and if present, Dynamics 365 Field Service. For more information, see [Defining skills and proficiencies](/project-operations/resource-management/define-skills-proficiencies).

### Turn off integration

When the integration is turned off, the field on bookable resource is removed, the data associated with field is also removed. If there were any characteristics added through the integration on the worker, those will remain on the bookable resource after the integration is turned off.

