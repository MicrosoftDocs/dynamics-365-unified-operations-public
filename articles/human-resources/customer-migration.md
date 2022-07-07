---
# required metadata

title: Dynamics 365 Human Resources migration 
description: Migrate Human Resources to the finance and operations merged infrastructure. 
author: twheeloc
ms.date: 07/06/2022
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

## How should Dynamics 365 Human Resources customers plan to move to the F&O infrastructure? 
There are two categories of Dynamics 365 Human Resources customers that will be impacted and will need to make changes to ensure they are on the latest Dynamics 365 finance and operations infrastructure:  
 - Customers who use Dynamics 365 Human Resources and don't have any other operations apps from Microsoft Dynamics 365. 
 - Customers who use both Dynamics 365 Human Resources and Dynamics 365 Finance, Supply Chain Management, Commerce, or Project Operations.  

Regardless of which category the customer falls into they will need to move data into a newly created environment on the Dynamics 365 finance and operations infrastructure and validate the merge has been completed successfully. 

Going forward, the Dynamics 365 Human Resources application will have its own Dynamics 365 finance and operations environment that is separate from other operations apps. This allows customers to take advantage of extensibility options without the need to merge their current data. We will provide tooling and a sandbox environment that can be used for testing and validation of data migration, prior to moving into to a production environment. These tools will enable a near-automated process and will be available between August and November 2022.   
 
Customers that are using other applications on the finance and operations infrastructure will have the option to merge their HR data with an existing environment. Refer to the Merging Dynamics 365 with an existing Dynamics 365 finance and operations app environment section for more detail. 
 
## When will customers be moved to the Dynamics 365 finance and operations infrastructure?  
The transition for each company will depend on their current configuration and readiness to move to the Dynamics 365 finance and operations infrastructure. We recommend that customers work with their Microsoft partner to determine the best path forward. 
 - Organizations that use the HR module in Dynamics 365 Finance will have the ability to enable new capabilities from Dynamics 365 Human Resources as part of the regular
One Version update process. New features are planned to become generally available beginning in January 2022. 
 - Organizations using Dynamics 365 Human Resources will have access to tooling to complete the infrastructure merge. We will work with customers on the transition to prevent any interruption in service. Customers will have 12-18 months to make the transition starting from the time the migration tooling becomes available. 
 - Organizations that use both Dynamics 365 Human Resources and the HR module can move their stand-alone human resources infrastructure onto the Dynamics 365 finance and operations infrastructure. Another available option is to use the merge tooling to bring the environments into a single environment. There is no requirement or timeframe for merging the two environments together.  

Check the [Release plans](/dynamics365/release-plans/) regularly for up-to-date information. 
 
 
## Will customers still need custom integrations between Dynamics 365 Human Resources and the HR module?  
 - Customers that have both Dynamics 365 Human Resources and other Dynamics 365 finance and operations infrastructure environments that are currently integrated will need to continue to integrate the two environments after the merge.
 - Customers that choose to keep their Dynamics 365 Human Resources environment separate from their existing Dynamics 365 finance and operations app environment need to continue to integrate the environments to make the data available in both environments. 
 - Customers can continue to use the Data Integrator to copy data between the two environments. If the customer merges data into a single environment after the
migration, they will no longer need to integrate the data as all data will be in a single database.  

## Will customer ISV solutions be migrated automatically? 
The migration experience for each independent software vendor (ISV) solution will vary based on the integration method of the solution. We will work closely with ISVs
to provide a smooth transition to the finance and operations infrastructure. Many ISV solutions are built on Dataverse using the Power Platform capabilities. These solutions are dependent on the Dataverse integration between the Dynamics 365 Human Resources environment and the Dataverse environment. The Dataverse integration is being deprecated as part of the infrastructure merge. In the finance and operations infrastructure, new Dual Write maps are planned to replace the functionality of the Dataverse integration.  

## How will the Data integrator that moves data between Dynamics 365 Human Resources and other Dynamics 365 apps be affected? 
After moving to the finance and operations infrastructure, customers will need to continue to integrate data between the two environments. Customers can continue to use the Data Integrator to perform these data migration tasks. Customers who plan to keep their Dynamics 365 Human Resources environment separate from existing finance and operations apps environment will need to continue to integrate the data between the two environments. Customers who merge the two environments into a single environment, integration between the two environments will no longer be necessary. 

