---
title: Onboard the Approvals Management mobile app (preview)
description: This article explains how administrators can prepare Microsoft Dynamics 365 Supply Chain Management and Dataverse environments to support the Approvals Management mobile app. It also explains how to install the app on mobile devices.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Onboard the Approvals Management mobile app (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how administrators can prepare your Microsoft Dynamics 365 Supply Chain Management and Dataverse environments to support the Approvals Management mobile app. It also explains how to install the app on your mobile devices.

## Prerequisites

Before you can start to onboard the Approvals Management mobile app, you must meet the requirements that are outlined in this section.

### System requirements

To run the Approvals Management mobile app, you must be using Supply Chain Management version 10.0.41 or later.

### Region requirements

The Approvals Management mobile app is available in all regions where Supply Chain Management and Power Apps are supported. However, it isn't available for Microsoft Cloud for Sovereignty.

### Set up Dataverse for your Supply Chain Management environment

The Approvals Management mobile app uses [Dataverse virtual tables that are connected to Supply Chain Management](../../../fin-ops-core/dev-itpro/power-platform/virtual-entities-overview.md). Therefore, a Dataverse environment must be integrated with your Supply Chain Management environment. If Dataverse isn't already set up for your environment, follow the instructions in [Microsoft Power Platform integration with finance and operations apps](../../../fin-ops-core/dev-itpro/power-platform/overview.md).

When you create the Dataverse environment where you want to install the app, be sure to enable Dynamics 365 apps.

The [Power Apps component framework feature](/power-apps/developer/component-framework/component-framework-for-canvas-apps#enable-the-power-apps-component-framework-feature) must be enabled for your environment.

### Allow publishing of canvas apps in Dataverse

The Approvals Management mobile app is a canvas app. Therefore, before you can install it in Dataverse, you must enable the **Allow publishing of canvas apps with code components** option for your environment.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the navigation pane, select **Environments**, and then select the environment that is integrated with Supply Chain Management.
1. On the toolbar, select **Settings**.
1. On the **Settings** page, expand the **Product** section, and select **Features**.
1. Set the **Allow publishing of canvas apps with code components** option to *On*.

## <a name="install-in-dataverse"></a>Install the mobile app in Dataverse

You must install the Approvals Management mobile app in your Dataverse environment to enable users to access it when they sign in by using the Power Apps mobile app. The installation process also sets up the required user roles and other dependencies in Dataverse.

Follow these steps to install the Approvals Management mobile app in Dataverse.

1. Go to the [Dynamics 365 Approvals Management](https://appsource.microsoft.com/en-us/product/dynamics-365/mscrm.d365-approvalsmanagementapp-preview?flightCodes=9e074b1814ff4c7889a84758ecdbbd16) page on AppSource.
1. Select **Get it now**.
1. Follow the on-screen instructions to install the app in the Dataverse environment that is connected to your target Supply Chain Management environment.

## Grant access to the mobile app in Dataverse

After the mobile app solution is installed in your Dataverse environment, you must share it with your users. The Approvals Management mobile app is a canvas app. To share it, follow the instructions in [Share an app](/power-apps/maker/canvas-apps/share-app#share-an-app).

Each relevant user must also have the *Finance and Operations Basic User* role.

- To assign a role to a group team, follow the instructions in [Manage the security roles of a team](/power-platform/admin/manage-group-teams#manage-the-security-roles-of-a-team). We recommend that you use group teams if you must assign the role to multiple users. Learn more about how to manage team members in [Manage team members](/power-platform/admin/manage-teams#manage-team-members).
- To assign a role directly to a user, follow the instructions in [Assign a security role to a user](/power-platform/admin/assign-security-roles).

## <a name="roles-approvals"></a>Set up user accounts to manage approvals in Supply Chain Management

Each Supply Chain Management user who should be able to use the Approvals Management mobile app must have one or all of the following standard security roles:

- *Buying agent* – This role allows a Supply Chain Management user account to use the app to manage purchase orders.
- *Purchasing agent* – This role allows a Supply Chain Management user account to use the app to manage purchase requisitions.
- *Purchasing manager* – This role allows a Supply Chain Management user account to use the app to manage both purchase orders and purchase requisitions.

Users who have the *System administrator* role can use the app to manage all types of approval requests.

Follow these steps to add the required security roles to a Supply Chain Management user.

1. Sign in to your Supply Chain Management environment by using an administrator account.
1. Go to **System administration** \> **Users** \> **Users**.
1. Use the filter to find a user who should be able to use the app.
1. Open the details page for the selected user by selecting the link in the **User ID** column.
1. On the **User's roles** FastTab, on the toolbar, select **Assign roles** to open the **Assign roles to user** dialog box.
1. In the **Role name** column, find and select the *Buying agent*, *Purchasing agent* and/or *Purchasing manager* roles, as needed.
1. Select **OK** to apply your settings and close the dialog box.

> [!NOTE]
> User role organization assignments aren't supported. If one or more organizations that differ from a selected user's [default company](../../../fin-ops-core/fin-ops/get-started/personalize-user-experience.md#system-wide-options-for-the-current-user) have been assigned to any security role that is set for that user, app installation fails.

Learn more about how to set up roles and security in Supply Chain Management in [Security roles](../../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md#security-roles).

## Set up approval workflows

To enable the approval process for a document type, you must set up approval workflows for it in Supply Chain Management. Learn more in [Workflow system overview](../../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md).

After your approval workflows are set up, approval requests appear in the Approvals Management mobile app just as they do when the same user signs in to Supply Chain Management to manage approvals in the web client.

## Install and open the mobile app

Follow these steps to install and use the Approvals Management mobile app on a mobile device.

1. Install the Power Apps mobile app by following the instructions in [Install the Power Apps mobile app](/power-apps/mobile/run-powerapps-on-mobile).
1. Open the Power Apps mobile app, and sign in by using the same corporate account that you use to sign in to Supply Chain Management.
1. Use the **Search** field to search for *Approvals Management*. Because the Approvals Management mobile app is a canvas app, you can add it to your favorites list in Power Apps by swiping left on it after you find it.
1. Open the Approvals Management mobile app, and start to use it.

## Clear the Power Apps cache on a mobile device after an update of the back-end setup

If the back-end setup is updated in Supply Chain Management after you install the Power Apps mobile app on a mobile device (for example, if the legal entity setup is changed), you might have to clear the cache in Power Apps to update the local setup data. Power Apps can then reload the settings that otherwise might not take effect until the cache is cleared.

Follow these steps to clear the Power Apps cache on a mobile device.

1. Sign in to the Power Apps mobile app.
1. Select the image for your user account in the upper left of the page to open the settings menu.
1. Select **Clear cache** to open the **Clear cache** dialog box.
1. Select **Confirm**.
