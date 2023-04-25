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

To complete the following procedures and successfully configure business performance analytics, you must have system administrator and system customizer access in [Power Platform admin center](https://admin.powerplatform.microsoft.com/). You must also have system administrator access in Microsoft Dynamics 365 Finance, and access to create environments in Microsoft Dynamics Lifecycle Services.

## Configure Dataverse

To configure Dataverse for business performance analytics, follow these steps.

1. Sign in to [Lifecycle Services](https://lcs.dynamics.com/), open the environment details page, and confirm that the Microsoft Power Platform integration is set up.
2. If Dataverse has already been set up, the name of the Dataverse environment that's linked to the finance environment will be listed. 
3. If Dataverse hasn't yet been set up, select **Setup**. After the setup is successfully completed, the name of the Dataverse environment that's linked to the Finance environment should be listed.
4. If this integration was set up for an existing Microsoft Power Platform environment, confirm that the linked environment isn't in a disabled state. For more information, see [Enable Power Platform integration](//fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration). To access Power Platform admin center, go to <https://admin.powerplatform.microsoft.com/>.

## Configure your Azure AD tenant

Azure Active Directory (Azure AD) must be configured so that it can be used with Dataverse and the Microsoft Power Platform applications. The **Project owner** or **Environment manager** role must be assigned to the user in the **Project security role** field in Lifecycle Services.
The following setup must be completed:
1. You must have system administrator and system customizer access in Power Portal admin center.
2. A Dynamics 365 Finance or equivalent license must be applied to the user who installs business performance analytics.

## Move data from a production environment to a sandbox environment

To move data from your production environment to a sandbox environment, follow the instructions in [Data movement](//fin-ops-core/dev-itpro/database/dbmovement-operations). This data will be loaded into business performance analytics and is a prerequisite for the installation of business performance analytics.

## Required configurations

The following items are required in the environment before you can install business performance analytics. They're also required for record to report.

- SQL row version change tracking (preview)
- General ledger
- Budget
- Reversing entries

You can confirm these settings in Dynamics 365 Finance. Go to **System administration \> Setup \> License configuration**.

Before you can enable these items, the system must be in maintenance mode.

### Turn on maintenance mode by using Lifecycle Services

1. In Lifecycle Services, open the environment details page.
2. Select **Maintain \> Enable maintenance mode**.
3. Once the configuration is enabled, disable maintenance mode.
