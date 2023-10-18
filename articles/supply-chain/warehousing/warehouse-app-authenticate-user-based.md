---
title: Authenticate users by using device code flow
description: This article explains how to configure the Warehouse Management mobile app to connect to your Microsoft Dynamics 365 Supply Chain Management environment using user-based authentication.
author: pavlodatsiuk
ms.author: pavlodatsiuk
ms.reviewer: kamaybac
ms.search.form: SysAADClientTable, WHSMobileAppField, WHSMobileAppFieldPriority, WHSRFMenu, WHSRFMenuItem, WHSWorker
ms.topic: how-to
ms.date: 10/18/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Authenticate users by using device code flow

[!include [banner](../includes/banner.md)]

When you use device code flow authentication, the Warehouse Management mobile app generates and shows a unique device code. The user who is setting up the device must then enter this device code into an online form, together with the credentials (name and password) for a Microsoft Entra ID user account that represents either the device itself or the user who is signing in (depending on how the admin has implemented the system). In some cases, depending on how the Microsoft Entra ID user account is configured, an admin might also have to approve the sign-in. In addition to the unique device code, the mobile app shows the URL where the user must enter the code and the credentials for the Microsoft Entra ID user account.

Device code flow authentication simplifies the authentication process, because users don't have to manage certificates or client secrets. However, it introduces a few extra requirements and restrictions:

- You should create a unique Microsoft Entra ID user account for each device or user. In addition, *these accounts should be strictly limited so that they can perform only warehouse mobile device user activities*.
- If a device remains [idle for 90 days](/azure/active-directory/develop/refresh-tokens), it's automatically signed out.
- The device code flow isn't fully supported by mobile mass deployment (MDM) systems such as Intune.

> [!IMPORTANT]
> All Microsoft Entra ID accounts that are used to sign in via the device code flow must be granted only the minimum set of permissions that they require to perform their warehousing tasks. Permissions should be strictly limited to warehouse mobile device user activities. Never use an admin account to sign in to devices.

## <a name="create-service"></a>Create a web service application in Microsoft Entra ID

To enable the Warehouse Management mobile app to interact with a specific Supply Chain Management server, you must register a web service application for the Supply Chain Management tenant in Microsoft Entra ID. The following procedure shows one way to complete this task. For detailed information and alternatives, see the links after the procedure.

1. In a web browser, go to [https://portal.azure.com](https://portal.azure.com/).
1. Enter the name and password of the user who has access to the Azure subscription.
1. In the Azure portal, on the left navigation pane, select **Microsoft Entra ID**.
1. Make sure that you're working with the instance of Microsoft Entra ID that's used by Supply Chain Management.
1. In the **Manage** list, select **App registrations**.
1. On the toolbar, select **New registration** to open the **Register an application** wizard.
1. Enter a name for the application, select the **Accounts in this organizational directory only** option, and then select **Register**.
1. Your new app registration is opened. Make a note of the **Application (client) ID** value, because you'll need it later. This ID will be referred to later in this article as the *client ID*.
1. Complete the following steps to use the device code flow to authenticate devices, follow the steps to set it up, and grant the required API permissions.

    1. In the **Manage** list, select **Authentication**.
    1. Set the **Enable the following mobile and desktop flows** option to *Yes* to enable the device code flow for your application. Then select **Save**.
    1. In the **Manage** list, select **API permissions**.
    1. Select **Add a permission**.
    1. In the **Request API permissions** dialog box, on the **Microsoft APIs** tab, select the **Dynamics ERP** tile and then the **Delegated permissions** tile. Under **CustomService**, select the **CustomService.FullAccess** checkbox. Finally, select **Add permissions** to save your changes.
    1. On the left navigation pane, select **Microsoft Entra ID**.
    1. In the **Manage** list, select **Enterprise applications**. Then, in the new **Manage** list, select the **All applications** tab.
    1. In the search form, enter the name that you entered for the app earlier in this procedure. Confirm that the **Application ID** value for the app that's found matches the client ID that you copied earlier. Then select the link in the **Name** column to open the properties for the app.
    1. In the **Manage** list, select **Properties**.
    1. Set the **Assignment required?** option to *Yes* and the **Visible to users?** option to *No*. Then select **Save** on the toolbar.
    1. In the **Manage** list, select **Users and groups**.
    1. On the toolbar, select **Add user/group**.
    1. On the **Add Assignment** page, select the link under the **Users** heading.
    1. In the **Users** dialog box, select each user that you'll use to authenticate devices with Supply Chain Management.

For more information about how to set up web service applications in Microsoft Entra ID, see the following resources:

- For instructions that show how to use Windows PowerShell to set up web service applications in Microsoft Entra ID, see [How to: Use Azure PowerShell to create a service principal with a certificate](/azure/active-directory/develop/howto-authenticate-service-principal-powershell).

- For complete details about how to manually create a web service application in Microsoft Entra ID, see the following articles:
    - [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app)
    - [How to: Use the portal to create a Microsoft Entra ID application and service principal that can access resources](/azure/active-directory/develop/howto-create-service-principal-portal)

## Set up mobile-device user accounts in Supply Chain Management

To manage user access and permissions in Supply Chain Management while integrating with Microsoft Entra ID, you must follow the procedures outlined in [Create and configure a user account in Supply Chain Management](install-configure-warehouse-management-app.md#user-azure-ad).

## <a name="revoke"></a>Remove access for a device that authenticates by using the device code flow

If a device is lost or compromised, you must remove its ability to access Supply Chain Management. When a device is authenticated by using the device code flow, it's essential that you disable the associated user in Microsoft Entra ID to revoke access for that device if it's ever lost or compromised. By disabling the user in Microsoft Entra ID, you effectively revoke access for any device that uses the device code that's associated with that user. For this reason, we recommend that you have one Microsoft Entra ID user per device.

To disable a user in Microsoft Entra ID, follow these steps.

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. On the left navigation pane, select **Microsoft Entra ID**, and ensure that you're in the correct directory.
1. In the **Manage** list, select **Users**.
1. Find the user who is associated with the device code, and select the name to open the user's profile.
1. On the toolbar, select **Revoke sessions** to revoke the user's sessions.

> [!NOTE]
> Depending on how you set up your authentication system, you might also want to change the user's password or completely disable the user account.

## Additional resources

- [Install the Warehouse Management mobile app](/install-configure-warehouse-management-app.md)
- [Authenticate by using a certificate or client secret](warehouse-app-authenticate-service-based.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
