---
title: Onboard the Asset Management mobile app
description: This article describes how administrators can prepare your Microsoft Dynamics 365 Supply Chain Management and Dataverse environments to support the Asset Management mobile app, and how to install the app on your mobile devices.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 03/17/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Onboard the Asset Management mobile app

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]
<!-- KFM: Preview until further notice. Note that app install procedure may change after GA -->

This article describes how administrators can prepare your Microsoft Dynamics 365 Supply Chain Management and Dataverse environments to support the Asset Management mobile app. It also describes how to install the app on your mobile devices.

## Prerequisites

Before you can start to onboard the Asset Management mobile app, you must meet the requirements that are outlined in this section.

### System requirements

To run the Asset Management mobile app, you must be using Supply Chain Management version 10.0.32 or later.

### Set up Dataverse for your Supply Chain Management environment

The mobile app uses [Dataverse virtual tables that are connected to Supply Chain Management](../../../fin-ops-core/dev-itpro/power-platform/virtual-entities-overview.md). Therefore, a Dataverse environment must be integrated with your Supply Chain Management environment. If Dataverse isn't already set up for your environment, follow the instructions in [Microsoft Power Platform integration with finance and operations apps](../../../fin-ops-core/dev-itpro/power-platform/overview.md).

When you create the Dataverse environment where you want to install the app, be sure to enable Dynamics 365 apps.

### Configure dual-write in Supply Chain Management

