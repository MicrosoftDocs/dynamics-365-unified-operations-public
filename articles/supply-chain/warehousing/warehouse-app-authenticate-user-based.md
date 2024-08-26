---
title: User-based authentication for the Warehouse Management mobile app
description: Learn how to configure the Warehouse Management app to connect to your Dynamics 365 Supply Chain Management environment using user-based authentication.
author: JTOne123
ms.author: pavlodatsiuk
ms.topic: how-to
ms.date: 03/07/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: SysAADClientTable, WHSMobileAppField, WHSMobileAppFieldPriority, WHSRFMenu, WHSRFMenuItem, WHSWorker
---

# User-based authentication for the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

The Warehouse Management mobile app supports the following types of user-based authentication:

- Device code flow authentication
- Username and password authentication

> [!IMPORTANT]
> All Microsoft Entra ID accounts that are used to sign in must be granted only the minimum set of permissions that they require to perform their warehousing tasks. Permissions should be strictly limited to warehouse mobile device user activities. Never use an admin account to sign in to devices.

## <a name="scenarios"></a>Scenarios for managing devices, Microsoft Entra ID users, and mobile device users

For security purposes, the Warehouse Management mobile app uses Microsoft Entra ID to authenticate the connection between the app and Dynamics 365 Supply Chain Management. There are two basic scenarios for managing Microsoft Entra ID user accounts for your various devices and users: one where each Microsoft Entra ID user account represents a unique device and one where each Microsoft Entra ID user represents a unique human worker. In each case, each human worker will have one *warehouse worker* record set up in the Warehouse management module, plus one or more *mobile device user accounts* for each warehouse worker record. For warehouse worker accounts that have more than one mobile device user account, it's possible to make one of them the default mobile device user account. The two scenarios are:

