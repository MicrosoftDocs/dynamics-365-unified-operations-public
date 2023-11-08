---
# required metadata

title: Copilot in Finance and Operations
description: This article describes the functionality and configuration of Copilot for Finance and Operations
author: jaredha
ms.date: 11/6/2023
ms.topic: article
ms.prod: 
ms.technology: finance and operations

# optional metadata

# ms.search.form:
audience: Developer, IT Pro, Administrator
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
# ms.custom: bap-template
ms.search.region: Global
# ms.search.industry:
ms.author: jaredha
ms.search.validFrom: 11/01/2023
ms.dyn365.ops.version: 10.0.35 PU59
---

# Copilot in Finance and Operations (preview)

[!include[banner](../includes/banner.md)]
[!INCLUDE[banner](../includes/preview-banner.md)]

> [!IMPORTANT]
> This feature requires version 10.0.38 or greater of finance and operations apps.

Copilot in Finance and Operations provides users of finance and operations apps with access to AI capabilities augmenting the application experiences and functionality. Copilot experiences for finance and operations apps can be: 

1. **Embedded**: These are built into the application as intelligent capabilities on the form, bringing AI to the center of the applicatino experience. For example, the [Confirmed purchase orders with changes](../../../supply-chain/procurement/purchase-order-changes-after-confirmation#the-confirmed-purchase-orders-with-changes-workspace) workspace has AI capabilities built into the page to assist in understanding and reacting to changes in confirmed purchase orders.
2. **Outside**: Agents help orchestrate across apps and tasks. For example, users can ask questions about finance and operations data in Microsoft 365 Copilot. See [FAQ for finance and operations data on Microsoft 365 Copilot (Preview)](./faq-for-chat-with-fno-data-on-m365copilot) for more information.
3. **Beside**: The Copilot sits alongside the application as a helper for the user experience. 

This documentation topic focuses on the **Copilot in Finance and Operations sidecar chat** panel, which is the primary Copilot interface in finance and operations apps, falling in the "beside" category living alongside the user in the application. This provides a natural language chat experience throughout finance and operations apps as a helper with the applicatin functionality and data. 

Currently, the sidecar chat enables users to ask questions and receive generative help and guidance about application functionality. See [Add a link here](https://link) for more information. But Copilot is learning and will continue to expand in capabilities with the types of questions and guidance the user can receive.

## Setup and configuration
This section describes the steps required to configure the Copilot for Finance and Operations sidecar chat in your finance and operations apps.

### Step 1: Enable the Power Platform Integration
Ensure you have configured the [Power Platform Integration](../power-platform/overview.md) for your environment. See [Enable Power Platform Integration](../power-platform/enable-power-platform-integration.md) for more information and detailed steps for configuring the Power Platform Integration in your environment. 

> [!NOTE]
> The Power Platform Integration is required for cross-platform integrations and features such as [Dual-write](../data-entities/dual-write/dual-write-overview.md), [Virtual entities for finance and operations apps](../power-platform/virtual-entities-overview.md), Copilot for Finance and Operations, and other existing and upcoming features. Even if you are not using these features today it is strongly recommended that you enable the Power Platform Integration. In a coming release the Power Platform Integration will be mandatory in all finance and operations environments.

### Step 2: Enable finance and operations apps access to your Dataverse environment
With the Power Platform Integration enabled, the administrator for the linked Dataverse environment must provide consent for users in finance and operations apps to make Dataverse requests with the permissions assigned to that user in Dataverse.

1. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
2. Select the Power Platform environment that is connected to your finance and operations environment through the Power Platform Integration, and open the detail view.
3. Select the **Settings** menu on the menu bar.
4. Go to **Products > Features**.
5. In the **Finance and Operations in Dataverse** section, set the **Enable Finance and Operations User Impersonation in Dataverse** option to **On**.

### <a name="enable-change-tracking"></a>Step 3: Enable row version change tracking
[Row version change tracking](../data-entities/rowversion-change-track.md) is required to install the Copilot application, and will be mandatory in all finance and operations environments in a coming release. If you haven't enabled the configuration key you will get an error when installing the Copilot application in the next step.

1. In finance and operations apps, go to **System administration > Setup > License configuration**.
2. On the **Configuration keys** tab, scroll down to the **Sql row version change tracking** key. If the key is already enabled, then skip the rest of this procedure. If it isn't enabled, then continue to the next step.
3. Put your system into maintenance mode, as described in [Maintenance mode](./sysadmin/maintenance-mode).
4. Return to the **License configuration** page and enable the **Sql row version change tracking** key.
5. Turn off maintenance mode, as described in [Maintenance mode](./sysadmin/maintenance-mode).

### Step 4: Install the Copilot application
The **Copilot in Finance and Operations** solution must be installed in the linked Power Platform environment. The solution is included in the Copilot deployment packages for each of the finance and operations apps that have built Copilot capabilities. In the initial release this includes only the Dynamics 365 Supply Chain Management package, but will soon expand to include all finance and operations apps.

1. Go to the [Copilot in Microsoft Dynamics 365 Supply Chain Management](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamicsscmai-preview?flightCodes=f42a7338c806438f8fca820c4ed82b7c&tab=Overview) page in the Microsoft commercial marketplace.
2. Select **Get it now**.
3. The deployment process opens [Power Platform admin center](https://admin.powerplatform.microsoft.com). Select the Power Platform environment that's connected to your finance and operations environment to install the solution.

> [!NOTE]
> If during the installation you experience an error indicating SQL row version change tracking is required for an entity, follow the steps to enable row version change tracking here: [Step 3: Enable row version change tracking](#enable-change-tracking).
>
> If you have previously installed Copilot in Microsoft Dynamics 365 Supply Chain Management package, then you will only need to update the app, which you can do from the detail view of the Power Platform environment. On the **Resources** menu, select **Dynamics 365 apps**. Select the **Update available** link for the **Copilot in Microsoft Dynamics 365 Supply Chain Management** app, and select **Update**.

### Step 5: Enable the required security roles
Users who should have access to the functionality must be assigned to the **AIB Roles** and **Finance and Operations AI** security roles in Dataverse. 

1. In the detail view of the environment, in the **Access** section, select **Users** if you want to assign access by user or **Teams** if you want to assign access by team.
2. Select the user or team that should have access.
3. Select **Manage security roles** on the action ribbon.
4. Assign the **AIB Roles** and **Finance and Operations AI** security roles, and select **Save**.

### Step 6: Enable the Copilot feature in Feature management
In the **[Feature management](../fin-ops/get-started/feature-management/feature-management-overview)** workspace, turn on the **(Preview) User experience for Copilot in Finance and Operations** feature.
