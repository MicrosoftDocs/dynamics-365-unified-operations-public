---

# required metadata

title: Dynamics 365 Human Resources infrastructure merge overview
description: This article describes the Microsoft Dynamics 365 Human Resources infrastructure merge.
author: twheeloc
ms.date: 10/24/2022
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
# Dynamics 365 Human Resources infrastructure merge 

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

##  Dynamics Human Resources 365

Microsoft Dynamics 365 Human Resources provides tools that help HR teams increase organizational agility, transform the employee experience, and optimize HR programs to
create a workplace where people and the business can thrive. To learn more about Dynamics 365 Human Resources, see [Dynamics 365 Human Resources](https://dynamics.microsoft.com/human-resources/overview/).

- **Transform employee experiences.** Retain top performers by empowering managers and employees through connected self-service experiences that drive engagement and 
growth.
- **Optimize HR programs** Decrease operational costs, and create people-centric leave and absence, time, benefit, and compensation management programs.
- **Increase organizational agility** Enable HR to operate with the dexterity that the business requires by using Dataverse and Microsoft Power Platform to centralize
people data and easily extend Dynamics 365 Human Resources.
- **Discover workforce insights** Make data-driven decisions through the ability to analyze and visualize people data on rich dashboards that are available on any 
device.

## Human Resources infrastructure merge
Dynamics 365 Human Resources is a standalone application that uses a different infrastructure than other finance and operations apps, such as Dynamics 365 Finance or 
Dynamics 365 Supply Chain Management. The infrastructure merge will bring Dynamics 365 Human Resources into the same infrastructure as other finance and operations apps. To learn more about Human Resources infrastructure merge, see [Merging of HR offerings](https://cloudblogs.microsoft.com/dynamics365/it/2021/09/15/merging-of-hr-offerings-brings-capabilities-together-for-customers/). 
To learn more about frequently asked questions, see [Human Resources infrastructure merge FAQ](./hr-infrastructure-merge-faq.md) 

## Customer migration vs. customer merge

As part of the infrastructure merge, all Human Resources application capabilities have been made available on finance and operations environments. With the 
availability of the migration tooling through Lifecycle services (LCS), customers may migrate their Human resources environment(s). Customers may optionally elect to merge their data with their existing finance and operations environment. 

The difference between customer migration and customer merge is as follows:
-	Customer migration: This is a lift and shift migration of customer database using the automated migration tooling to the finance and operations infrastructure. The result is a new finance and operations environment utilizing the customer’s Human resources database. 
-	Customer merge: This not required by Microsoft and is at the customer’s discretion. This is an additional step to move customer data into an existing environment like a Dynamics 365 Finance or Project Operations environment. This is mostly manual and can be done using DMF data entities, on customer’s own timeline. 

>[!Note] 
> Lift and shift migration is the movement of customer database from the Human Resources infrastructure to the finance and operations infrastructure. 

## Planning a Human Resources environment migration

As a part of the Dynamics 365 Human Resources infrastructure merge, all customers will be required to migrate their existing Human Resources environments from the 
standalone infrastructure. To help this process, we recommend using the automated migration tooling in Lifecycle Services (LCS) to move your current environments 
to the new infrastructure. 

The following sections provide more detail about how to use the LCS tools to migrate a standalone human resources environment. 
When planning for the migration, customers can expect the following:
 - All customers will be required to migrate a sandbox environment before the production environment can be migrated. 
 - Migration tooling allows sandbox to sandbox and production to production migration only. This means that your environment type will determine what environment can be
migrated appropriately. 
 - Customers can migrate as many sandboxes as required if a target sandbox slot is available before migrating their production environment. Customers can also delete a migrated sandbox and remigrate multiple times. 
 - If a sandbox migration fails, or you want to start over, you can delete an environment on the finance and operations infrastructure and remigrate the same environment again.
 - The URL of your Dynamics 365 Human Resources environment will be different after the migration.
 - Plan an appropriate amount of downtime for your production environment migration. The estimated timeframe for the automated migration process to complete is 
approximately 3 to 4 hours. The estimated timeframe will vary based on your organization’s data. You should validate the amount of time required during your sandbox
environment migration and allow for time for any additional manual tasks that must be completed.

>[!Important] 
> When a production environment is successfully migrated to finance and operations, the source standalone production environment is automatically deleted. You shouldn't delete the migrated production environment. 

The process for the migration is mostly automatic, some manual steps and validation after the migration will be required by your business users. 
The following manual steps need to be completed:
 - Create a new LCS project for the migration.
 - Revise any integrations in your old environment to the new environment by pointing the integration to the new URL/endpoints based on each integration configuration.
 - Refresh the data store for embedded PowerBI reports.
 - Refresh data entity list from Data Management Framework (DMF) workspace.
 - Link to LCS for help.
 - Create fiscal calendars.

During the automatic process the following actions are completed and you'll want to validate the following:

 - Data
    -   Configurations
    -   Security roles (including custom roles)
    -   Workflows
    -   Personalizations and saved views
    -   Transactions
    -   Custom fields
    -   Attachments

 - Data management – Bring your own database (BYOD)
 - Feature management - Enabled/disabled features
 - Embedded PowerApps
 - PPAC attached Environment (production only)
 - Batch Jobs
 - An empty ledger is created for each legal entity. The default exchange rate type and the accounting currency for each ledger is set.
 - A new chart of accounts is automatcially created and linked to the **Ledger** page in each Legal entity. The financial dimensions configured in your Human Resources environment will be automatcially added to a new Account structure and linked to the ledger. 

>[!Note]
>A ledger is required in finance and operations as part of the Dynamics 365 Finance product. The custom dimension controller that existed in Dynamics 365 Human Resources standalone application isn't available. The merged infrastructure for Human Resources is dependent on the finance logic for displaying financial dimensions in the Human Resources module. Learn more about the chart of accounts and financial dimensions here. 

## Considerations

 - Migration to environments will always be on the latest generally available (GA) version. Based on your migration and testing plan, if your migration validation for
sandbox environment(s) were on a different version, it's recommended to validate a sandbox migration on the same version as your production environment. 
 - The migrated environment(s) will be placed in the same region as the source standalone Human Resources environment(s) during migration.

## Licensing

There are no changes to licensing for Dynamics 365 Human Resources including: 
 - Minimum license purchase requirement 
 - License(s) to a production and a sandbox environment: If you have existing standalone Human Resources license(s) that grants one production and one sandbox 
environment, the same is available on the finance and operations infrastructure, at no additional cost.
 - Additional sandbox license(s): If you have purchased additional sandbox license(s) for standalone Human Resources application, the same number of sandbox license(s) 
are available for a standard acceptance test (sandbox) environment on the finance and operations infrastructure at no extra cost. 



