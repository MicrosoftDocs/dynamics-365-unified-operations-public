---

# required metadata

title: Dynamics 365 Human Resources infrastructure merge FAQ
description: This article answers frequently asked questions about the infrastructure merge for Microsoft Dynamics 365 Human Resources and finance and operations apps.
author: twheeloc
ms.date: 11/15/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---

# Dynamics 365 Human Resources infrastructure merge FAQ

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

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

For more information about the migration to the finance and operations infrastructure, see [Human Resource customer migration FAQ](./customer-migration.md).