## How will data be moved between Dynamics 365 Human Resources on the F&O infrastructure and the Dataverse after the migration? 
The current Dataverse Integration between Dynamics 365 Human Resources and the Dataverse is being deprecated as part of the finance and operations infrastructure. There are plans to introduce Dual Write maps to map the finance and operations entities to the Dataverse tables. Customers will need to decide which Dual Write maps are needed for their implementation. We recommend using Virtual Tables for integrations and ISV solutions unless there is a specific business need for the data to be duplicated into the Dataverse to execute business logic.  

## How does the migration impact Dataverse extensions for Dynamics 365 Human Resources? 
Customers will be required to migrate to a Sandbox environment prior to migrating their production environment. When customers migrate their sandbox environment, they
will need to create a copy of their Dataverse environment to connect to the new finance and operations migrated environment. We recommend customers copy both the data and the solutions for the environment, so they are the same as the customer’s current production environment. 
When a customer is ready to migrate their production Dynamics 365 Human Resources environment, Microsoft will migrate the database and Azure Blob storage automatically. The migrated database and storage will point the new environment on the finance and operations infrastructure to the same production Dataverse environment. Customers will need to enable any Dual Write maps that are required for their integrations, extensions, and ISV solutions that are built on the Dataverse for the data to continue to be copied into the Dataverse. 

## Will Power Platform components built for Dynamics 365 Human Resources work automatically once the infrastructure migration is completed? 
Power Apps, Power Automate, and other Power Platform customizations are like Dataverse extensions. During the migration of customer production environments, there's 
no impact to Dataverse environments including any extensions. Power Apps, Power Automate flows, and other Power Platform customizations should continue to work without
additional configuration.  

## What will happen to Dataverse virtual tables entities for Dynamics 365 Human Resources during the migration? 
When customers migrate their Dynamics 365 Human Resources environment to the finance and operations infrastructure, the environment will remain connected to the Dataverse environment that is currently connected to Dynamics 365 Human Resources. The Dataverse virtual tables that have been generated in the environment will continue to work without any additional configuration. The virtual tables may need to be regenerated in the Dataverse environment that is connected to the customer’s existing finance and operations environment. 

## How will an integration using the Applicant Tracking System (ATS) API, Payroll API, Dataverse virtual tables for Dynamics 365 Human Resources, or other entities in the Dataverse Web API work after the infrastructure merge is completed? 
When customers migrate their Dynamics 365 Human Resources environment to the finance and operations infrastructure, the environment will remain connected to the Dataverse environment currently connected to Dynamics 365 Human Resources. Any integrations developed against the Dataverse Web API will continue to work once the migration is completed. Our organization has configured custom security in Dynamics 365 Human Resources. 

## Will our custom security still be applied once the infrastructure migration is completed? 
Yes, custom security configurations will be included in the data migration. 

## Will workflows in Dynamics 365 Human Resources be migrated automatically?  
Yes, workflow configurations, workflow history, and current in-process workflows will be migrated. 

## Will saved views in Dynamics 365 Human Resources be migrated automatically? 
Yes, saved views will be migrated to the merged infrastructure. 

## Will features enabled in Dynamics 365 Human Resources be automatically available after the infrastructure merge? 
 - For customers using the HR module, features that are only in Dynamics 365 Human Resources will be managed through Feature management. These features will not be enabled by default. There may be some cases where features do need to be enabled by default, in which case, they will be documented. 
 - For customers using Dynamics 365 Human Resources, features will be in the infrastructure. In the event there are features that are not available, documentation will be provided. Any feature management key that is enabled in the current Dynamics 365 Human Resources environment will be enabled in the merged infrastructure. 
For more information, see [Feature management overview](/fin-ops/get-started/feature-management-overview.md).  

## What happens to BYOD databases during the migration? 
Import and export configurations for bring your own database (BYOD) will be migrated to the finance and operations infrastructure. 

## Is there an impact on the Azure region when the customer environment is migrated? 
The Dynamics 365 Human Resources environment will stay within the same Azure region for the migration. If there is a requirement to move an environment to a different
Azure region, customers will need to follow the standard steps to migrate to a new region after the migration is complete.  

