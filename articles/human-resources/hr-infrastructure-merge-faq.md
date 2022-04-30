---

# required metadata

title: Dynamics 365 Human Resources infrastructure merge FAQ
description: This topic answers frequently asked questions about the infrastructure merge for Microsoft Dynamics 365 Human Resources and Finance and Operations apps.
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
ms.search.scope: Human Resources
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



This topic answers frequently asked questions about the infrastructure merge for Microsoft Dynamics 365 Human Resources and Finance and Operations apps.

## What is the Dynamics 365 Human Resources infrastructure merge?

Dynamics 365 Human Resources is a stand-alone application that uses a different infrastructure than other Finance and Operations apps, such as Dynamics 365 Finance, Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, and Dynamics 365 Project Operations. The infrastructure merge will bring Dynamics 365 Human Resources into the same infrastructure as other Finance and Operations apps.

## Value and benefits of the infrastructure merge

### My organization uses Dynamics 365 Human Resources to manage its HR operations. What benefits will we see from these changes?

- These changes remove the confusion caused by multiple sets of human resources (HR) capabilities in Dynamics 365.
- They provide both Microsoft Power Platform extensibility, and a way to extend business logic and feature options.
- They bring consistency between Dynamics 365 Human Resources and other Finance and Operations apps in terms of Application Lifecycle Management (ALM), Microsoft Dynamics Lifecycle Services (LCS), geographic availability, extensibility, and more.
- They let you take advantage of shared services and tooling, and help reduce costs.

### My organization uses the Human Resources module in Dynamics 365 Finance, Supply Chain Management, Commerce, or Project Operations. What benefits will we see from these changes?

The capabilities and investments that have been made in Dynamics 365 Human Resources will now be available to customers who are using the HR module in Dynamics 365 Finance. Some of these capabilities include leave and absence management, benefits management, and task management.

### Will I lose any features or capabilities that I currently use?