For the mobile app to work, Power Apps must be able to communicate with your Supply Chain Management environment through virtual entities. To enable virtual entities in your Dataverse environment, follow the instructions in [Getting the virtual entity solution](../../../fin-ops-core/dev-itpro/power-platform/admin-reference.md#get-virtual-entity-solution).

> [!IMPORTANT]
> If dual-write and virtual entities were already set up on your Dataverse environment for a previous purpose, you must still update your virtual entity solution before you install the Asset Management mobile app in Dataverse. If you install the app over an outdated virtual entity solution, you risk needing to manually update the schema for each virtual entity afterwards. For more information about how to manually install and update the virtual entity solution, see [Manage Dynamics 365 apps](/power-platform/admin/manage-apps).

## <a name="install-in-dataverse"></a>Install the mobile app in Dataverse

You must install the Asset Management mobile app in your Dataverse environment to enable users to access it when they sign in by using the Power Apps mobile app. The installation process also sets up the required user roles and other dependencies in Dataverse.

Follow these steps to install the Asset Management mobile app in Dataverse.

1. Go to ["Dynamics 365 Asset Management Mobile Application (Public Preview)" in Microsoft AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.d365-scm-assetmanagementmobileapp).
1. Select **Get it now**.
1. Follow the instructions on your screen to install the app in the Dataverse environment that is connected to your target Supply Chain Management environment.

## Grant access to the mobile app in Dataverse

After the mobile app solution is installed in your Dataverse environment, you must share it with your users. The Asset Management mobile app is a canvas app. To share it, follow the instructions in [Share an app](/power-apps/maker/canvas-apps/share-app#share-an-app).

Each relevant user must be assigned a role that lets them work with the Dataverse Supply Chain Management virtual tables that the solution installs. The solution installs a role named *Asset Management Mobile Application User Role* that grants access privileges to all the required virtual tables. You can assign this role to a Dataverse group team. Any user who's a member of that team will then have the role too. Alternatively, you can assign the role directly to a user.

- To assign a role to a group team, follow the instructions in [Manage the security roles of a team](/power-platform/admin/manage-group-teams#manage-the-security-roles-of-a-team). We recommend that you use group teams if you must assign the role to multiple users. For information about how to manage team members, see [Manage team members](/power-platform/admin/manage-teams#manage-team-members).
- To assign a role directly to a user, follow the instructions in [Assign a security role to a user](/power-platform/admin/assign-security-roles).

## <a name="roles-workers"></a>Configure users and workers in Supply Chain Management

Each user who will use the Asset Management mobile app must be set up as described in this section.

### Set up user accounts to maintain assets and/or request maintenance

Each Supply Chain Management user who should be able to operate the Asset Management mobile app must have one or both of the following standard security roles:

- *Maintenance requester* – This role allows a Supply Chain Management user account to use the app to create maintenance requests.
- *Maintenance worker* – This role allows a Supply Chain Management user account to use the app to manage maintenance work orders.

Users who have the *System administrator* role can use the app both to create maintenance requests and to manage work orders.

Follow these steps to add the required security roles to a Supply Chain Management user and review that user's **Person** setting.

1. Sign in to your Supply Chain Management environment by using an administrator account.
1. Go to **System administration \> Users \> Users**.
1. Use the filter to find a user who should be able to use the app.
1. Open the details page for the selected user by selecting the hyperlink in the **User ID** column.
1. Review the value of the **Person** field to determine which person is assigned to the current user account. If a person is assigned, write down their name. If no person is assigned, you'll assign one in the next section.
1. On the **User's roles** FastTab, on the toolbar, select **Assign roles** to open the **Assign roles to user** dialog box.
1. In the **Role name** column, find and select the *Maintenance requester* and *Maintenance worker* roles.
1. Select **OK** to apply your settings and close the dialog box.

> [!NOTE]
> User role organization assignments aren't supported. If one or more organizations that differ from a selected user's [default company](../../../fin-ops-core/fin-ops/get-started/personalize-user-experience.md#system-wide-options-for-the-current-user) have been assigned to any security role that's set for that user, app installation will fail.

For more information about how to set up roles and security in Supply Chain Management, see
[Security roles](../../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md#security-roles).

### Set up a maintenance worker for each user

Follow these steps to confirm or create a maintenance worker for a selected user account.

1. Go to **Asset Management \> Setup \> Workers \> Workers**.
1. Follow one of these steps, depending on whether a person was assigned to the user account that you set up in the previous section:

    - If a person was assigned, confirm that the same person is listed here as a maintenance worker. If they aren't, set up a maintenance worker for that person now. If you must set up a worker, follow the instructions in [Maintenance workers and worker groups](../setup-for-objects/workers-and-worker-groups.md).
    - If no person was assigned, either select a maintenance worker in the list here, or add the person that you want to use as a maintenance worker by following the instructions in [Maintenance workers and worker groups](../setup-for-objects/workers-and-worker-groups.md). Then go back to **System administration \> Users \> Users**, and open the user account that you're setting up. In the **Person** field, assign the maintenance worker that you just selected or added.

> [!CAUTION]
> The **Person** setting for user accounts is permanent. You won't be able to edit it after you save your changes. Therefore, make sure that you select the correct person when you set up the user account.

## Install and open the Asset Management mobile app

Follow these steps to install and use the Asset Management mobile app on a mobile device.

1. Install the Power Apps mobile app by following the instructions in [Install the Power Apps mobile app](/power-apps/mobile/run-powerapps-on-mobile).
1. Open the Power Apps mobile app, and sign in by using the same corporate account that you use to sign in to Supply Chain Management.
1. Use the **Search** field to search for *Asset Management*. Because it's a canvas app, you can add it to your favorites list in Power Apps by swiping left on it after you find it.
1. Open the Asset Management mobile app, and start to use it.

## Clear the Power Apps cache on a mobile device after an update of the back-end setup

If the back-end setup is updated in Supply Chain Management after you install the Power Apps mobile app on a mobile device (for example, if the legal entity setup is changed), you might have to clear the cache in Power Apps to update the local setup data. Power Apps will then be able to reload the settings that otherwise might not take effect until the cache is cleared.

Follow these steps to clear the Power Apps cache on a mobile device.

1. Sign in to the Power Apps mobile app.
1. Select the image for your user account in the upper left of the page to open the settings menu.
1. Select **Clear cache** to open the **Clear cache** dialog box.
1. Select **Confirm**.
