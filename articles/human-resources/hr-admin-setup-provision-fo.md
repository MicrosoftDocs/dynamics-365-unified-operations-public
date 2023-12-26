---
# required metadata

title: Provision Human Resources in the finance and operations infrastructure
description: This article explains the process of provisioning a new production environment for Microsoft Dynamics 365 Human Resources in the finance and operations infrastructure.
author: twheeloc
ms.date: 01/07/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SystemAdministrationWorkspaceForm
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Provision Human Resources in the finance and operations infrastructure

_**Applies To:** Human Resources on the finance and operations app infrastructure_ 

> [!NOTE]
> Starting July 2022, new Human Resources environments can't be provisioned on the stand-alone Human Resources infrastructure, and new Microsoft Dynamics Lifecycle Services (LCS) projects can't be created on it. Customers can deploy Human Resources environments on the finance and operations infrastructure.

This article explains the process of provisioning a new production environment for Microsoft Dynamics 365 Human Resources in the finance and operations infrastructure.

## Prerequisites

Before you start to provision a new environment, the following prerequisites must be in place:

- You've purchased Human Resources through a Cloud Solution Provider (CSP) or enterprise architecture (EA) agreement. If you have an existing Dynamics 365 license that already includes the Human Resources service plan, and you can't complete the steps in this article, contact Support.
- The global administrator has signed in to [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com) and created a new finance and operations project.

## Provision a Human Resources trial environment

> [!NOTE]
> Starting April 2022, the Human Resources trial environments won't be available in the stand-alone application. Potential customers who are interested in evaluating the Human Resources capabilities in finance and operations apps can use the free 30-day trial together with the demo data. Dynamics 365 Finance will include the Human Resources capabilities that are brought to the Finance infrastructure through the merge of the stand-alone application. For more information, see [Merging of HR offerings brings capabilities together for customers](https://cloudblogs.microsoft.com/dynamics365/it/2021/09/15/merging-of-hr-offerings-brings-capabilities-together-for-customers). For more information about Dynamics 365 Finance trials, see the [step-by-step guide](../fin-ops-core/fin-ops/get-started/before-you-buy.md).

## Plan Human Resources environments

Before you create your first Human Resources environment, you should carefully plan the environment needs for your project. A base subscription to Human Resources includes two environments: a production environment and a default standard acceptance test (Sandbox) environment. Depending on the complexity of your project, you have the option to purchase additional environments to support project activities.

Here are some considerations for additional optional environments:

- **Data migration** – Data migration activities enable your sandbox environment to be used for testing purposes throughout the project. When you have an additional environment, data migration activities can continue while testing and configuration activities occur simultaneously in a different environment.
- **Integration** – Configure and test integrations, which might include native integrations or custom integrations, such as those for payroll, applicant tracking systems, or benefit systems and providers.
- **Training** – You might need a separate environment that is configured with a set of training data, so that you can train your employees how to use the new system. 
- **Multi-phase project** – You might need an additional environment to support configuration, data migration, testing, or other activities in a project phase that is planned after the initial go-live of the project.
- **Development** – In the finance and operations infrastructure, you can now extend the solution and develop your own customizations. Each developer is required to use their own development environment. For more information, see [Deploy and access development environments](../fin-ops-core/dev-itpro/dev-tools/access-instances.md).
- **GOLD** – For new deployments, a common practice is to use a separate GOLD environment that is kept pristine for configuration and data migration. This environment can be used throughout the implementation to refresh other environments. It will be used to create the new production environment that has the base configuration and data migration. You can't deploy a production environment on the finance and operations infrastructure until you've completed the go-live readiness process. For more information, see [Prepare for go-live](../fin-ops-core/fin-ops/imp-lifecycle/prepare-go-live.md).

<!--NOTE: Need to come back and verify Tier-1 can be used and if a customer cannot purchase tier 3-5 need specific documentation about this.-->

