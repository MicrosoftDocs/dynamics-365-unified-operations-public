---

# required metadata

title: Dynamics 365 Human Resources infrastructure merge overview
description: This article describes the Microsoft Dynamics 365 Human Resources infrastructure merge.
author: twheeloc
ms.date: 05/15/2023
ms.topic: overview
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
[!include [preview banner](../includes/preview-banner.md)]

## Dynamics Human Resources 365

Microsoft Dynamics 365 Human Resources provides tools that help HR teams increase organizational agility, transform the employee experience, and optimize HR programs to create a workplace where people and the business can thrive. To learn more about Dynamics 365 Human Resources, see [Dynamics 365 Human Resources](https://dynamics.microsoft.com/human-resources/overview/).

- **Transform the employee experience.** Retain top performers by empowering managers and employees through connected self-service experiences that drive engagement and growth.
- **Optimize HR programs.** Help decrease operational costs, and create people-centric leave and absence, time, benefit, and compensation management programs.
- **Increase organizational agility.** Enable HR to operate with the dexterity that the business requires by using Dataverse and Microsoft Power Platform to centralize people data and easily extend Dynamics 365 Human Resources.
- **Discover workforce insights.** Make data-driven decisions through the ability to analyze and visualize people data on rich dashboards that are available on any device.

## Human Resources infrastructure merge

Dynamics 365 Human Resources is a standalone application that currently uses a different infrastructure than other finance and operations apps, such as Dynamics 365 Finance or Dynamics 365 Supply Chain Management. The infrastructure merge will bring Dynamics 365 Human Resources into the same infrastructure as other finance and operations apps.

To learn more about the Human Resources infrastructure merge, see [Merging of HR offerings](https://cloudblogs.microsoft.com/dynamics365/it/2021/09/15/merging-of-hr-offerings-brings-capabilities-together-for-customers/). For answers to frequently asked questions, see [Human Resources infrastructure merge FAQ](./hr-infrastructure-merge-faq.md).

## Value and benefits of the infrastructure merge

What is the Dynamics 365 Human Resources infrastructure merge?
There are currently two separate sets of HR capabilities on two different infrastructures in Dynamics 365:
 - Dynamics 365 Human Resources – A stand-alone app that runs on an independent infrastructure. When this app was launched, the infrastructure was separated from other Dynamics 365 operations apps. Our customers use this app to increase organizational agility, optimize HR programs, transform employee experiences, and gain workforce insights.
 - HR module – A legacy set of capabilities that was previously part of the Unified Operations licensing. The HR module runs on the finance and operations infrastructure, which is the same across all operations apps. These apps include Dynamics 365 Finance, Dynamics 365 Project Operations, and Dynamics 365 Supply Chain Management. Customers received the HR capabilities as part of Dynamics 365 Finance or Dynamics 365 Supply Chain Management.
 
Over the last three years, Microsoft has not enhancemented the HR module. Instead, our investments have focused on the Dynamics 365 Human Resources app.
By bringing these two sets of capabilities onto the same infrastructure, customers benefit by:
 - Enhancements that have been added to Dynamics 365 Human Resources over the last three years, including enhanced leave and absence, benefit management, and reporting.
 - Improved extensibility through Microsoft Power Platform and the ability to extend business logic to personalize pages.
 - Improved deployment, updates, and maintenance that are consistent in terms of application lifecycle management (ALM), lifecycle services, geographic availability, and more.
 - More technological innovation as our engineering team uses shared services, tooling, and reduced platform costs.

This transition affects customers who are currently using either Dynamics 365 Human Resources or the legacy HR module.

For more inforamtion about the infrastructure merge, see [Infrastructure merge FAQ](hr-infrastructure-merge-faq.md#general-questions-about-the-infrastructure-merge).


## Customer migration vs. customer merge

As part of the infrastructure merge, all capabilities of the Human Resources application have been made available in finance and operations environments. Customers can migrate their Human Resources environments by using the migration tooling that is available in Microsoft Dynamics Lifecycle Services. They can also optionally merge their data with their existing finance and operations environment. 

Customer migration and customer merge differ in the following way:

- **Customer migration** – The automated migration tooling is used to perform a "lift-and-shift migration" (movement) of the customer database from the Human Resources infrastructure to the finance and operations infrastructure. The result is a new finance and operations environment that uses the customer's Human Resources database. 
- **Customer merge** – This additional step isn't required by Microsoft. It's done at the customer's discretion and on the customer's own timeline. During this step, customer data is moved into an existing environment, such as a Finance or Project Operations environment. It's mostly manual and can be done by using Data Management Framework (DMF) data entities. 

## Planning a Human Resources environment migration

As part of the infrastructure merge, all customers will be required to migrate their existing Human Resources environments from the standalone infrastructure. To help this process, we recommend that you use the automated migration tooling in Lifecycle Services to move your current environments to the new infrastructure. 

The following sections provide more detail about how to use the Lifecycle Services tools to migrate a standalone Human Resources environment. 

Customers that are planning a migration can have the following expectations:

- All customers will be required to migrate a sandbox environment before the production environment can be migrated. 
- Migration tooling enables only sandbox-to-sandbox and production-to-production migration. Therefore, your environment type will determine what environment can be appropriately migrated. 
- Customers can migrate as many sandboxes as required before they migrate their production environment, provided that a target sandbox slot is available. Customers can also delete a migrated sandbox and remigrate multiple times. 
- If a sandbox migration fails, or if you want to start over, you can delete an environment on the finance and operations infrastructure and remigrate the same environment.
- The URL of your Human Resources environment will be different after the migration.
- Plan an appropriate amount of downtime for the migration of your production environment. The estimated timeframe for completion of the automated migration process is three to four hours. The timeframe will vary, depending on your organization's data. You should validate the amount of time that is required during the migration of your sandbox environments and allow time for any additional manual tasks that must be completed.

> [!IMPORTANT] 
> When a production environment is successfully migrated to the finance and operations infrastructure, the source standalone production environment is automatically deleted. You should not delete the migrated production environment. 

The process for the migration is mostly automatic. However, your business users will have to complete some manual steps and validation after the migration.

The following manual steps must be completed:

- Create a new Lifecycle Services project for the migration.
- Revise any integrations in your old environment to the new environment by pointing the integration to the new URL/endpoints, based on each integration configuration.
- Refresh the data store for embedded Power BI reports.
- Refresh the data entity list from the DMF workspace.
- Link to Lifecycle Services for help.
- Create fiscal calendars.

During the automatic process, the following actions are completed and should be validated:

- Data:

    - Configurations
    - Security roles (including custom roles)
    - Workflows (including notifications)
    - Personalizations and saved views
    - Transactions
    - Custom fields
    - Attachments
    - Alerts

- Data management – Bring your own database (BYOD).
- Feature management - Enabled/disabled features.
- Embedded Power Apps.
- Power Platform admin center attached environment (production only).
- Batch jobs.
- An empty ledger is created for each legal entity. The default exchange rate type and the accounting currency for each ledger are set.
- A new chart of accounts is automatically created and linked to the **Ledger** page in each legal entity. The financial dimensions that are configured in your Human Resources environment will automatically be added to a new account structure and linked to the ledger. 

> [!NOTE]
> A ledger is required on the finance and operations infrastructure as part of the Dynamics 365 Finance product. The custom dimension controller that existed in the Dynamics 365 Human Resources standalone application isn't available. The merged infrastructure for Human Resources depends on the Finance logic to show financial dimensions in the **Human Resources** module. To learn more about the chart of accounts and financial dimensions, see [here](../finance/general-ledger/plan-chart-of-accounts.md). 

## Considerations

- Migration to environments will always be on the latest generally available (GA) version. Depending on your migration and testing plan, if your migration validation for sandbox environments was on a different version, we recommend that you validate a sandbox migration on the same version as your production environment. 
- During migration, the migrated environments will be placed in the same region as the source standalone Human Resources environments.

## Licensing

There are no changes to licensing for Dynamics 365 Human Resources in the following areas: 

- **Minimum license purchase requirement**
- **Licenses to a production and a sandbox environment** – If you have existing standalone Human Resources licenses that grants one production environment and one sandbox environment, the same number of licenses is available on the finance and operations infrastructure, at no additional cost.
- **Additional sandbox licenses** – If you've purchased additional sandbox licenses for the standalone Human Resources application, the same number of sandbox licenses 
is available for a standard acceptance test (sandbox) environment on the finance and operations infrastructure, at no additional cost. 
