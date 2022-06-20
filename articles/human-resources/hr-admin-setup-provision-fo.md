---
# required metadata

title: Provision Human Resources in the finance and operations infrastrcuture
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

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

>[!NOTE]
> Starting June 2022, Human Resources environments can only be deployed on the finance and operations app infrastrcuture. 

This article explains the process of provisioning a new production environment for Microsoft Dynamics 365 Human Resources in the finance and operations infrastructure.

## Prerequisites

Before you begin provisioning a new environment, the following prerequisites must be in place:

- You have purchased Human Resources through a Cloud Solution Provider (CSP) or enterprise architecture (EA) agreement. If you have an existing Microsoft Dynamics 365 license that already includes the Human Resources service plan, and you can't complete the steps in this article, contact Support.

- The global administrator has signed in to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com) (LCS) and created a new finance and operations project. 

## Provision a Human Resources trial environment

Starting April 2022, the Human Resources trial environments will not be available on the stand-alone application. Potential customers who are interested in evaluating the Human Resources capabilities within finance and operations apps, can do so using the free 30-day trial along with the demo data. Dynamics 365 Finance will include the Human Resources capabilities brought to the Finance infrastructure through the merge of the stand-alone application. For more information, see [Merging of HR offerings brings capabilities together for customers](https://cloudblogs.microsoft.com/dynamics365/it/2021/09/15/merging-of-hr-offerings-brings-capabilities-together-for-customers) For more information about Dynamics 365 Finance trials, see the step-by-step [guide](../fin-ops-core/fin-ops/get-started/before-you-buy.md). 

## Plan Human Resources environments

Before you create your first Human Resources environment, you should carefully plan the environment needs for your project. A base subscription to Human Resources includes two environments: a production environment and a default standard acceptance test (this was referred to as a Sandbox in the stand-alone Human Resources infrastructure) environment. Depending on the complexity of your project, you have the option to purchase additional environments to support project activities. 

Considerations for additional optional environments:

- **Data migration**: You may need to consider an additional environment for data migration activities to allow your sandbox environment to be used for testing purposes throughout the project. Having an additional environment allows data migrations activities to continue while testing and configuration activities occur simultaneously in a different environment.
- **Integration**: You may need to consider an additional environment to configure and test integrations. This could include native integrations or custom integrations such as those for payroll, applicant tracking systems, or benefit systems and providers.
- **Training**: You may need a separate environment that is configured with a set of training data in order to train your employees on use of the new system. 
- **Multi-phase project**: You may need an additional environment to support configuration, data migration, testing, or other activities in a project phase that is planned after the initial go-live of the project.
- **Development**: With the finance and operations infrastructure, you can now extend the solution and develop your own customizations. Each developer is required to use thier own development environment. For more information, see [Deploy and access development environments](/fin-ops-core/dev-itpro/dev-tools/access-instances).
- **GOLD**: It is common practice for new deployments to use a seperate "GOLD" environment that is kept pristine for configuration and data migration. This environment can be used throughout the implementation to refresh other environments. It will be used to create the new production environment with the base configuration and data migration. This practice is commonly used becuase you can't deploy a production environment on the finance and operations infrastructure until you have completed the go-live readiness process. For more infromation, see [Prepare for go-live](/fin-ops-core/fin-ops/imp-lifecycle/prepare-go-live) 

--NOTE: Need to come back and verify Tier-1 can be used and if a customer cannot purchase tier 3-5 need specific documentation about this. 

 > [!IMPORTANT]
 > As you consider your environments, we recommend the following:
 > - Use your default standard acceptance test (formerly Sandbox) or another environment to perform a mock cutover prior to your go-live. </br></br>
 > - Keep a detailed cutover checklist that includes each of the data packages required to migrate the final data into the production environment during the go-live cutover. This is especially important if you do not have a separate GOLD environment to store your configurations.</br></br>
 > - Use your default standard acceptance test (formerly Sandbox) or another tier-2 or higher environment throughout your project as your TEST environment. If you need additional environments, your organization can purchase them for an additional cost.</br></br>

## Create an LCS project

To use LCS to manage your Human Resources environments, you must first create an LCS project. If you are migrating your Human Resources environment to the finance and operations infrastrcuture you will need to create a new LCS project for finance and operations. For more information, see [Migrating your Human Resources environment](hr-admin-migrate-overview). If you already have an LCS project for other finance and operations apps, you can enable the Human Resources features in the **Feature management** workspace. For more information, see [Feature management overview](/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

When a new customer signs up for Human Resources, the subscription includes an Implementation project workspace. After the customer activates the service, the tenant administrator must sign in at https://lcs.dynamics.com by using the tenant account. The project workspace is automatically created for the organization. For more information, see [Lifecycle Services (LCS) for Finance and Operations apps customers](/fin-ops-core/dev-itpro/lifecycle-services/lcs-works-lcs).

> [!NOTE]
> To ensure successful provisioning, the account you use to provision the Human Resources environment must be assigned to either the **System Administrator** or **System Customizer** role in the Power Apps environment associated with the Human Resources environment. For more information about assigning security roles to users in the Power Platform, see [Configure user security to resources](/power-platform/admin/database-security).

You will be required to complete the LCS project onboarding process in order to start deploying environments. For more information, see [Project onboarding](/fin-ops-core/dev-itpro/lifecycle-services/project-onboarding). For more information about using LCS, see [Lifecycle Services (LCS) user guide](/fin-ops-core/dev-itpro/lifecycle-services/lcs-user-guide).

## Deploy Human Resources environments
Working with Microsoft to deploy finance and operations apps in the cloud, including Human Resources, requires that you understand the environment and subscription that you are deploying to, who can perform which tasks, and the data and customizations that you need to manage. It is recommended to use a service account, rather than a named user when you deploy new environments. To learn more about deploying environments in the finance and operations infrastrcuture, see [Cloud deployment overview](/fin-ops-core/dev-itpro/deployment/cloud-deployment-overview).

In order to deploy a production environment for Human Resources on the finance and operations infrastructure, you must complete the go-live readiness process. For more information, see [Prepare for go-live](/fin-ops-core/fin-ops/imp-lifecycle/prepare-go-live). This process includes the subscription estimator in LCS. For more information, see [Subscription estimator](/fin-ops-core/dev-itpro/lifecycle-services/subscription-estimator).

## Integrate the Power Platform with Human Resources
Microsoft Power Platform provides a suite of capabilities for Dynamics 365 applications via the Power Platform admin center. You can integrate and extend the use of Human Resources data using the Power Platform. For information about integrating Human Resources with the Power Platform, see [Microsoft Power Platform integration with Finance and Operations apps](/fin-ops-core/dev-itpro/power-platform/overview).  

## Supported geographies
To learn about the languages and geographies that are support for Dynamics 365 Human Resources, see [Global by design: learn about countries and languages supported](https://dynamics.microsoft.com/en-us/availability-reports/).

## Grant access to the environment
By default, the global administrator who created the environment has access to it. You must explicitly grant access to additional application users. You must add users and assign the appropriate roles to them in the Human Resources environment. For more information, see [Create new users](/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/create-new-users) and [Assign users to security roles](/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/assign-users-security-roles). 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
