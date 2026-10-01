---
title: Install, update, or uninstall Traceability (preview)
description: This article describes how to install, update, or uninstall the various components of the Traceability Add-in for Dynamics 365 Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 10/01/2026
ms.custom: 
  - bap-template
---

# Install, update, or uninstall Traceability (preview)

[!INCLUDE [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
[!INCLUDE [lcs-freeze-banner](../../../includes/lcs-freeze-banner.md)]
<!-- KFM: Preview until further notice -->

This article describes how to install, update, or uninstall the various components of the Traceability Add-in for Dynamics 365 Supply Chain Management.

## Prerequisites

To use Traceability, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 (build 10.0.1935.80) or higher.
- Your Supply Chain Management installation must be running on one of the following types of environments:
    - Tier-2 environment
    - A Unified Developer Experience (UDE) environment copied from a tier-2 environment that didn't have Traceability installed. Copying an environment with Traceability already installed isn't supported.
- The Dynamics 365 app named *Dynamics 365 Finance and Operations Platform Tools* must be installed for your environment in [Power Platform admin center](https://admin.powerplatform.microsoft.com/).

## Turn on features in Supply Chain Management

To use Traceability together with Dynamics 365 Supply Chain Management, you must enable the following features in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

- *Tracked components* – Enables component tracking in Supply Chain Management. As of Supply Chain Management version 10.0.45, this feature is turned on by default.
- *(Preview) Traceability* – Integrates Traceability with the component tracking features in Supply Chain Management.

## Microsoft Azure configuration

### Register a new Microsoft Entra application

1. Sign in to the [Azure portal](https://ms.portal.azure.com/).
1. Search for or navigate to the **App registrations** page.
1. On the toolbar, select **New registration**.
1. Fill out the **Register and application** page and select **Register**. For more information about these settings, see [Quickstart: Register an application with the Microsoft identity platform](/entra/identity-platform/quickstart-register-app?tabs=certificate).
1. Your new app registration opens. On the left navigation pane, select **Overview**. Copy the **Application (client) ID** value to a temporary text file. You'll need it later when [setting up communication with the API](traceability-api.md).

## Install and configure the Traceability app in Power Apps

The Traceability app is part of the Traceability Add-in for Dynamics 365 Supply Chain Management. It's a Power Apps application that provides a user interface for configuring and using the Traceability Add-in. When you install the Traceability app in Power Apps, the system also installs the necessary add-in components in Supply Chain Management.

To install the Traceability app in Power Apps, complete the following steps.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the left navigation pane, select **Resources** > **Dynamics 365 apps**.
1. Find the *Dynamics 365 Supply Chain Traceability* app on the **Dynamics 365 apps** page. Select **More application actions** (the **...** button) for the app and then select **Manage**.
1. The **Install Dynamics 365 Supply Chain Traceability** dialog opens. Make the following settings:
    - **Select an environment** – Select the environment where you want to set up the app.
    - **I agree to the terms of service** – Select this checkbox.

1. Select **Install**.
1. When installation is complete, you should see that an app called *Dynamics 365 Supply Chain Traceability* is shown with a status of *Installed* in the list of **Dynamics 365 apps** for your environment.
1. On the left navigation pane, select **Environments**.
1. Open the environment where you installed the Traceability app.
1. On the **Generative AI features** tile, check to make sure that **Move data across regions** is set to *Allowed*. If it isn't, then follow these steps to allow it:
    - Select the **Edit** link on the **Generative AI features** tile.
    - In the **Generative AI features** dialog, select the **Move data across regions** checkbox
    - Select **Save** to close the dialog.

## Update the Traceability app in Power Apps

This section describes how to check for updates to the Traceability app and how to apply them.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. On the left navigation pane, select **Environments**.
1. Open the environment where you want to update the Traceability app.
1. From the **Resources** tile, select **Dynamics 365 apps**.
1. Find the app called *Dynamics 365 Supply Chain Traceability* in the list and check its **Status**. If the **Status** is *Installed*, then the app is up to date and you can skip the rest of this procedure. If the **Status** is *Update available*, continue with this procedure to apply the update.
1. Select **More application actions** (the **...** button) next to the app name to open a menu, then select **Update**.
1. The **Update Dynamics 365 Supply Chain Traceability** dialog opens. Select **I agree to the terms of service** and then select **Update**.
1. When the update is complete, you should see that the *Dynamics 365 Supply Chain Traceability* app now shows a **Status** of *Installed*.
1. Open the [Power Apps maker portal](https://make.powerapps.com/).
1. On the left navigation pane, select **Solutions**.
1. On the **Solutions** page, select **All**.
1. On the toolbar, select **Publish all customizations**.

## Uninstall the Traceability Add-in from Supply Chain Management

The Traceability Add-in is automatically installed on your Supply Chain Management environment when you install the Traceability app in Power Apps. However, to uninstall the add-in, you must use Microsoft Dynamics Lifecycle Services by following these steps:

1. Sign in to [Lifecycle Services](https://lcs.dynamics.com/).
1. Open the page for managing your Supply Chain Management environment.
1. In the **Environment add-ins** section, on the **Traceability service** tile, select **Uninstall**.

## Uninstall the Traceability app from Power Apps

To remove the Traceability app from your Power Apps environment, complete the following steps:

1. Sign in to [Power Platform maker](https://make.powerapps.com/).
1. On the left navigation pane, select **Solutions**.
1. The **Solutions** page opens. Open the **Managed** tab.
1. Find and delete each of the following solutions. To delete a solution, select the **Commands** button next to its name and then select **Delete**.
    - *Dynamics 365 Supply Chain Traceability anchor solution*
    - *Dynamics 365 Supply Chain Traceability portal solution*
    - *Dynamics 365 Supply Chain Traceability controls solution*
    - *Dynamics 365 Supply Chain Traceability Plugins solution*
    - *Supply chain traceability integration - authorization*
    - *Dynamics 365 Supply Chain Traceability common solution*

    > [!IMPORTANT]
    > You must delete *Dynamics 365 Supply Chain Traceability common solution* last.
