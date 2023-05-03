---
# required metadata

title: Set up business performance analytics
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

# Set up business performance analytics

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for business performance analytics, contact <bpaquestions@service.microsoft.com>.

This article describes how to configure business performance analytics.

To complete the following procedures and successfully configure business performance analytics, you must have the following privileges:

- The **System Administrator** and **System Customizer** roles in [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
- The **System administrator** role in Microsoft Dynamics 365 Finance.
- The **Organization Admin** role to create environments in Microsoft Dynamics Lifecycle Services. Additionally, the **Project owner** or **Environment manager** role must be assigned to the user in the **Project security** role field in Lifecycle Services.

## Configure Microsoft Power Platform

To configure Microsoft Power Platform for business performance analytics, follow these steps.

1. Sign in to [Lifecycle Services](https://lcs.dynamics.com/).
2. Go to the details page of the implementation project that's used to manage the Dynamics 365 Finance environment.
3. Select **Full details** for the environment that you want to use for the setup.
4. Confirm that the Microsoft Power Platform Integration is shown. If Microsoft Power Platform has been set up, the name of the Microsoft Power Platform environment that's linked to the Dynamics 365 Finance environment will be listed and will show a status of **Power Platform environment setup is complete**. If Microsoft Power Platform hasn't yet been set up, select **Setup**, and follow the prompts as required. After the setup is successfully completed, the name of the Microsoft Power Platform environment that's linked to the Dynamics 365 Finance environment should be listed.
5. If the integration was set up for an existing Microsoft Power Platform environment, confirm that the linked environment isn't in a disabled state. For more information, see [Enable Power Platform integration](//fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration). For more information, go to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

## Configure the Azure AD tenant

Azure Active Directory (Azure AD) must be configured so that it can be used with Microsoft Power Platform. The following setup must be completed.

1. In the Azure portal, go to the [license assignment page](https://ms.portal.azure.com/#view/Microsoft_AAD_IAM/LicensesMenuBlade/~/Products). Sign in by using the credentials of the tenant administrator.
2. Apply a Dynamics 365 Finance or equivalent license to the user who's installing business performance analytics.

For more details, see [Assign or remove licenses](/azure/active-directory/fundamentals/license-users-groups).

## Move data from a production environment to a sandbox environment

To move data from your production environment to a sandbox environment, follow the instructions in [Data movement](//fin-ops-core/dev-itpro/database/dbmovement-operations). This data will be loaded into business performance analytics and is a prerequisite for the installation of business performance analytics.

## Required configurations in Dynamics 365 Finance

The following setup is required in the Dynamics 365 Finance before you can install business performance analytics.

1. Turn on maintenance mode by using Lifecycle Services.

    1. In Lifecycle Services, open the environment details page.
    2. Select **Maintain \> Enable maintenance mode**.

2. In Dynamics 365 Finance, follow these steps:

    1. Go to **System administration \> License configuration**.
    2. Confirm that **SQL row version change tracking (preview)** is enabled. If it isn't, select the checkbox.
    3. In **General ledger**, confirm that **Budget** and **Reversing entries** are enabled. If they aren't, select the checkboxes.

3. When you've finished, disable maintenance mode.