- **Use one Microsoft Entra ID user account for each mobile device** – In this scenario, admins set up the Warehouse Management mobile app to use either [device code flow authentication](#deviceCodeFlow) or [username/password authentication](#usernamePasswordFlow) to connect to Supply Chain Management through the *device's* Microsoft Entra ID account. (In this scenario, human workers don't need a Microsoft Entra ID user account.) The app then shows a sign-in page that lets human workers sign in to the app so they can gain access to the work and other records that apply to them at their location. Human workers sign in by using the user ID and password of one of the mobile device user accounts that are assigned to their warehouse worker record. Because human workers must always enter a user ID, it doesn't matter whether one of the mobile device user accounts is set as the default account for the warehouse worker record. When a human worker signs out, the app remains authenticated with Supply Chain Management but shows the sign-in page again, so that the next human worker can sign in by using their mobile device user account.
- **Use one Microsoft Entra ID user account for each human worker** – In this scenario, each human user has a Microsoft Entra ID user account that's linked to their warehouse worker account in Supply Chain Management. Therefore, the Microsoft Entra ID user sign-in might be all that the human worker needs to both authenticate the app with Supply Chain Management and sign in to the app, provided that a [default user ID](mobile-device-work-users.md#set-wma-users) is set for the warehouse worker account. This scenario also supports [single sign-on](#sso) (SSO), because the same Microsoft Entra ID session can be shared across other apps on the device (such as Microsoft Teams or Outlook) until the human worker signs out of the Microsoft Entra ID user account.

## <a name="deviceCodeFlow"></a>Device code flow authentication

When you use device code authentication, the Warehouse Management mobile app generates and shows a unique device code. The admin who is setting up the device must then enter this device code into an online form, together with the credentials (name and password) for a Microsoft Entra ID user account that represents either the device itself or the human worker who is signing in (depending on how the admin has implemented the system). In some cases, depending on how the Microsoft Entra ID user account is configured, an admin might also have to approve the sign-in. In addition to the unique device code, the mobile app shows the URL where the admin must enter the code and the credentials for the Microsoft Entra ID user account.

Device code authentication simplifies the authentication process, because users don't have to manage certificates or client secrets. However, it introduces a few extra requirements and restrictions:

- You should create a unique Microsoft Entra ID user account for each device or human worker. In addition, *these accounts should be strictly limited so that they can perform only warehouse mobile device user activities*.
- While a worker is signing in by using the Warehouse Management mobile app, a generated device code is shown to them. This code expires after 15 minutes and is then hidden by the app. If the code expires before sign-in is completed, the worker must generate a new code by selecting **Connect** again in the app.
- If a device remains [idle for 90 days](/azure/active-directory/develop/refresh-tokens), it's automatically signed out.
- Single sign-on (SSO) isn't supported when you use device code flow authentication together with a mobile mass deployment (MDM) system (such as Intune) to distribute the Warehouse Management mobile app. You can still use an MDM system to deliver the app to each mobile device and deliver a `connections.json` file that sets up connections using device code. The only difference is that workers must manually sign in when they start to use the app. (This step is required only once.)

## <a name="usernamePasswordFlow"></a>Username/password authentication

When you use username/password authentication, each human worker must enter the Microsoft Entra ID username and password associated either with the device or with themselves (depending on the [authentication scenario](#scenarios) you're using). They might also need to enter a mobile device user account ID and password, depending on their [warehouse worker record setup](mobile-device-work-users.md). This authentication method supports [single sign-on](#sso) (SSO), which also enhances the convenience of mobile mass deployment (MDM).

## <a name="create-service"></a>Register an application in Microsoft Entra ID (optional)

The Warehouse Management mobile app uses a Microsoft Entra ID application to authenticate and connect to your Supply Chain Management environment. You can use a global application that's provided and maintained by Microsoft, or you can register your own application in Microsoft Entra ID by following the procedure in this section.

> [!IMPORTANT]
> In most situations, we recommend that you use the global Microsoft Entra ID application, because it's easier to set up, use, and maintain. (Learn more in [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md).) In that case, you can skip this section. However, if you have specific requirements that the global application doesn't meet (such as the requirements for some on-premises environments), you can register your own application as described here.

The following procedure shows one way to register an application in Microsoft Entra ID. For detailed information and alternatives, use the links after the procedure.

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
1. In the **Configure Desktop \+ devices** dialog box, set the **Custom redirect URIs** field to the following value:

    ``` text
    ms-appx-web://microsoft.aad.brokerplugin/S-1-15-2-3857744515-191373067-2574334635-916324744-1634607484-364543842-2321633333
    ```

1. Select **Configure** to save your settings and close the dialog boxes.
1. You return to the **Authentication** page, which now shows your new platform configuration. Select **Add a platform** again.
1. In the **Configure platform** dialog box, select **Android**.
1. In the **Configure your Android app** dialog box, set the following fields:

    - **Package name** – Enter the following value:

        ``` text
        com.microsoft.warehousemanagement
        ```

    - **Signature hash** – Enter the following value:

        ``` text
        hpavxC1xAIAr5u39m1waWrUbsO8=
        ```

1. Select **Configure** to save your settings and close the dialog box. Then select **Done** to return to the **Authentication** page, which now shows your new platform configurations.
1. Select **Add a platform** again.
1. In the **Configure platform** dialog box, select **iOS / macOS**.
1. In the **Configure your iOS or macOS app** dialog box, set the **Bundle ID** field to *com.microsoft.WarehouseManagement*.
1. Select **Configure** to save your settings and close the dialog box. Then select **Done** to return to the **Authentication** page, which now shows your new platform configurations.
1. In the **Advanced settings** section, set **Allow public client flows** to *Yes*.
1. In the **Manage** list, select **API permissions**.
1. Select **Add a permission**.
1. In the **Request API permissions** dialog box, on the **Microsoft APIs** tab, select the **Dynamics ERP** tile and then the **Delegated permissions** tile. Under **CustomService**, select the **CustomService.FullAccess** checkbox. Finally, select **Add permissions** to save your changes.
1. On the left navigation pane, select **Microsoft Entra ID**.
1. In the **Manage** list, select **Enterprise applications**. Then, in the new **Manage** list, select **All applications**.
1. In the search form, enter the name that you entered for the app earlier in this procedure. Confirm that the **Application ID** value for the app that's found matches the client ID that you copied earlier. Then select the link in the **Name** column to open the properties for the app.
1. In the **Manage** list, select **Properties**.
1. Set the **Assignment required?** option to *Yes* and the **Visible to users?** option to *No*. Then select **Save** on the toolbar.
1. In the **Manage** list, select **Users and groups**.
1. On the toolbar, select **Add user/group**.
1. On the **Add Assignment** page, select the link under the **Users** heading.
1. In the **Users** dialog box, select each user that you'll use to authenticate devices with Supply Chain Management.
1. Select **Select** to apply your settings and close the dialog box. Then select **Assign** to apply your settings and close the **Add Assignment** page.
1. In the **Security** list, select **Permissions**.
1. Select **Grant admin consent for \<*your tenant*\>**, and grant admin consent on behalf of your users. If you lack the necessary permissions, return to the **Manage** list, open **Properties**, and set the **Assignment required?** option to *False*. Each user can then provide consent individually.

For more information about how to register an application in Microsoft Entra ID, see the following resources:

- For instructions that show how to use Windows PowerShell to register an application in Microsoft Entra ID, see [How to: Use Azure PowerShell to create a service principal with a certificate](/azure/active-directory/develop/howto-authenticate-service-principal-powershell).

- For complete details about how to manually register an application in Microsoft Entra ID, see the following articles:
    - [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app)
    - [How to: Use the portal to create a Microsoft Entra ID application and service principal that can access resources](/azure/active-directory/develop/howto-create-service-principal-portal)

## <a name="user-azure-ad"></a>Set up employee, user, and warehouse worker records Supply Chain Management

Before workers can begin to sign in by using the mobile app, each Microsoft Entra ID account that you assigned to the enterprise app in Azure must have a corresponding employee record, user record, and warehouse worker record in Supply Chain Management. For information about how to set up these records, see [Mobile device user accounts](mobile-device-work-users.md).

## <a name="sso"></a>Single sign-on

To use single sign-on (SSO), you must be running Warehouse Management mobile app version 2.1.23.0 or later.

SSO enables users to sign in without having to enter a password. It works by reusing credentials from Intune Company Portal ([Android](/mem/intune/user-help/sign-in-to-the-company-portal) only), Microsoft Authenticator ([Android](/mem/intune/user-help/sign-in-to-the-company-portal) and [iOS](/mem/intune/user-help/sign-in-to-the-company-portal)), or other apps on the device.

> [!NOTE]
> SSO requires that you use [username/password](#usernamePasswordFlow) authentication.

To use SSO, follow one of these steps, depending on how you configure the connection.

- If you *manually configure the connection* in the Warehouse Management mobile app, you must enable the **Brokered Authentication** option on the mobile app's [**Edit connection** page](install-configure-warehouse-management-app.md#config-manually).
- If you *configure the connection by using a JavaScript Object Notation (JSON) file or QR code*, you must include `"UseBroker": true` in your [JSON file or QR code](install-configure-warehouse-management-app.md#connection-file-qr).

> [!IMPORTANT]
>
> - To use mobile mass deployment (MDM), you must enable SSO.
> - The Warehouse Management mobile app does *not* support [shared device mode](/entra/identity-platform/msal-shared-devices).

## <a name="revoke"></a>Remove access for a device that uses user-based authentication

If a device is lost or compromised, you must remove its ability to access Supply Chain Management. When a device is authenticated by using the device code flow, it's essential that you disable the associated user account in Microsoft Entra ID to revoke access for that device if it's ever lost or compromised. By disabling the user account in Microsoft Entra ID, you effectively revoke access for any device that uses the device code that's associated with that user account. For this reason, we recommend that you have one Microsoft Entra ID user account per device.

To disable a user account in Microsoft Entra ID, follow these steps.

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. On the left navigation pane, select **Microsoft Entra ID**, and ensure that you're in the correct directory.
1. In the **Manage** list, select **Users**.
1. Find the user account that's associated with the device code, and select the name to open the user's profile.
1. On the toolbar, select **Revoke sessions** to revoke the user account's sessions.

> [!NOTE]
> Depending on how you set up your authentication system, you might also want to change the user account's password or completely disable the user account.

## Related information

- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)
- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Service-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-service-based.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
