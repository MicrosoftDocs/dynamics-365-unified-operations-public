---
# required metadata

title: Human Resources customer migration FAQ
description: This article answers frequently asked questions about the migration of Microsoft Dynamics 365 Human Resources to the finance and operations merged infrastructure. 
author: twheeloc
ms.date: 08/23/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---
# Human Resources customer migration

## How should Dynamics 365 Human Resources customers plan to move to the finance and operations infrastructure?

Two categories of Microsoft Dynamics 365 Human Resources customers are affected and have to make changes to ensure that they are on the latest finance and operations infrastructure:

- Customers who use Dynamics 365 Human Resources and don't have any other operations apps from Dynamics 365
- Customers who use both Dynamics 365 Human Resources and Dynamics 365 Finance, Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, or Dynamics 365 Project Operations

Regardless of the category that they belong to, customers have to move data into a newly created environment on the finance and operations infrastructure and validate that the merge has been successfully completed.

Going forward, the Dynamics 365 Human Resources app has its own finance and operations environment that is separate from other operations apps. In this way, customers are able to take advantage of extensibility options without having to merge their current data. Microsoft provides tooling and a sandbox environment that customers can use to test and validate the data migration before they move to a production environment. The tooling enables a near-automated process and will be available between August and November 2022.

Customers who are using other apps on the finance and operations infrastructure will have the option to merge their Human Resources data with an existing environment. 

## When will customers be moved to the finance and operations infrastructure?

The transition for each company depends on that company's current configuration and readiness to move to the finance and operations infrastructure. We recommend that customers work with their Microsoft partner to determine the best path forward.

- Organizations that use the **Human Resources** module in Dynamics 365 Finance will be able to enable new capabilities from Dynamics 365 Human Resources as part of the regular One Version update process. New features are planned to become generally available starting in January 2022.
- Organizations that use Dynamics 365 Human Resources have access to tooling that they can use to complete the infrastructure merge. Microsoft will work with customers on the transition, to help prevent any interruption in service. Customers have 12 months to make the transition, starting from the time when the migration tooling becomes available.
- Organizations that use both Dynamics 365 Human Resources and the **Human Resources** module can move their stand-alone Human Resources infrastructure onto the finance and operations infrastructure. Another option is to use the merge tooling to bring the environments into a single environment. There is no requirement or timeframe for merging the two environments.

For up-to-date information, regularly check the [Release plans](/dynamics365/release-plans/).

## Will customers still need custom integrations between Dynamics 365 Human Resources and the Human Resources module?

- Customers who have both Dynamics 365 Human Resources and other finance and operations infrastructure environments that are currently integrated will have to continue to integrate the two environments after the merge.
- Customers who choose to keep their Dynamics 365 Human Resources environment separate from their existing finance and operations app environment will have to continue to integrate the environments to make the data available in both environments.
- Customers can continue to use the Data Integrator to copy data between the two environments. Customers who merge data into a single environment after the migration will no longer have to integrate the data, because all data will be in a single database.

## Will customer ISV solutions automatically be migrated?

The migration experience for each independent software vendor (ISV) solution will vary, depending on the integration method of the solution. Microsoft will work closely with ISVs to help provide a smooth transition to the finance and operations infrastructure. Many ISV solutions are built on Dataverse by using capabilities of Microsoft Power Platform. These solutions depend on the Dataverse integration between the Dynamics 365 Human Resources environment and the Dataverse environment. The Dataverse integration is being deprecated as part of the infrastructure merge. In the finance and operations infrastructure, new dual-write maps are planned to replace the functionality of the Dataverse integration.

## How will the Data Integrator that moves data between Dynamics 365 Human Resources and other Dynamics 365 apps be affected?

After customers move to the finance and operations infrastructure, they will have to continue to integrate data between the two environments. Customers can continue to use the Data Integrator to perform these data migration tasks. Customers who plan to keep their Dynamics 365 Human Resources environment separate from their existing finance and operations apps environment will have to continue to integrate the data between the two environments. For customers who merge the two environments into a single environment, integration between the two environments will no longer be required.

## How will data be moved between Dynamics 365 Human Resources on the finance and operations infrastructure and Dataverse after the migration?

The current Dataverse integration between Dynamics 365 Human Resources and Dataverse is being deprecated as part of the finance and operations infrastructure. There are plans to introduce dual-write maps to map the finance and operations entities to the Dataverse tables. Customers will have to decide which dual-write maps are required for their implementation. We recommend that virtual tables be used for integrations and ISV solutions, unless there is a specific business need for the data to be duplicated in Dataverse to run business logic.

