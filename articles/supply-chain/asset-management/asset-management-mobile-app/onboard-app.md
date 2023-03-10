---
title: Onboard the Asset Management mobile app
description: This article describes how administrators can prepare your Supply Chain Management and Dataverse environments to support the Asset Management mobile app and how to install the app on your mobile devices.
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

This article describes how administrators can prepare your Supply Chain Management and Dataverse environments to support the Asset Management mobile app and how to install the app on your mobile devices.

## Prerequisites

Before you can start to onboard the Asset Management mobile app, you must meet the requirements outlined in this section.

### System requirements

To run the Asset Management mobile app, you must be using Supply Chain Management version 10.0.32 version or higher.

### Set up Dataverse for your Supply Chain Management environment

The mobile application uses [Dataverse virtual tables connected to Supply Chain Management](../../../fin-ops-core/dev-itpro/power-platform/virtual-entities-overview.md). Therefore, a Dataverse environment must be integrated with your Supply Chain Management environment. If you don't already have Dataverse set up for your environment, follow the instructions given in [Microsoft Power Platform integration with finance and operations apps](../../../fin-ops-core/dev-itpro/power-platform/overview.md).

When creating the Dataverse environment where you want to install the app, be sure to enable Dynamics 365 apps.

### Configure dual-write in Supply Chain Management

For the mobile app to work, Power Apps must be able to communicate with your Supply Chain Management environment through virtual entities. To enable virtual entities in your Dataverse environment, follow the instructions given in [Configure Dataverse virtual entities](/dynamics365/fin-ops-core/dev-itpro/power-platform/admin-reference#get-virtual-entity-solution).

## Install the mobile application in Dataverse

You must install the Asset Management mobile app into your Dataverse environment to make it possible for users to access it when they sign in using the Power Apps mobile app. This process also sets up the required user roles and other dependencies in Dataverse.

Follow these steps to install the Asset Management mobile app in Dataverse:

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Add the *Dynamics 365 Asset Management Mobile Application* to your Dataverse environment by following the instructions given in [Manage Dynamics 365 apps](/power-platform/admin/manage-apps#install-an-app).

## Grant access to the mobile application in Dataverse

Once the mobile application solution is installed on your environment's Dataverse environment, you must be shared it with your users. To share the Asset Management mobile application (which is a canvas application), follow the instructions given in [Share a canvas app with your organization](/power-apps/maker/canvas-apps/share-app#share-an-app).

Each relevant user must be assigned a role that lets them work with the Dataverse Supply Chain Management virtual tables installed by the solution. The solution installs a role called *Asset Management Mobile Application User Role* that grants access privileges to all the required virtual tables. You can assign the role to a Dataverse group team and then any user that is a member of that team will have the role as well.

- For instructions on how to assign a role to a group team, see [Manage group teams](/power-platform/admin/manage-group-teams#manage-the-security-roles-of-a-team).
- For instructions on how to assign a role directly to a user instead, see [Assign a security role to a user](/power-platform/admin/assign-security-roles).
- We recommend that you use group teams to assign the role to multiple users. For information about how to manage team members, see [Microsoft Dataverse teams management](/power-platform/admin/manage-teams#manage-team-members).

## Configure users and work orders in Supply Chain Management

Each user that will use the Asset Management mobile app must be set up as described in the following subsections.

### Set up user accounts to maintain assets and/or request maintenance

Each Supply Chain Management user that should be able to operate the Asset Management mobile app must have one or both of the following standard security roles:

- *Maintenance requester* – Allows a Supply Chain Management user account to use the app to create maintenance requests.
- *Maintenance worker* – Allows a Supply Chain Management user account to use the app to manage maintenance work orders.

Users with the *System administrator* role can both create maintenance requests and manage work orders using the app.

Follow these steps to add the required security roles to a Supply Chain Management user and check that user's **Person** setting:

1. Sign in to your Supply Chain Management environment with an administrator account.
1. Go to **System administration \> Users \> Users**.
1. Use the filter to find a user that should be able to use the app.
1. Open the details page for the selected user by selecting the hyperlink for the **User ID**.
1. Check the **Person** field to see which person is assigned to the current user account. If a person is assigned, write down their name. If no person is assigned, then you'll assign one in the next section.
1. On the **User's roles** FastTab toolbar, select **Assign roles** to open the **Assign roles to user** dialog.
1. In the **Role name** column, find and select both the *Maintenance requester* and *Maintenance worker* roles.
1. Select **OK** to apply your settings and close the dialog.

> [!NOTE]
> User role organization assignments are not supported. If any of the security roles set for a selected user have been assigned one or more organizations that are different than the user's [default company](../../../fin-ops-core/fin-ops/get-started/personalize-user-experience.md#system-wide-options-for-the-current-user), the app installation will fail.

For more information about how to set up roles and security in Supply Chain Management, see
[Security roles](../../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md#security-roles).

### Set up a maintenance worker for each user

Follow these steps to confirm or create a maintenance worker for a selected user account.

1. Go to **Asset Management \> Setup \> Workers \> Workers**.
1. Do one of the following steps, depending on whether the user account you set up in the previous section had a **Person** assigned.

    - If a person was assigned, then check whether that same person is listed here as a maintenance worker. If not, set up a maintenance worker for that person now. If you need to set up a worker, see [Maintenance workers and worker groups](../setup-for-objects/workers-and-worker-groups.md) for instructions.
    - If no person was assigned, then either choose a maintenance worker from this list or add the person you want to use as a maintenance worker as described in [Maintenance workers and worker groups](../setup-for-objects/workers-and-worker-groups.md). Then, go back to **System administration \> Users \> Users**, open the user account you're setting up, and assign the maintenance worker you chose or created here as the **Person** for that account.

> [!CAUTION]
> The **Person** setting for user accounts is permanent, so you won't be able to edit it after saving. Make sure you choose the right one when setting up the user account.

## Install and launch the Asset Management mobile app

Follow these steps to download and use the Asset Management mobile app on a mobile device.

1. Install the Power Apps mobile app as described in [Install the Power Apps mobile app](/power-apps/mobile/run-powerapps-on-mobile).
1. Launch the Power Apps mobile app and sign in using the same corporate account that you use to sign in to Supply Chain Management.
1. Use the **Search** field to search for *Asset Management*. It's a canvas app, so you can add it to your favorites list in Power Apps by swiping left on it after you find it.
1. Open the Asset Management mobile app and start using it.

## Clear the Power Apps cache on a mobile device after updating the backend setup

If the backend setup is modified in Supply Chain Management after installing the Power Apps mobile app on a mobile device (for example by changing the legal entity setup), then you may need to clear the cache in Power Apps to update the local setup data. This operation will allow Power Apps to reload the settings that otherwise might not take effect until the cache is cleared.

To clear the Power Apps cache on a mobile device:

1. Sign into the Power Apps mobile app.
1. Select your user account icon at the top left of the screen to open the settings menu.
1. Select **Clear cache** to open the **Clear cache** dialog.
1. Select **Confirm**.
