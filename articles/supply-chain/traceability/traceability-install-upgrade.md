---
title: Install and update Traceability (preview)
description: This article describes how to install and update the various components of the Traceability add-in for Dynamics 365 Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Install and update Traceability (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article describes how to install and upgrade the various components of the Traceability add-in for Dynamics 365 Supply Chain Management.

## Prerequisites

To use Traceability, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.39 or later.
- If you also want to integrate Traceability with the production floor execution interface, you must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 or later.

## Microsoft Azure configuration

<!-- KFM: Do we only need to do this if we will use third-party integration and API? Maybe this isn't needed if we only want to integrate with SCM? -->

### Register a new Microsoft Entra application

1. Sign in to [Azure portal](https://ms.portal.azure.com/).
1. Search for or navigate to the **App registrations** page.
1. On the toolbar, select **New registration**.
1. Fill out the **Register and application** page and select **Register**. For more information about these settings, see [Quickstart: Register an application with the Microsoft identity platform](/entra/identity-platform/quickstart-register-app?tabs=certificate).
1. You new app registration opens. On the left navigation pane, select **Overview**. Copy the following values to a temporary text file. You'll need them later.
    - **Application (client) ID**
    - **Directory (tenant) ID**

### Create client secrets for the new Microsoft Entra application

1. In [Azure portal](https://ms.portal.azure.com/), open the application you just registered in the previous section.
1. In the left navigation pane, select **Manage** \> **Certificates & secrets**.
1. On the **Certificates & secrets** page, select **New client secret**.
1. In the **Add a client secret** dialog, enter a description and choose an expiration date for the secret. Then select **Add**.
1. The **Certificates & secrets** page now includes your new secret. Copy the **Value** and **Secret ID** of the secret and store it in a secure location. You'll need these values later. **IMPORTANT:** the **Value** is only displayed once, so you won't be able to retrieve it again after closing this page.

## Install and configure the Traceability application in Power Apps

Apply the following steps in Power Platform Admin Center to install the Traceability application in Power Apps.

1. Find the [*Dynamics 365 Supply Chain Traceability* app in AppSource](https://appsource.microsoft.com/en-US/product/dynamics-365/mscrm.d365-supply-chain-traceability-preview?flightCodes=sctprivatepreview). <!--KFM: Will this app be renamed before release? -->
1. Select **Get it now**.
1. You are transferred to the Power Platform admin center. Select the environment where you want to install the solution, agree to the license terms and privacy statement, and then select **Install** to install the app in your selected environment. <!--KFM: There was some info here about selecting a region, but it was confusing and seems like a special case, so I removed it. The UI provides a help link about it anyway. Please advise if we need to put this info back here. -->
1. The **Dynamics 365 apps** \> **Dynamics 365 Supply Chain Traceability** page opens. Make the following settings: <!--KFM: This is how it worked for me, but it's different from what the original guide described. The guide described finding the not-configured app in a list and selecting **Manage**.  -->
    - **Select an environment** – Select the environment where you want to set up the app.
    - **Enter application ID of service** – Enter the Application (client) ID that you copied after you registered the Microsoft Entra application.
    - **Enter tenant ID of service** – Enter the Directory (tenant) ID that you copied after you registered the Microsoft Entra application.
    - **I agree to the terms of service** – Select this check box.

    <!--KFM: Original draft included the following. Do we really want this?   **Note: If there is no entry for application id and tenant id, please contact the product team.** --->

1. Select **Install**.
1. When installation is complete, you should be able to see that an app called *Dynamics 365 Supply Chain Traceability* is shown as installed in the list of Dynamics 365 apps for your environment. <!--KFM: Will this app be renamed before release? -->

## Assign security roles to users in Power Apps

<!--KFM: First draft says this is for private preview. Do we need to update or remove this?-->

The Traceability app adds a security role called *Traceability service role* to your Power Platform environment. Use this role to grant access to the Traceability app.

Use the [Power Platform admin center](https://admin.powerplatform.microsoft.com) to grant Traceability permissions to the following types of users:

- **Administrator users** – Assign the default *Traceability service role*, as provided, to users who need to configure the Traceability app.
- **Business users** – Create a copy of the *Traceability service role* and rename the copy (for example, to *Traceability business role*). Edit the copy to remove access to the table *Environment Configuration*. Assign the copied role to business users who need to use the Traceability app. You must also assign the *Finance and Operations Basic User* role to each of these users.

For more information about how to complete these steps, see [Assign a security role to a user](/power-platform/admin/assign-security-roles), [Save time creating a security role by copying one](/power-platform/admin/copy-security-role), and [Create or edit a security role to manage access](/power-platform/admin/create-edit-security-role).

## Turn on features in Supply Chain Management

To use Traceability together with Dynamics 365 Supply Chain Management, you must enable one or both of the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

- *(Preview) Supply Chain Traceability* – <!--KFM: What does this give us if we don't turn on the next one? -->
- *Tracked components* – Integrates Traceability with the [production floor execution interface](../production-control/production-floor-execution-use.md))

## Update the Supply Chain Traceability application in Power Apps

This section describes how to see when an update of the Supply Chain Traceability application is available and how to apply the update.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. On the left navigation pane, select **Environments**.
1. Open the environment where you want to update the Supply Chain Traceability application.
1. On the left navigation pane, select **Resources** \> **Dynamics 365 apps**.
1. Find the app called *Dynamics 365 Supply Chain Traceability* in the list and its **Status**. If the **Status** is *Installed*, then the app is up to date and you can skip the rest of this procedure. If the **Status**  is *Update available*, continue with this procedure to apply the update.
1. Select the **...** button next to the app name to open a menu and then select **Update**.
1. The **Update Dynamics 365 Supply Chain Traceability** dialog opens. Select **I agree to the terms of service** and then select **Update**.
1. When update is complete, you should be able to see that the *Dynamics 365 Supply Chain Traceability* app now shows a **Status** of *Installed*.
1. Open the [Power Apps maker portal](https://make.powerapps.com/).
1. On the left navigation pane, select **Solutions**.
1. On the **Solutions** page, select **All**.
1. On the toolbar, select **Publish all customizations**.