## How does the migration affect Dataverse extensions for Dynamics 365 Human Resources?

Customers will be required to migrate to a sandbox environment before they migrate their production environment. When customers migrate their sandbox environment, they will have to create a copy of their Dataverse environment to connect to the new finance and operations migrated environment. We recommend that a customer copy both the data and the solutions for the environment, so that they match the customer's current production environment.

When customers are ready to migrate their production Dynamics 365 Human Resources environment, Microsoft will automatically migrate the database and Azure Blob storage. The migrated database and storage will point the new environment on the finance and operations infrastructure to the same production Dataverse environment. Before the data can continue to be copied to Dataverse, customers will have to enable any dual-write maps that are required for their integrations, extensions, and ISV solutions that are built on Dataverse.

## Will Microsoft Power Platform components that were built for Dynamics 365 Human Resources automatically work after the infrastructure migration is completed?

Apps that are created in Power Apps, flows that are created in Power Automate, and other Microsoft Power Platform customizations are like Dataverse extensions. During the migration of customer production environments, there is no impact on Dataverse environments, including any extensions. Apps, flows, and other Power Microsoft Platform customizations should continue to work without requiring additional configuration.

## What will happen to Dataverse virtual table entities for Dynamics 365 Human Resources during the migration?

When customers migrate their Dynamics 365 Human Resources environment to the finance and operations infrastructure, the environment will remain connected to the Dataverse environment that is currently connected to Dynamics 365 Human Resources. The Dataverse virtual tables that have been generated in the environment will continue to work without requiring any additional configuration. The virtual tables might have to be regenerated in the Dataverse environment that is connected to a customer's existing finance and operations environment.

## How will an integration that uses the Applicant Tracking System (ATS) API, Payroll API, Dataverse virtual tables for Dynamics 365 Human Resources, or other entities in the Dataverse Web API work after the infrastructure merge is completed?

When customers migrate their Dynamics 365 Human Resources environment to the finance and operations infrastructure, the environment will remain connected to the Dataverse environment that is currently connected to Dynamics 365 Human Resources. Any integrations that were developed against the Dataverse Web API will continue to work after the migration is completed.

## Our organization has configured custom security in Dynamics 365 Human Resources. Will it still be applied after the infrastructure migration is completed?

Yes, custom security configurations will be included in the data migration.

## Will workflows in Dynamics 365 Human Resources automatically be migrated?

Yes, workflow configurations, workflow history, and current in-process workflows will be migrated to the merged infrastructure.

## Will saved views in Dynamics 365 Human Resources automatically be migrated?

Yes, saved views will be migrated to the merged infrastructure.

## Will features that are enabled in Dynamics 365 Human Resources automatically be available after the infrastructure merge?

- For customers who use the **Human Resources** module, features that are available only in Dynamics 365 Human Resources will be managed through Feature management. Usually, these features won't be enabled by default. Any features that must be enabled by default will be documented.
- For customers who use Dynamics 365 Human Resources, features will be available in the infrastructure. Any features that aren't available will be documented. Every Feature management key that is enabled in the current Dynamics 365 Human Resources environment will be enabled in the merged infrastructure. For more information, see [Feature management overview](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

## What happens to BYOD databases during the migration?

Import and export configurations for bring your own database (BYOD) will be migrated to the finance and operations infrastructure.

## Is there an impact on the Azure region when the customer environment is migrated?

The Dynamics 365 Human Resources environment will stay in the same Azure region for the migration. If there is a requirement to move an environment to a different Azure region, customers will have to follow the standard steps to migrate to a new region after the migration is completed.

## What happens to Azure data lakes during the migration?

Any export that is currently configured for Azure Data Lake in finance and operations apps will maintain the same configuration after the migration.

> [!NOTE]
> Dual-write maps will have to be enabled to continue to write data from the Human Resources environment into Dataverse.

Customers who want to export Human Resources data to the data lake can enable this feature after the migration to the finance and operations infrastructure is completed. For more information, see [Data lakes - Azure Architecture Center](/azure/architecture/data-guide/scenarios/data-lake).

Customers can link multiple finance and operations environments to the same data lake. However, each environment will point to a different folder and container. Customers who plan to merge environments later should carefully plan their approach.
 
