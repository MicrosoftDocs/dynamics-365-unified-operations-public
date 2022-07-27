---

# required metadata

title: Dynamics 365 Human Resources infrastructure merge FAQ
description: This article answers frequently asked questions about the infrastructure merge for Microsoft Dynamics 365 Human Resources and finance and operations apps.
author: twheeloc
ms.date: 08/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---

# Dynamics 365 Human Resources infrastructure merge FAQ

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This page is currently being updated with new content. 

## What is Dynamics 365 Human Resources?

Microsoft Dynamics 365 Human Resources provides tools that help HR teams increase organizational agility, transform the employee experience, and optimize HR programs to create a workplace where people and the business can thrive. To learn more about Dynamics 365 Human Resources, see [Dynamics 365 Human Resources](https://dynamics.microsoft.com/human-resources/overview/).

- **Transform employee experiences.** Retain top performers by empowering managers and employees through connected self-service experiences that drive engagement and growth.
- **Optimize HR programs.** Decrease operational costs, and create people-centric leave and absence, time, benefit, and compensation management programs.
- **Increase organizational agility.** Enable HR to operate with the dexterity that the business requires by using Dataverse and Microsoft Power Platform to centralize people data and easily extend Dynamics 365 Human Resources.
- **Discover workforce insights.** Make data-driven decisions through the ability to analyze and visualize people data on rich dashboards that are available on any device.

## Value and benefits of the infrastructure merge

### What is the Dynamics 365 Human Resources infrastructure merge?

There are currently two separate sets of HR capabilities on two different infrastructures in Dynamics 365:

- **Dynamics 365 Human Resources** – A stand-alone app that runs on an independent infrastructure. When this app was launched, the infrastructure was separated from other Dynamics 365 operations apps. Our customers use this app to increase organizational agility, optimize HR programs, transform employee experiences, and gain workforce insights.
- **HR module** – A legacy set of capabilities that was previously part of the Unified Operations licensing stock keeping unit (SKU). The HR module runs on the finance and operations infrastructure, which is the same across all operations apps. These apps include Dynamics 365 Finance, Dynamics 365 Project Operations, and Dynamics 365 Supply Chain Management. Customers received the HR capabilities as part of Dynamics 365 Finance or Dynamics 365 Supply Chain Management.

Over the last three years, Microsoft has added no new capabilities or enhancements to the HR module. Instead, our roadmap investments have focused on the Dynamics 365 Human Resources app.

By bringing these two sets of capabilities onto the same infrastructure, we will help customers gain the following benefits:

- Enhancements that have been added to Dynamics 365 Human Resources over the last three years, including enhanced leave and absence, benefit management, and reporting.
- Improved extensibility through Microsoft Power Platform and the ability to extend business logic to personalize pages.
- Improved deployment, updates, and maintenance that are consistent in terms of application lifecycle management (ALM), lifecycle services, geographic availability, and more.
- More technological innovation as our engineering team uses shared services, tooling, and reduced platform costs.

This transition will affect customers who are currently using either Dynamics 365 Human Resources or the legacy HR module.

## Glossary of terms used in this FAQ

- **Dynamics 365 Human Resources** – Our current and future product that offers HR capabilities to the market.
- **HR module** – A set of legacy capabilities that was previously licensed with the Unified Operations offering. The capabilities are enabled when a customer owns Dynamics 365 Finance or Dynamics 365 Supply Chain Management.
- **Finance and operations infrastructure** – The development architecture that is used by the operations portfolio, including Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Project Operations. This infrastructure is the one that will be used going forward. In this FAQ, the term *merged infrastructure* refers to the finance and operations environment.
- **Human resources infrastructure** – The development architecture that was historically used for the Dynamics 365 Human Resources app. The infrastructure merge project brings Dynamics 365 Human Resources onto the finance and operations infrastructure. The stand-alone infrastructure will be discontinued.

## General questions about the infrastructure merge

### Will customers lose any features or capabilities?

Our objective is to minimize the impact that this transition has on customers. We won't be removing any features or capabilities. There will be functional parity between Dynamics 365 Human Resources and the HR module. In cases where a feature exists in both infrastructures, the Dynamics 365 Human Resources experience will be used.

### Will the user experience change?

The user experience will be consistent with the standard Dynamics 365 platform experience. Although the general experience for the dashboard and menus will remain similar, it will be aligned with the standard Dynamics 365 Finance app experience. Navigation will include both modules and workspaces, allow for favorites, and more. The Dynamics 365 Human Resources workspaces, such as **Personnel management** and **People**, will merge onto the finance and operations infrastructure. In the future, new capabilities will be delivered through Feature management, which lets customers view new features and decide which ones they want to use. For more information, see [Feature management overview](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and [User interface documentation](../fin-ops-core/fin-ops/get-started/user-interface-elements.md?toc=/dynamics365/human-resources/toc.json).

### When will the Dynamics 365 Human Resources infrastructure merge be completed?

The infrastructure merge will roll out in phases to give customers time to plan and complete the necessary steps. We began to roll out capabilities in the Dynamics 2021 release wave 2. We plan to complete all product development efforts for this project by the end of 2022 release wave 2. Note that timelines are subject to change. For the most up-to-date information, see [release plans](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

### What training and resources will be available to help with the infrastructure merge?

We will provide documentation that describes each step of the infrastructure merge process in detail. We will provide additional training resources, such as videos and workshops, as necessary to help customers and partners with a smooth transition.

### Will there be changes in development capabilities after the infrastructure merge is completed?

To learn more about development capabilities, see [Develop and customize home page](../fin-ops-core/dev-itpro/dev-tools/developer-home-page.md).

## Feature availability questions

### Will the LinkedIn Talent Hub integration work on the finance and operations infrastructure?

No, the LinkedIn Talent Hub integration won't be a part of the merged infrastructure. Public application programming interfaces (APIs) are available to build integrations with recruiting and applicant tracking solutions. Customers who are planning to use LinkedIn Talent Hub should work with their Microsoft partner to integrate by using the provided APIs. For more information about Applicant Tracking System (ATS) integration APIs, see [Applicant Tracking System integration API introduction](./hr-admin-integration-ats-api-introduction.md).

### Will the capabilities that are currently available only in Dynamics 365 Human Resources (for example, leave management and benefits management) be available after the merge is completed?

Yes. All Dynamics 365 Human Resources application capabilities are being brought to the finance and operations infrastructure. The features will be made available in a phased approach. For up-to-date information about feature availability for the merged infrastructure, regularly review the [release plans](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

### Will Ceridian integrations with Dynamics 365 Human Resources be available after the infrastructure merge is completed?

Ceridian is in the process of creating a V2 integration with Dynamics 365 Human Resources that takes advantage of the Payroll APIs. The file-based integration that currently exists in Dynamics 365 Human Resources won't be migrated to the finance and operations infrastructure. For more information, see [Payroll API introduction](./hr-admin-integration-payroll-api-introduction.md).

### Will applicant tracking or onboarding/offboarding of employee's functionality be included?

In previous releases, we created the ATS Integration API to enable partners and customers to create ATS integrations with Human Resources. Additional ATS-related functionality became available in 2022 wave 1. We will continue to enhance these APIs in future releases.

The HR functionality that currently exists in the finance and operations infrastructure includes some recruitment management functionality that doesn't exist in Dynamics 365 Human Resources. When the infrastructure merge is completed, this functionality will be available to all Human Resources customers. This functionality provides lightweight ATS functionality. However, we don't plan to expand this functionality in the future. Customers who require more advanced functionality can take advantage of partner ATS integrations. For more information about ATS integration APIs, see [Applicant Tracking System integration API introduction](./hr-admin-integration-ats-api-introduction.md).

### Will the Dynamics AX 2012 upgrade tools be used to upgrade the HR module in AX 2012 to the Dynamics 365 Human Resources app?

Yes. Upgrade from Dynamics AX 2012 to Dynamics 365 Human Resources will follow the same upgrade path and tooling that are used to upgrade to the latest version of other Dynamics 365 operations apps, such as Dynamics 365 Finance or Dynamics 365 Supply Chain Management.

## Customer migration

### How should Dynamics 365 Human Resources customers plan to move to the finance and operations infrastructure?

Two categories of Dynamics 365 Human Resources customers will be affected and will have to make changes to ensure that they are on the latest finance and operations infrastructure:

- Customers who use **Dynamics 365 Human Resources** and don't have any additional Dynamics 365 operations apps.
- Customers who use both **Dynamics 365 Human Resources** and **Dynamics 365 Finance**, **Dynamics 365 Supply Chain Management**, **Dynamics 365 Commerce**, or **Dynamics 365 Project Operations**.

Regardless of the category that a customer falls into, they will have to move data into a newly created environment on the finance and operations infrastructure and validate that the merge has been successfully completed.

Going forward, the Dynamics 365 Human Resources app will have its own finance and operations environment that is separate from other operations apps. In this way, customers can take advantage of extensibility options without having to merge their current data. We will provide tooling and a sandbox environment that customers can use for testing and validation of data migration before they move to a production environment. These tools will enable a near-automated process and will be available between August and November 2022. For updates, see the [release plans](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

Customers who are using other applications on the finance and operations infrastructure will have the option to merge their HR data with an existing environment.

### When will customers be moved to the finance and operations infrastructure?

The transition for each company will depend on that company's current configuration and readiness to move to the finance and operations infrastructure. We recommend that customers work with their Microsoft partner to determine the best path forward.

- Organizations that use the **HR module in Dynamics 365 Finance** will be able to enable new capabilities from Dynamics 365 Human Resources as part of the regular One Version update process. New features are planned to become generally available beginning in January 2022. (Dates are subject to change. For the latest information, see the [release plans](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).) Review licensing changes and timelines, because all customers will have to move to Dynamics 365 Human Resources to use these capabilities in the future.
- Organizations that use **Dynamics 365 Human Resources** will have access to tooling that they can use to complete the infrastructure merge. For up-to-date information about when some of the tools will be available, regularly review the [release plans](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance). We will work with customers on the transition, to help prevent any interruption in service. Customers will have 12 to 18 months to make the transition, starting from the time when the migration tooling becomes available.
- Organizations that use both **Dynamics 365 Human Resources** and the **HR module** can move their stand-alone Human Resources infrastructure to the finance and operations infrastructure, and can optionally use the merge tooling to bring the environments into a single environment. There is no requirement or timeframe for merging the two environments together.

### Will customers still need custom integrations between Dynamics 365 Human Resources and the HR module?

Customers who have both Dynamics 365 Human Resources and other finance and operations infrastructure environments that are currently integrated will have to continue to integrate the two environments after the merge.

Customers who choose to keep their Dynamics 365 Human Resources environment separate from their existing finance and operations app environment will have to continue to integrate the environments to make the data available in both environments.

Customers can continue to use the Data Integrator to copy data between the two environments. If a customer decides to merge data into a single environment after the migration, they will no longer have to integrate the data, because all data will be in a single database.

### Will customer ISV solutions be migrated automatically?

The migration experience for each independent software vendor (ISV) solution will vary, based on the integration method of the solution. We will work closely with ISVs to provide a smooth transition to the finance and operations infrastructure. Many ISV solutions are built on Dataverse by using Power Platform capabilities. These solutions are dependent on the Dataverse integration between the Dynamics 365 Human Resources environment and the Dataverse environment. The Dataverse integration is being deprecated as part of the infrastructure merge. In the finance and operations infrastructure, new dual-write maps are planned to replace the functionality of the Dataverse integration. For more information about the dual-write maps and their availability, see the [release plans](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

### How will the Data Integrator that moves data between Dynamics 365 Human Resources and other Dynamics 365 apps be affected?

After customers move to the finance and operations infrastructure, they will have to continue to integrate data between the two environments. Customers can continue to use the Data Integrator to perform these data migration tasks.

Customers who plan to keep their Dynamics 365 Human Resources environment separate from their existing finance and operations apps environment will have to continue to integrate the data between the two environments.

For customers who merge the two environments into a single environment, the integration between the two environments will no longer be necessary.

### How will data be moved between Dynamics 365 Human Resources on the finance and operations infrastructure and Dataverse after the migration?

The current Dataverse integration between Dynamics 365 Human Resources and Dataverse is being deprecated as part of the finance and operations infrastructure. There are plans to introduce new dual-write maps to map the finance and operations entities to the Dataverse tables. Customers will have to decide which dual-write maps are required for their implementation. We recommend that virtual tables be used for integrations and ISV solutions, unless there is a specific business need for the data to be duplicated into Dataverse to run business logic.

### How does the migration affect Dataverse extensions for Dynamics 365 Human Resources?

Customers will be required to migrate to a sandbox environment before they migrate their production environment. When customers migrate their sandbox environment, they will have to create a copy of their Dataverse environment to connect to the new finance and operations migrated environment. We recommend that customers copy both the data and the solutions for the environment, so that they are the same as the customer's current production environment.

When a customer is ready to migrate their production Dynamics 365 Human Resources environment, Microsoft will automatically migrate the database and Azure Blob Storage, and point the new environment on the finance and operations infrastructure to the same production Dataverse environment. For the data to continue to be copied into Dataverse, customers will have to enable any dual-write maps that are required for their integrations, extensions, and ISV solutions that are built on Dataverse.

### Will Microsoft Power Platform components that are built for Dynamics 365 Human Resources automatically work after the infrastructure migration is completed?

Power Apps, Power Automate, and other Microsoft Power Platform customizations are like Dataverse extensions. During the migration of customer production environments, there is no impact on Dataverse environments, including any extensions. Apps that are created by using Power Apps, flows that are created by using Power Automate, and other Microsoft Power Platform customizations should continue to work without any additional configuration.

### What will happen to Dataverse virtual table entities for Dynamics 365 Human Resources during the migration?

When customers migrate their Dynamics 365 Human Resources environment to the finance and operations infrastructure, the environment will remain connected to the Dataverse environment that is currently connected to Dynamics 365 Human Resources. The Dataverse virtual tables that have been generated in the environment will continue to work without any additional configuration.

The virtual tables might have to be regenerated in the Dataverse environment that is connected to the customer's existing finance and operations environment.

### How will an integration that uses the ATS API, Payroll API, Dataverse virtual tables for Dynamics 365 Human Resources, or other entities in the Dataverse Web API work after the infrastructure merge is completed?

When customers migrate their Dynamics 365 Human Resources environment to the finance and operations infrastructure, the environment will remain connected to the Dataverse environment that is currently connected to Dynamics 365 Human Resources. Any integrations that were developed against the Dataverse Web API will continue to work after the migration is completed.

### Our organization has configured custom security in Dynamics 365 Human Resources. Will our custom security still be applied after the infrastructure migration is completed?

Yes, custom security configurations will be included in the data migration.

### Will workflows in Dynamics 365 Human Resources be migrated automatically?

Yes, workflow configurations, workflow history, and current in-process workflows will be migrated.

### Will saved views in Dynamics 365 Human Resources be migrated automatically?

Yes, saved views will be migrated to the merged infrastructure.

### Will features that are enabled in Dynamics 365 Human Resources automatically be available after the infrastructure merge?

For customers who use the HR module, features that are available only in Dynamics 365 Human Resources will be managed through Feature management. These features won't be enabled by default. If any features must be enabled by default, they will be documented.

For customers who use Dynamics 365 Human Resources, features will be available in the infrastructure. If any features are unavailable, they will be documented. Any feature management key that is enabled in the current Dynamics 365 Human Resources environment will be enabled in the merged infrastructure. For more information, see [Feature management overview](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### What happens to BYOD databases during the migration?

Import and export configurations for bring your own database (BYOD) will be migrated to the finance and operations infrastructure.

### Is there an impact on the Azure region when the customer environment is migrated?

The Dynamics 365 Human Resources environment will stay within the same Azure region for the migration. If there is a requirement to move an environment to a different Azure region, customers will have to follow the standard steps to migrate to a new region after the migration is completed.

### What happens to data lakes during the migration?

Any export that is currently configured for Azure Data Lake Storage in finance and operations apps will maintain the same configuration after the migration. Note that dual-write maps will have to be enabled to continue to write data from the Dynamics 365 Human Resources environment to Dataverse.

If a customer wants to export Human Resources data to the data lake, they can optionally enable this feature after the migration to the finance and operations infrastructure is completed. For more information, see [Data lakes](/azure/architecture/data-guide/scenarios/data-lake/). Customers can link multiple finance and operations apps environments to the same data lake. However, each environment will point to a different folder and container. Customers who are planning to merge environments together later should carefully plan their approach.

### What migration will be required if the customer is currently using the HR module?

Customers who use the HR module will have the new feature functionality from Dynamics 365 Human Resources applied to their environment through the standard [One Version](../fin-ops-core/fin-ops/get-started/public-preview-releases.md) update process. Customers can expect to see the new functionality in their environment as it becomes available in each update. Customers can use Feature management to enable these features. Customers should plan to validate these new features by using the processes that they already have in place for validating other updates to their environment.

### What will happen to custom integrations with external systems?

Customers will have to migrate their integrations to the finance and operations environment. Because the endpoint of this environment is different, customers might have to update or change the integrations so that they point to the new environment. This process will be primarily manual, and the changes that are required will depend on the architecture of the integration. Customers should work with their Microsoft partner to determine the best approach for moving integrations.

### What will happen to Microsoft Power Platform (Dataverse) extensions if a customer merges a Dynamics 365 Human Resources environment with an existing finance and operations environment?

If a customer decides to merge a Dynamics 365 Human Resources environment and an existing finance and operations environment into a single Dataverse instance after the migration, their Dataverse environments will have to be combined as part of the merge process. This task will require that any apps that are created by using Power Apps, and other customizations, be redeployed in the new environment.

### What will happen to documents during the migration?

When customers migrate their Dynamics 365 Human Resources environment to the finance and operations infrastructure, the documents will remain in the existing document storage and will automatically be mapped to the new environment in the finance and operations infrastructure.

In a future release, we will provide new data entities that customers who choose to merge their Dynamics 365 Human Resources environment into an existing finance and operations environment can use to export documents and move them into the existing environment.

### What happens to the batch jobs that are configured in Dynamics 365 Human Resources after the migration?

Batch jobs will have to be reconfigured in the finance and operations environment. Customers will have to evaluate each batch job and compare it to the current list of batch jobs in the finance and operations environment. Customers should also analyze the overall batch schedule when they merge the two sets of batch jobs together, to determine whether changes should be made to the batch schedule, priorities, or batch groups.

### How will the migration affect the LCS project for Dynamics 365 Human Resources?

Customers will be required to create a new Microsoft Dynamics Lifecycle Service (LCS) project, and select the finance and operations product and the **Implementation** project type. Additionally, a new field for the sub-project type is available when an LCS project is created. To migrate an existing Human Resources LCS project into the finance and operations infrastructure, customers will have to select the option for Dynamics 365 Human Resources migration.

The features of finance and operations LCS projects differ from the features of Human Resources LCS projects. New customers will have to complete project onboarding, complete the methodology, fill in a subscription estimator, and complete the go-live readiness process to go live on the finance and operations infrastructure. For more information about finance and operations LCS projects, see [Projects (Lifecycle Services, LCS)](/dynamicsax-2012/appuser-itpro/projects-lifecycle-services-lcs/).

### How will the Business process modeler be migrated?

Customers will be required to export their Business process modeler library from the Human Resources LCS project and import it into the finance and operations LCS project. Additionally, customers will have to update the Help settings in the application so that they point to the new LCS project.

### How will the migration affect the service update process?

After the migration, customers will have much more flexibility in ALM and service updates. Service updates will no longer be automatically applied to Dynamics 365 Human Resources environments. Instead, the service will follow One Version service update processes and functionality, and will enable configuration options for updates through LCS. For more information, see [One Version service updates overview](../fin-ops-core/dev-itpro/lifecycle-services/oneversion-overview.md).

### Will customers be eligible for FastTrack assistance with the infrastructure merge?

We are still defining what tools and resources will be available from FastTrack to help with the merge.