There will be functional parity between Dynamics 365 Human Resources and the HR module in Finance and Operations apps. Dynamics 365 Human Resources will take precedence for like features. For more information, see [Feature management overview](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Will the experience change for my users?

The new HR capabilities will be managed through Feature management. Customers will decide whether they want to uptake them. In some cases, capabilities might be modified. In those cases, documentation will be provided.

### How does this change affect me if I am an existing customer, and I use both the HR module on the Finance and Operations infrastructure and Dynamics 365 Human Resources through custom integrations?

Custom integrations between Dynamics 365 Human Resources and the HR module in Dynamics 365 Finance will no longer be required. All HR data will reside in the same database as other Finance and Operations apps.

## Migration from Dynamics 365 Human Resources to Finance and Operations apps

### My organization uses Dynamics 365 Human Resources to manage HR operations. What do we have to plan for to migrate to the new experience?

If your organization uses Dynamics 365 Human Resources but doesn't use any other Finance and Operations apps, your Human Resources environment will be migrated to the new infrastructure. Much of this migration process will be automated. Processes will be in place to migrate your database and synchronize it with the new infrastructure.

Additionally, tooling will be in place so that you can test the migration process, and validate your data and experience, before you migrate your production environment.

If your organization uses both Dynamics 365 Human Resources and other Finance and Operations apps, you should plan more time for validation to ensure that your data is correctly migrated to the new environment. The migration to the new infrastructure will merge the data from your Human Resources environment with your Finance and Operations environment. Conflicting data will require user input to determine how the conflict should be resolved. Users and administrators will have to manage the data mappings where there are conflicts and test the migration in sandbox environments before the migration of production environments.

### My organization uses the Human Resources module in Dynamics 365 Finance, Supply Chain Management, Commerce, or Project Operations. What do we have to plan for to migrate to the new experience?

For organizations that are using the HR module in Finance and Operations apps, the new feature functionality from Dynamics 365 Human Resources will be applied to your environment through the standard One Version update process. You can expect to see the new functionality in your environment as it becomes available in each update. You can use Feature management to turn on new features, however you should plan to validate these features. Follow the processes that you have in place for validating other updates to your environment. For more information about how updates are applied to Finance and Operations apps, see [One Version overview](../fin-ops-core/dev-itpro/lifecycle-services/oneversion-overview.md).

### When will my organization be migrated?

The migration for each organization will depend on its current configuration and readiness to migrate to the new infrastructure. These dates are subject to change.

- Organizations that use the HR module in Finance and Operations apps will receive the HR functionality for Dynamics 365 Human Resources as part of the regular One Version update process. New features are planned to become generally available beginning in January 2022.
- Organizations that use only Dynamics 365 Human Resources will have access to migration tooling so that they can begin testing and start the migration beginning in mid-2022. The date that the migration to the new infrastructure must be completed by hasn't yet been determined. However, it will be at least one year after the date when migration tooling becomes available.
- Organizations that use both Dynamics 365 Human Resources and other Finance and Operations apps will have access to migration tooling so that they can begin testing and start the migration beginning in late 2022. The date that the migration to the new infrastructure must be completed by hasn't yet been determined. However, it will be at least one year after the date when migration tooling becomes available.

For more information about the new features for Dynamics 365 Human Resources, see [What's new or changed in Human Resources](./hr-admin-whats-new.md).

### My organization has not yet gone live on Dynamics 365 Human Resources. Should we go live with the Human Resources module in the Finance and Operations apps or with the Dynamics 365 Human Resources app on the legacy infrastructure?

Important items to consider are what HR functionality is needed and when that functionality will be available on the new infrastructure. If the organization needs the core functionality for personnel management, that is currently available in the HR module of the Finance and Operations apps on the new infrastructure. Feature parity between the HR module of the Finance and Operations apps and the Dynamics 365 Human Resources app is expected in the 10.0.25 release, which is scheduled to be generally available in March 2022. Integration features like the Teams app and Dataverse entity integrations will be available in later releases.

If the organization HR functionality needs will be available on the new infrastructure within the timeframe in which the organization will go live, it may be easier to go live on the Human Resources module in the Finance and Operations apps. This will result in an easier migration as it will be a standard application upgrade to the Dynamics 365 Human Resources application and the customer will already be on the new infrastructure. If the organization decides to go live on the Dynamics 365 Human Resources application on the legacy infrastructure, then an environment migration will be needed to move to the new infrastructure. This can be avoided by going live on the new infrastructure.

### I am using new capabilities that are available only in Dynamics 365 Human Resources (such as **Leave and absence** and **Benefits management**). Will these capabilities now be available in the Human Resources module on the Finance and Operations infrastructure too?

Yes, all the modules from Dynamics 365 Human Resources will work as-is in Finance and Operations apps, and there will be 100-percent feature parity. As part of the overall migration strategy for customers who currently use these capabilities in HR, customer data will be migrated so that it continues to work on the Finance and Operations infrastructure.

### I use the new Dynamics 365 Human Resources benefits management capabilities. I've built custom integrations with the HR module on the Finance and Operations infrastructure so that I can take advantage of the payroll capabilities by using benefits data. Will these custom integrations be required going forward?

As part of the infrastructure merge, HR data is brought into the same database as other Finance and Operations apps. Integration between modules in Finance and Operations apps will no longer be required.

### My organization uses one or more ISV solutions with Dynamics 365 Human Resources. Will our ISV solutions be migrated automatically?

The migration experience for each independent software vendor (ISV) solution will vary, depending on the integration method of the solution. Microsoft will work closely with ISVs to ensure a smooth transition to the new infrastructure.

### My organization uses LinkedIn Talent Hub integration with Dynamics 365 Human Resources. Will this integration continue to work after the infrastructure change is completed?

No, the LinkedIn Talent Hub integration will not work after the migration to the new infrastructure. The service for LinkedIn Talent Hub integration will be retired with the legacy Dynamics 365 Human Resources infrastructure.

### My organization uses the Human Resources app for Teams. Will the app continue to work after the infrastructure change is completed?

Yes, the Human Resources app for Teams will continue to work after the migration to the new infrastructure.

### My organization has configured custom security in Dynamics 365 Human Resources. Will our custom security still be applied after the infrastructure change is completed?

Yes, custom security configurations will be included in the data migration to the new infrastructure.

### We are using Data integrator to move data between Dynamics 365 Human Resources and Finance and Operations apps. How will the data that is currently being integrated be affected?

HR data that is currently in Dynamics 365 Human Resources is synchronized with Dataverse. Data Integrator can then be used for one-way synchronization with Finance and Operations apps. After the migration to the new infrastructure, HR data will be native to the Finance and Operations apps. Data integrator will no longer be required to synchronize the data between Finance and Operations apps and Human Resources.

The current Dataverse native data tables for Human Resources will continue to synchronize the data from the environment on the new infrastructure. The entities will be converted to support dual-write. Any other data integrations that are configured via Data Integrator against these tables for other Dynamics 365 apps will continue to work as they are currently configured.

### We are using dual-write to move HR data between Dataverse and other Finance and Operations apps. How will the data that is currently being integrated be affected by the migration to the new infrastructure?

HR data will be native to the Finance and Operations apps in the environment on the new infrastructure. Dual-write will be used to move HR data between the new environment and the Dataverse environment.

### We have built custom integrations from Dynamics 365 Human Resources to one or more external systems. Will we have to develop new integrations after the infrastructure change is completed?

It depends on the integration endpoint. For more information about the integration technologies that are available in Finance and Operations apps, and how to choose the best integration technology, see [Integration overview](../fin-ops-core/dev-itpro/data-entities/integration-overview.md).

### We have extended Dataverse for Dynamics 365 Human Resources. Will these extensions be migrated automatically?

If the Dynamics 365 Human Resources and Finance and Operations environments that will be joined in the environment on the new infrastructure are connected to the same Dataverse environment, the two apps will continue to be connected to the same Dataverse environment after the migration. No migration will be required for any Dataverse extensions.

However, if the Dynamics 365 Human Resources and Finance and Operations environments are currently connected to separate Dataverse environments, the two Dataverse environments will have to be combined so that they are connected to a single environment on the new infrastructure. For this Dataverse migration, the Dataverse tables that are standard to the Human Resources solutions can be connected to and resynchronized with the new Dataverse environment. Any extensions to the Dataverse environment won't be migrated automatically but must be redeployed in the new environment. We recommend that you use managed solutions to manage your Dataverse extensions. For more information, see [Introduction to solutions](/powerapps/developer/data-platform/introduction-solutions).

### We have configured Microsoft Power Automate flows and/or Microsoft Power Apps to work with Dynamics 365 Human Resources. Will these Microsoft Power Platform components be migrated and work automatically after the infrastructure change is completed?

Power Apps, Power Automate flows, and other Microsoft Power Platform customizations are similar to Dataverse extensions. Whether they work automatically after the migration to the new infrastructure depends on whether the Human Resources app and the Finance and Operations apps are connected to the same Power Apps environment before the migration.

If the apps are currently connected to the same Power Apps environment, they will continue to be connected to that Power Apps environment after the migration to the new infrastructure. In this case, Power Apps, Power Automate flows, and other Microsoft Power Platform customizations will continue to work without any additional configuration. We recommend that you use managed solutions to manage your application extensions on the Dataverse. For more information, see [Introduction to solutions](/powerapps/developer/data-platform/introduction-solutions).

However, if the Human Resources app and the Finance and Operations apps are connected to separate Power Apps environments, they will have to be combined as part of the migration. This task will require that any Power Apps and other customizations be redeployed in the new environment.

### We have enabled Dataverse virtual tables for Dynamics 365 Human Resources. What will happen to these tables during the migration?

After the migration, if the environment on the new infrastructure remains connected to the Dataverse environment that is currently connected to Dynamics 365 Human Resources, the Dataverse virtual tables that have been generated in that environment will continue to work without any additional configuration.

However, if the environment on the new infrastructure is connected to a different Dataverse environment after the migration, the virtual tables will have to be regenerated in the new Dataverse environment.

### We have developed an integration by using the Applicant Tracking System (ATS) API, Payroll API, Dataverse virtual tables for Dynamics 365 Human Resources, or other entities in the Dataverse Web API. Will these integrations continue to work after the infrastructure change is completed?

After the migration, if the environment on the new infrastructure remains connected to the Dataverse environment that is currently connected to Dynamics 365 Human Resources, any integrations that have been developed against the Dataverse Web API will continue to work after the migration is completed.

However, if the environment on the new infrastructure is connected to a different Dataverse environment after the migration, any integrations that have been developed against the Dataverse Web API will have to be reconfigured so that they connect to the new Dataverse environment.

### Is there an impact on the Azure region when my environment is migrated?

It is expected that your Human Resources environment will typically remain in the same Azure region during the migration. The only exception is if the Human Resources environment will be merged with a Finance and Operations environment that is in a different region. In this case, the Human Resources environment will be migrated to the Azure region of the Finance and Operations environment.

### My organization depends on workflows in Dynamics 365 Human Resources for one or more business processes. Will the workflows be migrated automatically?

Yes, workflow configurations, workflow history, and current in-process workflows will be migrated.

### What training and resources will be available to help with the migration process?

Full documentation will be provided to describe each step of the migration process in detail. Additional training resources, such as videos and workshops, might also be available, depending on need.

### My organization has created Saved views in Dynamics 365 Human Resources to improve the usability of the interface. Will the Saved views be migrated automatically?

Yes, Saved views will be migrated to the new infrastructure.

### We are using Ceridian with Dynamics 365 Human Resources. Will the Ceridian integration be available after the infrastructure change is completed? 

The integration with Ceridian will be migrated to the Payroll API–based integration. The file-based integration that currently exists in Dynamics 365 Human Resources won't be migrated to the Finance and Operations infrastructure. For more information, see [Payroll API introduction](./hr-admin-integration-payroll-api-introduction.md).

### How will the migration affect the service update process?

After the migration, customers will have much more flexibility in terms of ALM and service updates. Service updates will no longer be applied automatically to Human Resources environments. Instead, the service will follow One Version service update processes and functionality. Therefore, configuration options for updates will be available through LCS. For more information, see [One Version overview](../fin-ops-core/dev-itpro/lifecycle-services/oneversion-overview.md).

### How will the migration affect my LCS project for Dynamics 365 Human Resources?

The migration to the new infrastructure will move management of your Dynamics 365 Human Resources environments into a Finance and Operations implementation project in LCS. If the migration is merging Dynamics 365 Human Resources with an existing Finance and Operations environment, your Human Resources LCS project will be merged into the LCS implementation project for the Finance and Operations app. If you're currently using only Dynamics 365 Human Resources, a new LCS implementation project will be created, and your existing Human Resources LCS project will be migrated to the new project.

The new project will be the same type of project that Finance and Operations apps use. It will have the same features and functionality for environment management. For more information, see [Lifecycle services resources](../fin-ops-core/dev-itpro/lifecycle-services/lcs.md).

### We have linked our task recordings to the Business Process Modeler in Human Resources. How will the Business Process Modeler be migrated and merged into LCS?

Business process libraries for the LCS project will be migrated to the new LCS project for Human Resources.

### My organization currently uses only Dynamics 365 Human Resources. What resources are available so that we can learn more about the development capabilities after the infrastructure change is completed?

Both Microsoft Power Platform extensibility options and Finance and Operations extensibility options will be available and can be used for development. For more information, see [Develop and customize home page](../fin-ops-core/dev-itpro/dev-tools/developer-home-page.md).

### We have enabled features in Dynamics 365 Human Resources. Will these features be enabled automatically during the migration?

Whether a feature is enabled automatically in the new infrastructure will be determined individually for each feature. This information will be included in the feature documentation.

### What happens to my BYOD database during the migration?

Import and export configurations for bring your own database (BYOD) will be migrated to the new infrastructure.

### What happens to my Azure Data Lake during the migration?

Any export that is currently configured for Azure Data Lake Storage in Finance and Operations apps will maintain the same configuration after the migration.

### We are currently using Dynamics AX 2012. Will the upgrade tools that are currently available be used to upgrade the HR module in AX 2012 to Dynamics 365 Human Resources?

Yes. Dynamics 365 Human Resources will be included in the merged codebase and infrastructure for Finance and Operations apps. An upgrade from Dynamics AX 2012 to Dynamics 365 Human Resources will use the same upgrade path and tooling that are used to upgrade to the latest version of Finance and Operations apps.

### We use Document handling with Dynamics 365 Human Resources. What will happen to the documents during the migration?

The documents will remain in the existing document storage. They will be remapped to the environment in the new infrastructure.

### What happens to the batch jobs that we have configured in Dynamics 365 Human Resources after the migration?

Applicable batch jobs will be migrated automatically to the new infrastructure.

## Licensing impact

This documentation doesn't supersede or replace any of the legal documentation that covers use rights.

### My organization uses Dynamics 365 Human Resources to manage its HR operations. Does our licensing or cost change?

Customers that have purchased Dynamics 365 Human Resources licenses won't be affected. There is no licensing migration for these customer. The additional sandbox stock keeping unit (SKU) that was specific for Human Resources will no longer be applicable. Instead, customers can choose to buy a Finance and Operations apps Tier 2 sandbox at a slightly lower cost. Existing customers who have purchased a Human Resources sandbox will be migrated to a Finance and Operations apps Tier 2 sandbox at no additional cost.

### My organization uses the Human Resources module in Dynamics 365 Finance, Supply Chain Management, Commerce, or Project Operations. Does my licensing or cost change?

Existing users of Dynamics 365 apps and users of stand-alone Dynamics 365 Finance, Supply Chain Management, Commerce, and Project Operations can access Human Resources as part of those licenses until February 2025 or until the current licensing agreement expires, whichever is earlier. You can choose to move to Human Resources licenses earlier if it helps you achieve better cost savings. Starting from February 2025, all existing CSP and EA customers must roll off the HR module and buy Human Resources licenses to take advantage of the new capabilities that are being brought to the Finance and Operations apps.

### My organization is live with Dynamics 365 Finance, Supply Chain Management, Commerce, or Project Operations. Will we be required to purchase an additional environment to support the infrastructure merge?

Additional environments aren't required to support the infrastructure change.

