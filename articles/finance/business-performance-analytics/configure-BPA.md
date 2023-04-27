---
# required metadata

title: Configure business performance analytics
description: This article describes how to configure business performance analytics.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 04/24/2023
ms.topic: conceptual
ms.prod: 
ms.technology:
ms.custom:

---

# Configure business performance analytics

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change.
>
> For more information about how to participate in the public preview of business performance analytics, contact <bpateam@microsoft.com>.

This article describes how to configure business performance analytics.

To complete the following procedures and successfully configure business performance analytics, you must have the following privileges:
 - **System Administrator** and **System Customizer** role in [Power Platform admin center](https://admin.powerplatform.microsoft.com/). 
 - **System administrator** role in Microsoft Dynamics 365 Finance, and 
 - **Organization Admin** role to create environments in Microsoft Dynamics Lifecycle Services. Additionally, the **Project owner** or **Environment manager** role must be assigned to the user in the **Project security** role field in Microsoft Dynamics Lifecycle Services.

## Configure Power Platform

To configure Power Platform for business performance analytics, follow these steps.

1. Sign in to [Lifecycle Services](https://lcs.dynamics.com/), and navigate to the details page of the implementation project used to manage the Microsoft Dynamics 365 Finance environment.
2. Click on Full Details for the environment which you wish to use for the setup.
3. Check if the Power Platform Integration is visible.
4. If Power Platform has already been set up, the name of the Power Platform environment linked to the Microsoft Dynamics 365 Finance environment will be listed and shows status as “Power Platform environment setup is complete”.
5. If Power Platform has not yet been set up, select Setup and follow the prompts as required. After the setup is successfully completed, the name of the Power Platform environment linked to the Microsoft Dynamics 365 Finance environment should be listed.
6. If this integration was set up for an existing Microsoft Power Platform environment, confirm that the linked environment isn't in a disabled state. For more information, see [Enable Power Platform integration](//fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration). To access Power Platform admin center, go to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

## Configure  Azure AD tenant

Microsoft Azure Active Directory (Azure AD) must be configured so that it can be used with Power Platform. The following setup must be completed:
1. Navigate to the azure portal license assignment page [Licenses - Microsoft Azure](https://ms.portal.azure.com/#view/Microsoft_AAD_IAM/LicensesMenuBlade/~/Products) using credentials of the tenant administrator.
2. Apply a Dynamics 365 Finance or equivalent license to the user who installs business performance analytics. 
For more details, go to [Assign or remove licenses - Microsoft Entra | Microsoft Learn](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/license-users-groups)

## Move data from a production environment to a sandbox environment

To move data from your production environment to a sandbox environment, follow the instructions in [Data movement](//fin-ops-core/dev-itpro/database/dbmovement-operations). This data will be loaded into business performance analytics and is a prerequisite for the installation of business performance analytics.

## Required configurations in Microsoft Dynamics 365 Finance

The following items are required in the Microsoft Dynamics 365 Finance before you can install business performance analytics.

1. Turn on maintenance mode by using Microsoft Dynamics Lifecycle Services
  a) In Microsoft Dynamics Lifecycle Services, open the environment details page.
  b) Select **Maintain > Enable maintenance mode**.
2. In Microsoft Dynamics 365 Finance, navigate to **System administration > License configuration**.
  a) Check that **SQL row version change tracking (preview)** is enabled. If not, enable the checkbox.
  b) Check that the **Budget** and **Reversing entries** are enabled in **General ledger**. If not, enable these checkboxes.

Once the configuration is enabled, disable maintenance mode.