## What migration will be required if a customer is currently using the Human Resources module?

Customers who use the **Human Resources** module will have the new feature functionality from Dynamics 365 Human Resources applied to their environment through the standard One Version update process. Customers can expect to see the new functionality in their environment as it becomes available in each update. Customers can use Feature management to enable the features. Customers should plan to validate these new features by using the processes that they already have in place and use to validate other updates to their environment.

## What will happen to custom integrations to external systems?

Customers have to migrate their integrations to the finance and operations environment. Because the endpoint of this environment is different, customers might have to update or change the integrations so that they point to the new environment. This task will primarily be a manual process, and the changes that are required will depend on the architecture of the integration. Customers should work with their Microsoft partner to determine the best approach for moving integrations.

## What will happen to Microsoft Power Platform (Dataverse) extensions if customers merge a Dynamics 365 Human Resources environment with an existing finance and operations environment?

If customers decide to merge a Dynamics 365 Human Resources environment and an existing finance and operations environment into a single Dataverse instance after the migration, their Dataverse environments must be combined as part of the merge process. This task will require that any apps that are created by using Power Apps, and any other customizations, be redeployed in the new environment.

## What will happen to documents during the migration?

When customers migrate their Dynamics 365 Human Resources environment to the finance and operations infrastructure, the documents will remain in the existing document storage and will automatically be mapped to the new environment in the finance and operations infrastructure.

In a future release, new data entities will be provided. After that change is made, customers who choose to merge their Dynamics 365 Human Resources environment with an existing finance and operations environment will then be able to export documents and move them into the existing environment.

## After the migration, what happens to the batch jobs that were configured in Dynamics 365 Human Resources?

Batch jobs will have to be reconfigured in the finance and operations environment. Customers will have to evaluate each batch job and compare it to the current list of batch jobs in the finance and operations environment. Customers should also analyze the overall batch schedule when they merge the two sets of batch jobs, to determine whether changes should be made to the batch schedule, priorities, or batch groups.

## How will the migration affect the LCS project for Dynamics 365 Human Resources?

Customers are required to create a new Microsoft Dynamics Lifecycle Service (LCS) project, and they will have to select finance and operations apps as the product and **Implementation** as the project type. Additionally, a new field for the sub-project type is available when an LCS project is created. Customers have to select the option for Dynamics 365 Human Resources migration to migrate an existing Human Resources LCS project to the finance and operations infrastructure.

The features of finance and operations LCS projects differ from the features of Human Resources LCS projects.

To go live, new customers will have to complete the following tasks:

- Complete project onboarding.
- Complete the methodology.
- Fill out a subscription estimator.
- Complete the go-live readiness process.

## How will the Business process modeler be migrated?

Customers are required to export their Business process modeler library from the Human Resources LCS project and import it into the finance and operations LCS project. Additionally, customers have to update the Help settings in the application so that they point to the new LCS project.

## How will the service update process be affected by the migration?

After the migration, customers will have much more flexibility for application lifecycle management (ALM) and service updates. Service updates will no longer be automatically applied to Human Resources environments. Instead, the service will follow the One Version service update processes and functionality, and configuration options for updates through LCS will be enabled.

## Will customers be eligible for FastTrack assistance with the infrastructure merge?

Microsoft is still defining what tools and resources will be available from FastTrack to help with the merge.

## Licensing impact

For more information about how licensing is affected, see [Dynamics 365 Human Resources infrastructure merge](hr-infrastructure-merge.md#licensing).

## Who needs to migrate? 
All customers on the standalone Human Resources infrastructure must migrate.  

## How long does it take to migrate using automated tooling? 
The migration using the automated tooling may take approximately three to four hours. However, the preparation, testing and validation time required for your organization are dependent on your business processes, integrations, and complexity.  

## What is the deadline for migrating?  
All customers are required to migrate their standalone environment(s) by December 31, 2023.   

## What happens to customers that don't migrate before the deadline? 
The infrastructure for the standalone application is scheduled to be turned off by December 31, 2023. As a result, environments that aren't migrated will no longer be available.  

## What happens to the Data Import Export Framework (DMF) project during the migration?
The DMF import and export project is migrated to the finance and operations infrastructure. Note that certain data entities have been enhanced in the new infrastructure. It's recommended to confirm the necessary fields are found in the data entity in the new infrastructure. Remove unavailable fields in mapping or re-add impacted data entity in the project to mitigate the issue.


