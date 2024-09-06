---
title: Install, update, or uninstall Traceability (preview)
description: This article describes how to install, update, or uninstall the various components of the Traceability Add-in for Dynamics 365 Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Install, update, or uninstall Traceability (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article describes how to Install, update, or uninstall the various components of the Traceability Add-in for Dynamics 365 Supply Chain Management.

## Prerequisites

To use Traceability, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 (build 10.0.1935.80) or higher.

## Turn on features in Supply Chain Management

To use Traceability together with Dynamics 365 Supply Chain Management, you must enable one or both of the following features in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

- *Tracked components* – Enables component tracking in Supply Chain Management.
- *(Preview) Traceability* – Integrates Traceability with the component tracking features in Supply Chain Management.

## Microsoft Azure configuration

### Register a new Microsoft Entra application

1. Sign in to the [Azure portal](https://ms.portal.azure.com/).
1. Search for or navigate to the **App registrations** page.
1. On the toolbar, select **New registration**.
1. Fill out the **Register and application** page and select **Register**. For more information about these settings, see [Quickstart: Register an application with the Microsoft identity platform](/entra/identity-platform/quickstart-register-app?tabs=certificate).
1. Your new app registration opens. On the left navigation pane, select **Overview**. Copy the following values to a temporary text file. You'll need them later.
    - **Application (client) ID**
    - **Directory (tenant) ID**

### Create client secrets for the new Microsoft Entra application

1. In the [Azure portal](https://ms.portal.azure.com/), open the application you registered in the previous section.
1. In the left navigation pane, select **Manage** \> **Certificates & secrets**.
1. On the **Certificates & secrets** page, select **New client secret**.
1. In the **Add a client secret** dialog, enter a description and choose an expiration date for the secret. Then select **Add**.
1. The **Certificates & secrets** page now includes your new secret. Copy the **Value** and **Secret ID** of the secret and store it in a secure location. You'll need these values later. 

    > [!IMPORTANT]
    > The **Value** is only displayed once, so you won't be able to retrieve it again after closing this page.

## Install and configure the Traceability app in Power Apps

The Traceability app is part of the Traceability Add-in for Dynamics 365 Supply Chain Management. It's a Power Apps application that provides a user interface for configuring and using the Traceability Add-in.

To install the Traceability app in Power Apps, complete the following steps.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the left navigation pane, select **Resources** \> **Dynamics 365 apps**. <!--KFM: ... or should I open the environment first? -->
1. Find the *Dynamics 365 Supply Chain Traceability* app on the **Dynamics 365 apps** page. Select **More application actions** (the **...** button) for the app and then select **Manage**. <!--KFM: Please confirm this step and labels. -->
1. The **Install Dynamics 365 Supply Chain Traceability** dialog opens. Make the following settings:
    - **Select an environment** – Select the environment where you want to set up the app.
    - **Enter application ID of service** – Enter the Application (client) ID that you copied after you registered the Microsoft Entra application.
    - **Enter tenant ID of service** – Enter the Directory (tenant) ID that you copied after you registered the Microsoft Entra application.
    - **I agree to the terms of service** – Select this checkbox.

    > [!NOTE]
    > If you don't see the **Enter application ID of service** and/or **Enter tenant ID of service** fields, you should contact the Traceability product team at [d365-Traceability-team@microsoft.com](mailto:d365-Traceability-team@microsoft.com).

1. Select **Install**.
1. When installation is complete, you should see that an app called *Dynamics 365 Supply Chain Traceability* is shown with a status of *Installed* in the list of **Dynamics 365 apps** for your environment.
1. Configure Generative AI features -> Move data across regions to “Allowed” to allow copilot summary. <!--KFM: This is too vague; more steps are probably needed. We should tell readers readers how to find this setting. -->

## Update the Traceability app in Power Apps

This section describes how to see when an update of the Supply Chain Traceability application is available and how to apply the update.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. On the left navigation pane, select **Environments**.
1. Open the environment where you want to update the Supply Chain Traceability application.
1. From the **Resources** tile, select **Dynamics 365 apps**.
1. Find the app called *Dynamics 365 Supply Chain Traceability* in the list and note its **Status**. If the **Status** is *Installed*, then the app is up to date and you can skip the rest of this procedure. If the **Status**  is *Update available*, continue with this procedure to apply the update.
1. Select **More application actions** (the **...** button) next to the app name to open a menu and then select **Update**.
1. The **Update Dynamics 365 Supply Chain Traceability** dialog opens. Select **I agree to the terms of service** and then select **Update**.
1. When the update is complete, you should be able to see that the *Dynamics 365 Supply Chain Traceability* app now shows a **Status** of *Installed*.
1. Open the [Power Apps maker portal](https://make.powerapps.com/).
1. On the left navigation pane, select **Solutions**.
1. On the **Solutions** page, select **All**.
1. On the toolbar, select **Publish all customizations**.

## Uninstall the Supply Chain Traceability application from Supply Chain Management

<!--KFM: I think we mean the add-in (not the app) but I'm not sure. Can we have an "app" in SCM? We didn't install anything in LCS until now, so how did this get installed here? What are we doing when we uninstall from here? How would we install this again later? -->

1. Go to LCS of Dynamics 365 Supply Chain Management. <!--KFM: How do we get here? What do we do next? -->
2. Find installed Traceability Service (Preview) and select **Uninstall**. <!--KFM: How can I find this? -->

## Uninstall the Traceability app from Power Apps

1. Sign in to [Power Platform maker](https://make.powerapps.com/).
1. On the left navigation pane, select **Solutions**.
1. The **Solutions** page opens. Open the **Managed** tab
1. Find and delete each of the following solutions. To delete a solution, select the **Commands** button next to its name and then select **Delete**.
    - *Dynamics 365 Supply Chain Traceability anchor solution*
    - *Dynamics 365 Supply Chain Traceability portal solution*
    - *Dynamics 365 Supply Chain Traceability controls solution*
    - *Dynamics 365 Supply Chain Traceability Plugins solution*
    - *Supply chain traceability integration - authorization*
    - *Dynamics 365 Supply Chain Traceability common solution*

    > [!IMPORTANT]
    > You must delete *Dynamics 365 Supply Chain Traceability common solution* last.
