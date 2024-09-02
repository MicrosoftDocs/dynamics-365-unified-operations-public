---
title: Install and update Traceability (preview)
description: This article describes how to install and update the various components of the Traceability Add-in for Dynamics 365 Supply Chain Management.
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

This article describes how to install and upgrade the various components of the Traceability Add-in for Dynamics 365 Supply Chain Management.

## Prerequisites

To use Traceability, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management with version 10.0.40 build 10.0.1935.80 or higher

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
1. The **Certificates & secrets** page now includes your new secret. Copy the **Value** and **Secret ID** of the secret and store it in a secure location. You'll need these values later. **IMPORTANT:** the **Value** is only displayed once, so you won't be able to retrieve it again after closing this page.

## Install and configure the Traceability app in Power Apps

The Traceability app is part of the Traceability Add-in for Dynamics 365 Supply Chain Management. It's a Power Apps application that provides a user interface for configuring and using the Traceability Add-in.

To install the Traceability app in Power Apps, complete the following steps in the Power Platform admin center.

1. Find the [*Dynamics 365 Supply Chain Traceability* app in AppSource](https://appsource.microsoft.com/en-US/product/dynamics-365/mscrm.d365-supply-chain-traceability-preview?flightCodes=sctprivatepreview).
1. Select **Get it now**.
1. You're transferred to the Power Platform admin center. Select the environment where you want to install the app, agree to the license terms and privacy statement, and then select **Install** to install the app in your selected environment.

    > [!NOTE]
    > If you don't see your environment listed, you might need to change your geographic region in the Power Platform admin center. Select **Cancel** and then choose a supported region from the region selector in the top right corner of the page. Then try again.

1. The **Dynamics 365 apps** \> **Dynamics 365 Supply Chain Traceability** page opens. Update the following settings:
    - **Select an environment** – Select the environment where you want to set up the app.
    - **Enter application ID of service** – Enter the Application (client) ID that you copied after you registered the Microsoft Entra application.
    - **Enter tenant ID of service** – Enter the Directory (tenant) ID that you copied after you registered the Microsoft Entra application.
    - **I agree to the terms of service** – Select this checkbox.

    > [!NOTE]
    >
    > - If the **Dynamics 365 Supply Chain Traceability** page doesn't open, find the *Dynamics 365 Supply Chain Traceability* app on the **Dynamics 365 apps** page of the Power Platform admin center. Select **More application actions** (the **...** button) for the app and then select **Manage**.
    > - If you don't see the **Enter application ID of service** and/or **Enter tenant ID of service** fields, you should contact the Traceability product team at [d365-Traceability-team@microsoft.com](mailto:d365-Traceability-team@microsoft.com).

1. Select **Install**.
1. When installation is complete, you should be able to see that an app called *Dynamics 365 Supply Chain Traceability* is shown as installed in the list of Dynamics 365 apps for your environment.

## Turn on features in Supply Chain Management

To use Traceability together with Dynamics 365 Supply Chain Management, you must enable one or both of the following features in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

- *Tracked components* – Enables component tracking in Supply Chain Management.
- *(Preview) Traceability* – Integrates Traceability with the component tracking features in Supply Chain Management.

## Update the Supply Chain Traceability application in Power Apps

This section describes how to see when an update of the Supply Chain Traceability application is available and how to apply the update.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. On the left navigation pane, select **Environments**.
1. Open the environment where you want to update the Supply Chain Traceability application.
1. On the left navigation pane, select **Resources** \> **Dynamics 365 apps**.
1. Find the app called *Dynamics 365 Supply Chain Traceability* in the list and its **Status**. If the **Status** is *Installed*, then the app is up to date and you can skip the rest of this procedure. If the **Status**  is *Update available*, continue with this procedure to apply the update.
1. Select the **...** button next to the app name to open a menu and then select **Update**.
1. The **Update Dynamics 365 Supply Chain Traceability** dialog opens. Select **I agree to the terms of service** and then select **Update**.
1. When the update is complete, you should be able to see that the *Dynamics 365 Supply Chain Traceability* app now shows a **Status** of *Installed*.
1. Open the [Power Apps maker portal](https://make.powerapps.com/).
1. On the left navigation pane, select **Solutions**.
1. On the **Solutions** page, select **All**.
1. On the toolbar, select **Publish all customizations**.