## What happens to Azure Data Lakes during the migration? 
Any export currently configured for Azure Data Lake in finance and operations apps will maintain the same configuration following the migration. 

> [!NOTE]
> Dual Write maps will need to be enabled to continue writing data from the Human Resources environment into the Dataverse.  

If a customer wants to export Human Resources data to the Data Lake, they can enable this feature after the migration to the Dynamics 365 finance and operations infrastructure is complete. For more information, see [Data lakes - Azure Architecture Center](../../azure/architecture/data-guide/scenarios/data-lake). 

Customers can link multiple finance and operations apps environments to the same Data Lake, however, each environment will point to a different folder and container. Customers planning to merge environments together later should carefully plan their approach. 
 
## What migration will be needed if the customer is currently using the HR module? 
Customers using the HR module will have the new feature functionality from Dynamics 365 Human Resources applied to their environment through the standard One Version
update process. Customers can expect to see the new functionality in their environment as it becomes available in each update. Customers can use feature management to
enable these features. Customers should plan to do validations on these new features following the processes they already have in place for validating other updates to
their environment.

## What will happen to custom integrations to external systems? 
Customers will need to migrate their integrations to the finance and operations environment. The endpoint of this environment is different, customers may need to make updates or changes to integrations to point to the new environment. This will be a primarily manual process and the changes required are dependent on the architecture of the integration. Customers should work with their Microsoft partner to determine the best approach for moving integrations.  

## What will happen to Power Platform (Dataverse) extensions if a customer merges Dynamics 365 Human Resources environment with an existing F&O environment? 
If a customer decides to merge a Dynamics 365 Human Resources environment and an existing finance and operations environment into a single Dataverse after the migration, their Dataverse environments need to be combined as part of the merge process. This will require any Power Apps and other customizations to be redeployed in the new environment. 

## What will happen to documents during the migration? 
When customers migrate their Dynamics 365 Human Resources environment to the finance and operations infrastructure, the documents will remain in the existing document storage and will be mapped automatically to the new environment in the finance and operations infrastructure. 
In a future release, new data entities will be provided. This will allow customers to who choose to merge their Dynamics 365 Human Resources environment into an existing
finance and operations environment to export documents and move them into the existing environment. 

## What happens to the batch jobs configured in Dynamics 365 Human Resources after the migration? 
Batch jobs will need to be reconfigured in the finance and operations environment. Customers will need to evaluate each batch job and compare it to the current list of batch jobs in the finance and operations environment. Customers should also analyze the overall batch schedule when merging the two sets of batch jobs together to determine if changes should be made to the batch schedule, priorities, or batch groups.

## How will the migration effect Lifecycle Service project for Dynamics 365 Human Resources? 
Customers will be required to create a new Lifecycle Service (LCS) project and select the finance and operations product and Implementation project type. Additionally, a new sub project type field has been added when creating an LCS project. Customers will need to select the option for Dynamics 365 Human Resources migration to migrate an existing Human Resources LCS project into the finance and operations infrastructure.  
The features of Dynamics 365 finance and operations LCS projects are different than Human Resources LCS projects. 

New customers will need to complete the following to go live:
 - project onboarding 
 - the methodology 
 - fill out a subscription estimator 
 - the go live readiness process 
  
## How will the Business Process Modeler be migrated? 
Customers will be required to export their business process modeler library from the Human Resources LCS project and import into the Dynamics 365 finance and operations LCS project. Additionally, customers will need to update the Help settings in the application to point to the new LCS project. 

## How will the service update process be affected by the migration? 
Customers will have much more flexibility in application lifecycle management (ALM) and service updates following the migration. Rather than having service updates 
applied automatically to Human Resources environments, the service will follow One Version service update processes and functionality, enabling configuration options 
for updates through Lifecycle Services (LCS). 

## Will customers be eligible for FastTrack assistance with the infrastructure merge? 
We are still defining what tools and resources will be available from FastTrack to assist with the merge.  

## Licensing Impact 
For more information regarding licensing impated, go to [Dynamics 365 Human Resources infrastructure merge FAQ](hr-infrastructure-merge-faq.md#licensing-impact).  
 