> [!IMPORTANT]
> As you consider your environments, we recommend the following approach:
>
> - Use your default standard acceptance test (formerly Sandbox) environment or another environment to do a mock cutover before your go-live.
> - Keep a detailed cutover checklist that includes each data package that is required to migrate the final data to the production environment during the go-live cutover. This recommendation is especially important if you don't have a separate GOLD environment to store your configurations.
> - Use your default standard acceptance test (formerly Sandbox) environment or another tier-2 or higher environment as your TEST environment throughout your project. If you need additional environments, your organization can purchase them at an additional cost.

## Create an LCS project

To use LCS to manage your Human Resources environments, you must first create an LCS project. If you're migrating your Human Resources environment to the finance and operations infrastructure, you must create a new LCS project for finance and operations apps. If you already have an LCS project for other finance and operations apps, you can enable the Human Resources features in the **Feature management** workspace. For more information, see [Feature management overview](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

When a new customer signs up for Human Resources, the subscription includes an Implementation project workspace. After the customer activates the service, the tenant administrator must sign in at <https://lcs.dynamics.com> by using the tenant account. The project workspace is automatically created for the organization. For more information, see [Lifecycle Services (LCS) for Finance and Operations apps customers](../fin-ops-core/dev-itpro/lifecycle-services/lcs-works-lcs.md).

> [!NOTE]
> To ensure successful provisioning, the account that you use to provision the Human Resources environment must be assigned to either the **System Administrator** role or the **System Customizer** role in the Power Apps environment that is associated with the Human Resources environment. For more information about how to assign security roles to users in Microsoft Power Platform, see [Configure user security to resources](/power-platform/admin/database-security).

You must complete the LCS project onboarding process before you can start to deploy environments. For more information, see [Project onboarding](../fin-ops-core/dev-itpro/lifecycle-services/project-onboarding.md). For more information about how to use LCS, see [Lifecycle Services (LCS) user guide](../fin-ops-core/dev-itpro/lifecycle-services/lcs-user-guide.md).

## Deploy Human Resources environments

Deployment of finance and operations apps, including Human Resources, in the cloud requires that you understand the environment and subscription that you're deploying to, who can perform which tasks, and what data and customizations you must manage. We recommend that you use a service account instead of a named user when you deploy new environments. For more information about how to deploy environments on the finance and operations infrastructure, see [Cloud deployment overview](/fin-ops-core/dev-itpro/deployment/cloud-deployment-overview).

To deploy a production environment for Human Resources on the finance and operations infrastructure, you must complete the go-live readiness process. For more information, see [Prepare for go-live](../fin-ops-core/fin-ops/imp-lifecycle/prepare-go-live.md). This process includes the subscription estimator in LCS. For more information, see [Subscription estimator](../fin-ops-core/dev-itpro/lifecycle-services/subscription-estimator.md).

## Integrate Microsoft Power Platform with Human Resources

Microsoft Power Platform provides a suite of capabilities for Dynamics 365 applications via the Power Platform admin center. You can integrate and extend the use of Human Resources data by using Microsoft Power Platform. For information about how to integrate Human Resources with Microsoft Power Platform, see [Microsoft Power Platform integration with Finance and Operations apps](../fin-ops-core/dev-itpro/power-platform/overview.md).

## Supported geographies

For information about the languages and geographies that are supported for Human Resources, see [Global by design: learn about countries/regions and languages supported](https://dynamics.microsoft.com/availability-reports/).

## Grant access to the environment

By default, the global administrator who created the environment has access to it. You must explicitly grant access to additional application users. You must add users and assign the appropriate roles to them in the Human Resources environment. For more information, see [Create new users](/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/create-new-users) and [Assign users to security roles](/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/assign-users-security-roles).

## Additional resources
You can learn more about how to use and manage projects in LCS on the finance and operations app infrastructure by using the following resources:

- [Lifecycle Services resources](../fin-ops-core/dev-itpro/lifecycle-services/lcs.md)
- [Lifecycle Services (LCS) user guide](../fin-ops-core/dev-itpro/lifecycle-services/lcs-user-guide.md)
- [Self-service deployment overview](../fin-ops-core/dev-itpro/deployment/infrastructure-stack.md)
- [Database movement operations home page](../fin-ops-core/dev-itpro/database/dbmovement-operations.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
