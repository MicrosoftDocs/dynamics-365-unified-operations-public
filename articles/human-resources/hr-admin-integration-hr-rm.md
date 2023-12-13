---
# required metadata

title: HR to Resource Integration
description: This article describes the details on Human resources workers to bookable resource integration. 
author: tulsijhaveri
ms.date: 12/05/2023
ms.topic: article
ms.prod: 
ms.technology: 
---
# HR to Resource Integration

Human Resources to Resource Integration allows organizations to integrate their worker information to enhance Resource manager's experience by bringing together worker information including their skills and proficiencies to find the best resources for a requirement. This functionality will alleviate the pain of double entry and maintenance of workers and characteristics in Project Operations and other areas that use Universal Resource Scheduling (URS) solution for resource scheduling.

This feature will enable resource managers to:

- Utilize workers that exist in Human Resources to set up as bookable resources in Project Operations.
- Find or book resources by skills and certificates associated with the worker in Human Resources.

## Integration Terminology

| **HR** | **RM** |
| --- | --- |
| Worker | Resource |
| Skills | Characteristics |
| Certificates | Characteristics |
| Rating models | Proficiency models |

## Integration Dataflow


- _Human Resources_: Workers and related Skill/Certificate is created.
- _Integration App_: Creates new skills/certificate for Resource associated with the worker in Dataverse
- _Project Operations_: Resource Manager reviews updated characteristics (Skills/Certificates)

![UpdateResourceSkills](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/129548753/97e486dc-516d-4f60-9c8e-7e949c0dd901)


## Process

Human Resources to Resource Integration uses [Dual-write](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-overview) infrastructure to provide near-real-time integration from Human Resources to Resource management. For more information, see [Guidance for dual-write setup](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/connection-setup).

### Pre-requisites:

Power Platform Integration is a feature that's enabled in Microsoft Dynamics Lifecycle Services. It lets administrators link their finance and operations environments with new or existing Microsoft Power Platform–based environments. 
To learn more and for detailed process, see [Enable Power Platform Integration](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration)

#### Install and connect Dynamics 365 applications

Some of the following Dual-write solutions may be required based on your organization's integration points:

- Dual-write core solution (Required)
- Dual-write Dynamics 365 Human Resources (Required)
- Dual-write Finance
- Dual-write Supply Chain solution
- Dynamics 365 HR Common Tables (Required)
- Finance and Operations Virtual Entity
- Microsoft Dynamics 365 Project Operations

> [!NOTE]
> The Dual-write solution(s) needed will depend on the customers scenario whether using the integration with Field Service, Project Operations, Scheduling, etc.

### Install Solution from PPAC

- Navigate to: **Power Platform admin center \> Dynamics 365 apps**
- Select **Install app**
- In the Install Dynamics 365 apps, find and select **Dynamics 365 HR Integration to URS**
![InstallDynApps1](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/129548753/58156d57-c31c-44ed-988c-553f64816f1c)


- Click **Next** and agree to terms of service to install the app
  ![InstallDynApps2](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/129548753/d0b4fb50-42fa-49e7-92ab-eb1fc7ad4f9c)


The solution installation is in progress, with the status '_Installing_'.
![InstallDynApps3](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/129548753/dd5a9e5e-6e8d-40da-9fb8-0e2f8c1fcd33)


When the solution completes installation, the status changes to '_Installed_'.
![InstallDynApps4](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/129548753/29c85e3d-42e3-462a-b248-cfee46cc8968)


### Install Dual Write Packages:

The Dual-write Human Resources package contains the solutions and maps that are required to sync Human Resources data. Please read [Dual-write Human Resources](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/separated-solutions#dual-write-human-resources), for more information.

### Enable DW Maps:

Dual-write is an out-of-box infrastructure that provides near-real-time interaction between customer engagement apps and finance and operations apps. For detailed instructions, please see [Enable dual-write for existing finance and operations apps](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/enable-dual-write).

Integration Process

Installing and applying the HR to URS Integration enables organizations to integrate the catalog of skills, certificates, and related information in Human Resources to the characteristics table on Dataverse; this also includes mapping for Rating models and rating levels.

In addition to providing Dual-write maps, this solution also includes virtual entities. Because this solution takes dependency on virtual entities for skills and certificates, those are automatically generated when the Dual-write package completes installing.

This also means that relevant business events are registered in Human Resources and when there are changes to those entities, Dataverse is able to consume those changes.

## Data Configuration

### Create Skills in Human Resources

You can track your worker's skills in Dynamics 365 Human Resources. You can also specify the skills that are required for a specific job.Please read more on how to [create skills](https://learn.microsoft.com/en-us/dynamics365/human-resources/hr-develop-skills) in Human Resources.

### Create Certificates in Human Resources

You can track worker's Certificates in Dynamics 365 Human Resources by creating a library of certificate types and certificates. You can then add those certificates on a worker record to indicate what certificates are accredited to the worker. You can also specify the certificates that are required for a specific job.

### Define skills and proficiencies in Project Operations

Skills are resource characteristics that are shared between Dynamics 365 Project Operations and if present, Dynamics 365 Field Service. Please read more about [defining skills and proficiencies](https://learn.microsoft.com/en-us/dynamics365/project-operations/resource-management/define-skills-proficiencies) in Project Operations.

### Turn off the Integration:

When the integration is turned off, the field on bookable resource will be removed, the data associated with field also gets removed. If there were any characteristics added through the integration on the worker, those will remain on the bookable resource after the integration is turned off.

