---
title: User-based authentication for the Warehouse Management mobile app
description: This article explains how to configure the Warehouse Management mobile app to connect to your Microsoft Dynamics 365 Supply Chain Management environment using user-based authentication.
author: JTOne123
ms.author: pavlodatsiuk
ms.reviewer: kamaybac
ms.search.form: SysAADClientTable, WHSMobileAppField, WHSMobileAppFieldPriority, WHSRFMenu, WHSRFMenuItem, WHSWorker
ms.topic: how-to
ms.date: 02/06/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# User-based authentication for the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

The Warehouse Management mobile app supports the following types of user-based authentication:

- Device code flow authentication
- Username and password authentication

## <a name="scenarios"></a>Scenarios for managing devices, Microsoft Entra ID users, and mobile device users

For security purposes, the Warehouse Management mobile app uses Microsoft Entra ID to authenticate the connection between the app and Supply Chain Management. There are two basic scenarios for managing Microsoft Entra ID user accounts for your various devices and users: one where each Microsoft Entra ID user accounts represents a unique device and one where each Microsoft Entra ID user represents a unique human worker. In each case, each human worker will have one *warehouse worker* record set up in the Warehouse management module, plus one or more *mobile device user accounts* for each warehouse worker record. For warehouse worker accounts that have more than one mobile device user account, it's possible to make one of them the default mobile device user account. The two scenarios are:

