---
# required metadata

title: Human resources to bookable resource integration
description: This article provides details about the integration of Microsoft Dynamics 365 Human Resources workers to bookable resources.
author: tulsijhaveri
ms.date: 5/15/2024
ms.topic: article
ms.reviewer: twheeloc
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

# Human resources to bookable resource integration

Human resources to bookable resource integration enables organizations to integrate their worker information. By bringing together worker information, including information about skills and proficiencies, the integration enhances the resource manager's experience and helps them find the best resources for a requirement. This functionality alleviates the pain of double entry and maintenance of workers and characteristics. This data no longer has to be entered and maintained in both Microsoft Dynamics 365 Project operations and other areas that use the Universal Resource Scheduling (URS) solution for resource scheduling.

This feature enables resource managers to:

- Set up existing workers in Dynamics 365 Human Resources as bookable resources in Project Operations.
- Find or book resources based on the skills and certificates that are associated with workers in Human resources.

## Integration terminology

| Human Resources | Resource management |
| --- | --- |
| Worker | Resource |
| Skills | Characteristics |
| Certificates | Characteristics |
| Rating models | Proficiency models |

## Integration dataflow

1. **Human resources** - Workers and their related skills and certificates are created.
2. **Integration app** - New skills/certificates are created for the resource that's associated with a worker in Dataverse.
3. **Project operations** - The resource manager reviews the updated characteristics (skills/certificates).

![Integration Dataflow](./media/Dualwrite-1.png)

## Process

Human resources to resource integration uses dual-write. For more information, see [Dual-write](../fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-overview.md). The dual-write infrastructure provides near-real-time integration from Human Resources to Resource management. For more information, see [Guidance for dual-write setup](../fin-ops-core/dev-itpro/data-entities/dual-write/connection-setup.md).

## Prerequisites

The Power Platform integration feature is enabled in Microsoft Dynamics Lifecycle Services. It lets administrators link their finance and operations environments with new or existing Microsoft Power Platform–based environments. For more information, see [Enable Power Platform integration](../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md).

### Install and connect Dynamics 365 applications

Some of the following dual-write solutions might be required, depending on your organization's integration points:

- Dual-write core solution (Required)
- Dual-write Dynamics 365 Human Resources (Required)
- Dual-write Finance
- Dual-write Supply Chain 
- Dynamics 365 Human Resources common tables (Required)
- Finance and operations virtual entity
- Microsoft Dynamics 365 Project Operations

> [!NOTE]
> The dual-write solutions that are required depend on the customer's scenario: whether they're using the integration with Dynamics 365 Field Service, Project Operations, or Scheduling.

## Install the solution from Power Platform admin center 

Follow these steps to install the integration from Power Platform admin center:

1. Sign in to Power Platform admin center.
2. On the left navigation, under **Resources**, select **Dynamics 365 apps**.
3. Select **Install app**.
4. In the **Install Dynamics 365 apps** dialog box, select **Dynamics 365 Human Resources integration to URS**, and then select **Next**.

![Install Dynamics 365 Human Resources integration to URS](./media/Installing.jpg)

5. Agree to the terms of service to install the app.

    While solution installation is in progress, the status is **Installing**. After the solution is installed, the status is changed to **Installed**.

![Status is Installing](./media/Status-installing.jpg)   

## Install dual-write packages

The dual-write Human resources package contains the solutions and maps that are required to sync Human resources data. For more information, see [Dual-write Human resources](../fin-ops-core/dev-itpro/data-entities/dual-write/separated-solutions.md#dual-write-human-resources).

## Enable dual-write maps

Dual-write is an out-of-box infrastructure that provides near-real-time interaction between customer engagement apps and finance and operations apps. For more information, see [Guidance for dual-write setup](../fin-ops-core/dev-itpro/data-entities/dual-write/connection-setup.md).

> [!IMPORTANT]
> It's recommended to refresh the entity list to ensure the most updated versions of entities are reflected.

### Apply solution
1. Go to **Data management** > **Dual-write**.
2. Select **Apply solution**.
3. Apply the following solutions: 
  - Dynamics 365 Human resources entity maps
  - HCM Scheduling 

![Dual write Apply Solution](./media/DW_ApplySolution.png)


### Run Dual-write table maps
Before you start dual-write on an entity, you can run an initial synchronization to handle existing data on both Finance and operations apps and customer engagement apps. For more information, see [Enable table maps for dual-write](../fin-ops-core/dev-itpro/data-entities/dual-write/enable-entity-map.md). 

Select appropriate table maps to run the dual-write maps for the worker to bookable resource integration. 
To enable worker to bookable resource integration, select the following: 
- Worker (cdm_workers)
- Skills (Dual-write) (characteristics)
- Certificate type (Dual-write) (characteristics)
- Rating models (ratingmodels)
- Rating level (ratingvalues)

## Integration process

By installing and applying the **Dynamics 365 Human Resources integration to URS** solution, organizations can integrate the catalog of skills, certificates, and related information in Human resources with the characteristics table in Dataverse. The integration also includes mapping for rating models and rating levels.

In addition to providing dual-write maps, the solution includes virtual entities. Because the solution takes a dependency on virtual entities for skills and certificates, those skills and certificates are automatically generated after the dual-write package is installed.

Relevant business events are registered in Human resources. Then, when there are changes to the entities, Dataverse can consume those changes.

> [!NOTE]
> The Dynamics 365 Human Resources integration to URS app allows the **Worker** field to be editable when a new bookable resource is created. The **Worker** field isn't editable for an existing resource or after the record is saved. However, linking an existing resource to a worker can be manually made in dataverse through the Power Platform.

## Create skills

You can track your workers' skills in Human resources. You can also specify the skills that are required for a specific job. For more information, see [Create skills](hr-develop-skills.md).

## Create certificates

You can track workers' certificates in Human resources by creating a library of certificate types and certificates. Certificates can then be added to a worker record to indicate the certificates that the worker has earned. You can also specify the certificates that are required for a specific job.

## Define skills and proficiencies in Project Operations

Skills are resource characteristics that are shared between Project Operations and, if it's present, Field service. For more information, see [Defining skills and proficiencies](/dynamics365/project-operations/resource-management/define-skills-proficiencies).

## Turn off the integration

If the integration is turned off, the field on bookable resources is removed. The data that's associated with the field is also removed. Any characteristics that were added on the worker through the integration remain on the bookable resource after the integration is turned off.
