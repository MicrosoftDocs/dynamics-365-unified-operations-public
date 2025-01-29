---
title: What are the prerequisites to installing Business performance analytics
description: This article describes how to complete the prerequisites for Business performance analytics, including outlines on availability, and systema and version requirements.
author: jinniew
ms.author: jiwo
ms.topic: conceptual
ms.date: 12/17/2024

ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Prerequisites to installing Business performance analytics 

## Before you install

Business performance analytics is currently supported in the following regions: Australia, UK, USA, Europe, Canada, and Japan. It will be available in these regions when Business performance analytics is generally available and in sovereign clouds after Business performance analytics is generally available.

Support for the following regions will be added by January 2025: India, Brazil, East Asia, UAE, Norway, South Africa, and Switzerland.

### System requirements

A Tier-2 environment (multi-box) is required to preview business performance analytics. For more information about environments, see [Environment planning](../../fin-ops-core/fin-ops/imp-lifecycle/environment-planning.md).

### Version requirements

Business performance analytics requires Dynamics 365 Finance version 10.0.38 (Application version 10.0.1777.94) or later.

### What are the prerequisites to installing Business performance analytics

The following items are required before installing Business performance analytics:

- Set up required privileges in Power Platform and Dynamics 365 Finance
- Configure Microsoft Power Platform
- Configure the Microsoft Entra tenant
- Move data from a production environment to a sandbox environment (if needed)
- Confirm the Power App users are enabled in Dynamics 365 Finance
- Configure Dynamics 365 Finance
- Configure Power Platform Admin Center

#### Required privileges

- In Power Platform:

    - The **System Administrator** and **System Customizer** roles in [Power Platform admin center](https://admin.powerplatform.microsoft.com/). Follow these steps to confirm that you have these privileges:

        1. In the Power Platform Admin Center, go to **Environments**.
        2. Select the relevant environment.
        3. In the **Access** section, select users.
        4. Select **Installing user** > **Roles**. Confirm the necessary privileges.

- In Microsoft Dynamics 365 Finance:

    - The **System administrator** role in Microsoft Dynamics 365 Finance. Follow these steps to confirm that you have these privileges:

        1. In Dynamics 365 Finance, go to **System administration**.
        2. Select **Users** > **Users**.
        3. Select **Installing user** > **Roles**. Confirm the necessary permissions.

- In Microsoft Dynamics Lifecycle Services:

    - The **Organization Admin** role to create environments. Additionally, the **Project owner** or **Environment manager** role must be assigned to the user in the **Project security** role field in Lifecycle Services.

#### Configure Microsoft Power Platform

To configure Microsoft Power Platform for Business performance analytics, follow these steps.

1. Sign in to [Lifecycle Services](https://lcs.dynamics.com/).
2. Go to the details page of the implementation project that's used to manage the Dynamics 365 Finance environment.
3. Select **Full details** for the environment that you want to use for the setup.
4. Confirm that the Microsoft Power Platform Integration is shown. If Microsoft Power Platform has been set up, the name of the Microsoft Power Platform environment that's linked to the Dynamics 365 Finance environment will be listed and shows a status of **Power Platform environment setup is complete**. If Microsoft Power Platform hasn't yet been set up, select **Setup**, and follow the prompts as required. After the setup is successfully completed, the name of the Microsoft Power Platform environment that's linked to the Dynamics 365 Finance environment should be listed.
5. If the integration was set up for an existing Microsoft Power Platform environment, confirm that the linked environment isn't in a disabled state. For more information, see [Enable Power Platform integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md). For more information, go to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

#### Configure the Microsoft Entra tenant

Microsoft Entra must be configured so that it can be used with Microsoft Power Platform. Complete the following setup:

1. In the Azure portal, go to the <a href="https://ms.portal.azure.com/#view/Microsoft_Microsoft Entra ID_IAM/LicensesMenuBlade/~/Products">license assignment page</a>. Sign in using the credentials of the tenant administrator.
2. Apply a Dynamics 365 Finance or equivalent license to the user who's installing Business performance analytics. For more information, see [Assign or remove licenses](/azure/active-directory/fundamentals/license-users-groups).

#### Move data from a production environment to a sandbox environment (if needed)

To move data from your production environment to a sandbox environment, follow the instructions in [Data movement](../../fin-ops-core/dev-itpro/database/dbmovement-operations.md). This data is loaded into Business performance analytics and is a prerequisite for the installation of Business performance analytics.

#### Power App users 

Before Business performance analytics can be installed, confirm the users are enabled in Dynamics 365 Finance.

1. In Dynamics 365 Finance, go to **System Administration \> Users**.
2. In filters, add **IsMicrosoftAccount Isexactly true**.
3. Select the **PowerplatformApp** user. 
4. Select **Edit**, and then select **Enabled**.
5. Select **Save**.

#### Required configurations in Dynamics 365 Finance

Before you install Business performance analytics, the following setup is required in Dynamics 365 Finance:

1. Turn on maintenance mode by using Lifecycle Services. Maintenance mode lets you make system changes that might affect system functionality, such as enabling or disabling configuration keys.

    1. Sign in to [Lifecycle Services](https://lcs.dynamics.com/) by using your credentials.
    2. Select the environment where you want to enable maintenance mode.
    3. Select the environment name to open the environment details page.
    4. In the **Maintenance** section, select **Maintain** \> **Enable maintenance mode**.
    5. Confirm that you want to enable maintenance mode. The environment is restarted in maintenance mode.

2. In Dynamics 365 Finance, follow these steps:

    1. Go to **System administration \> License configuration**.
    2. Confirm that **SQL row version change tracking (preview)** is enabled. If it isn't, select the checkbox.
    3. Confirm that the following checkboxes and sub-checkboxes are enabled:

        - **General ledger** – Budget, Reversing entries, Sales tax
        - **Fixed assets**
        - **Bank** – Check, Deposit slip, Negotiable instrument - Bill of exchange
        - **Trade** – Charges, Invoice matching, Return orders, Delivery date control, Warehouse and Transportation management - Material handling equipment interface
        - **Trade agreements** – Price/discount
        - **Project**
        - **Procurement 1** – Purchase requisition
        - **Service management**

3. When you've finished, disable maintenance mode.

#### Required configurations in Power Platform Admin Center

1. Go to <https://admin.powerplatform.microsoft.com/>.
2. Select **Environments**.
3. Select the environment where business performance analytics is installed.
4. In Power Platform Admin Center, **Resources** and select **Dynamics 365 installed apps**.
5. Find **Finance and Operations Virtual Entity** and check if any updates are available.
6. If an update is available, update the application. (Only required if installing Business performance analytics on existing environments).