- **Use one Microsoft Entra ID user account for each mobile device** – In this scenario, admins set up the Warehouse Management mobile app to use either [device code flow authentication](warehouse-app-authenticate-user-based.md#device-code-authentication) or [username/password authentication](warehouse-app-authenticate-user-based.md#usernamepassword-authentication) to connect to Supply Chain Management through the *device's* Microsoft Entra ID account (in this scenario, human workers don't need a Microsoft Entra ID user account). The app then shows a sign-in screen that lets human workers sign in to the app so they can gain access to the work and other records that apply to them at their location. Human workers sign in using the user ID and password of one of the mobile device user accounts assigned to their warehouse worker record. Human workers must always enter a user ID, so it doesn't matter which of these mobile device user accounts is set as the default for the warehouse worker record. When a human worker signs out, the app remains authenticated with Supply Chain Management but shows the sign-in screen again, so the next human worker can sign in using their mobile device user account.
- **Use one Microsoft Entra ID user account for each human worker** – In this scenario, each human user has a Microsoft Entra ID user account that's linked to their warehouse worker account in Supply Chain Management. As a result, the Microsoft Entra ID user sign-in might be all the human worker needs to both authenticate the app with Supply Chain Management and sign in to the app, provided the warehouse worker account has a [default user ID](mobile-device-work-users.md#set-up-mobile-device-user-accounts)  set for that warehouse worker account (or just one user ID for the warehouse worker account). This scenario also supports [single sign-on](warehouse-app-authenticate-user-based.md#single-sign-on) (SSO) because the same Microsoft Entra ID session can be shared across other apps on the device (such as Microsoft Teams or Microsoft Outlook) until the human worker signs out of the Microsoft Entra ID user account.

## <a name="deviceCodeFlow"></a>Device code flow authentication

When you use device code authentication, the Warehouse Management mobile app generates and shows a unique device code. The admin who is setting up the device must then enter this device code into an online form, together with the credentials (name and password) for a Microsoft Entra ID user account that represents either the device itself or the human worker who is signing in (depending on how the admin has implemented the system). In some cases, depending on how the Microsoft Entra ID user account is configured, an admin might also have to approve the sign-in. In addition to the unique device code, the mobile app shows the URL where the admin must enter the code and the credentials for the Microsoft Entra ID user account.

Device code authentication simplifies the authentication process, because users don't have to manage certificates or client secrets. However, it introduces a few extra requirements and restrictions:

- You should create a unique Microsoft Entra ID user account for each device or human worker. In addition, *these accounts should be strictly limited so that they can perform only warehouse mobile device user activities*.
- If a generated device code that is not used for authentication will expire after 15 minutes and the Warehouse Management mobile app will hide it. The user needs to press
*Connect* once more for the mobile app to generate a new code.
- If a device remains [idle for 90 days](/azure/active-directory/develop/refresh-tokens), it's automatically signed out.
- The device code flow isn't supported by mobile mass deployment (MDM) systems such as Intune, as the code is generated the moment one unauthenticated device tries to connect to Supply Chain Management.

[comment]: <> (Does this apply to both devicecode and userpass? if so we should move it below and change the text)
> [!IMPORTANT]
> All Microsoft Entra ID accounts that are used to sign in via the device code flow must be granted only the minimum set of permissions that they require to perform their warehousing tasks. Permissions should be strictly limited to warehouse mobile device user activities. Never use an admin account to sign in to devices.

## <a name="usernamePasswordFlow"></a>Username/password authentication
[comment]: <> (Does this section bring value? I added it because Bostjan created a hyperlink in his "scenarios" above)
When you use username/password authentication, the human worker must enter the Microsoft Entra ID username and password accossiated either with the device of with themselves (see (#scenarios)). Whether or not this is all the human worker needs to authenticate and sign in to the app, so they can gain access to the work depends on the Supply Chain Management [worker setup](mobile-device-work-users.md). This scenario also supports [single sign-on](warehouse-app-authenticate-user-based.md#single-sign-on) (SSO), which also enabled mobile mass deployment (MDM).

## <a name="create-service"></a>Create a web service application in Microsoft Entra ID

To enable the Warehouse Management mobile app to interact with a specific Supply Chain Management server, you must register a web service application for the Supply Chain Management tenant in Microsoft Entra ID. The following procedure shows one way to complete this task. For detailed information and alternatives, see the links after the procedure.

1. In a web browser, go to [https://portal.azure.com](https://portal.azure.com/).
1. Enter the name and password of the user who has access to the Azure subscription.
1. In the Azure portal, on the left navigation pane, select **Microsoft Entra ID**.
1. Make sure that you're working with the instance of Microsoft Entra ID that's used by Supply Chain Management.
1. In the **Manage** list, select **App registrations**.
1. On the toolbar, select **New registration** to open the **Register an application** wizard.
1. Enter a name for the application, select the **Accounts in this organizational directory only** option, and then select **Register**.
1. Your new app registration is opened. Make a note of the **Application (client) ID** value, because you'll need it later. This ID is referred to later in this article as the *client ID*.
1. In the **Manage** list, select **Authentication**.
1. On the **Authentication** page for the new app, set the **Enable the following mobile and desktop flows** option to *Yes* to enable the device code flow for your application. Then select **Save**.
1. Select **Add a platform**.
1. In the **Configure platform** dialog box, select **Mobile and desktop applications**.
1. In the **Configure Desktop \+ devices** dialog box, set the **Custom redirect URIs** field to *ms-appx-web://microsoft.aad.brokerplugin/S-1-15-2-3857744515-191373067-2574334635-916324744-1634607484-364543842-2321633333*.
1. Select **Configure** to save your settings and close the dialog boxes.
1. You return to the **Authentication** page, which now shows your new platform configuration. Select **Add a platform** again.
1. In the **Configure platform** dialog box, select **Android**.
1. In the **Configure your Android app** dialog box, set the following fields:

    - **Package name** – Enter *com.microsoft.warehousemanagement*.
    - **Signature hash** – Enter *hpavxC1xAIAr5u39m1waWrUbsO8=*.

1. Select **Configure** to save your settings and close the dialog box. Then select **Done** to return to the **Authentication** page, which now shows your new platform configurations.
1. Select **Add a platform** again.
1. In the **Configure platform** dialog box, select **iOS / macOS**.
1. In the **Configure your iOS or macOS app** dialog box, set the **Bundle ID** field to *com.microsoft.WarehouseManagement*.
1. Select **Configure** to save your settings and close the dialog box. Then select **Done** to return to the **Authentication** page, which now shows your new platform configurations.
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

## <a name="user-azure-ad"></a>Set up a mobile device user account in Supply Chain Management

Create a user that corresponds to the user credentials for the Warehouse Management mobile app.

1. In Supply Chain Management, go to **System administration \> Users \> Users**.
1. Create a user.
1. Assign the *Warehousing mobile device user* role to the user.

![Warehousing mobile device user role assigned to a user.](media/app-connect-app-users.png "Warehousing mobile device user role assigned to a user")

## <a name="sso"></a>Single sign-on

To use single sign-on (SSO), you must be running Warehouse Management mobile app version 2.1.23.0 or later.

SSO enables users to sign in without having to enter a password. It works by reusing credentials from Intune Company Portal ([Android](/mem/intune/user-help/sign-in-to-the-company-portal) only), Microsoft Authenticator ([Android](/mem/intune/user-help/sign-in-to-the-company-portal) and [iOS](/mem/intune/user-help/sign-in-to-the-company-portal)) or other apps on the device.

> [!NOTE]
> SSO applies exclusively to the [username/password](#usernamepassword-authentication) authentication.

The procedure in [Create a web service application in Microsoft Entra ID](#create-service) describes all the settings that are required to prepare your system to use SSO. However, to use SSO, you must also follow one of these steps, depending on how you configure the connection.

- If you *manually configure the connection* in the Warehouse Management mobile app, you must enable the **Brokered Authentication** option on the application's [connection edit [page]](install-configure-warehouse-management-app.md#config-manually).
- If you *configure the connection by using a JavaScript Object Notation (JSON) file or QR code*, you must include `"UseBroker": true` in your [JSON file or QR code](install-configure-warehouse-management-app.md#connection-file-qr).

> [!IMPORTANT]
> - To use mobile mass deployment (MDM), you must enable SSO.
> - The Warehouse Management mobile app does *not* support [shared device mode](/entra/identity-platform/msal-shared-devices).

## <a name="revoke"></a>Remove access for a device that uses user-based authentication

If a device is lost or compromised, you must remove its ability to access Supply Chain Management. When a device is authenticated by using the device code flow, it's essential that you disable the associated user account in Microsoft Entra ID to revoke access for that device if it's ever lost or compromised. By disabling the user account in Microsoft Entra ID, you effectively revoke access for any device that uses the device code that's associated with that user account. For this reason, we recommend that you have one Microsoft Entra ID user account per device.

To disable a user account in Microsoft Entra ID, follow these steps.

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. On the left navigation pane, select **Microsoft Entra ID**, and ensure that you're in the correct directory.
1. In the **Manage** list, select **Users**.
1. Find the user account that is associated with the device code, and select the name to open the user's profile.
1. On the toolbar, select **Revoke sessions** to revoke the user account's sessions.

> [!NOTE]
> Depending on how you set up your authentication system, you might also want to change the user account's password or completely disable the user account.

## Additional resources

- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)
- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Service-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-service-based.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
