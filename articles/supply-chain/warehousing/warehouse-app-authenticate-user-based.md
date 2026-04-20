---
title: User-based authentication for the Warehouse Management mobile app
description: Learn how to configure the Warehouse Management app to connect to your Dynamics 365 Supply Chain Management environment using user-based authentication.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 04/08/2026
ms.reviewer: kamaybac
ms.search.form: SysAADClientTable, WHSMobileAppField, WHSMobileAppFieldPriority, WHSRFMenu, WHSRFMenuItem, WHSWorker
ms.custom:
  - bap-template
  - sfi-ropc-nochange
---

# User-based authentication for the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

The Warehouse Management mobile app supports the following types of user-based authentication:

- Device code flow authentication
- Username and password authentication

> [!IMPORTANT]
> All Microsoft Entra ID accounts that are used to sign in must be granted only the minimum set of permissions that they require to perform their warehousing tasks. Permissions should be strictly limited to warehouse mobile device user activities. Never use an admin account to sign in to devices.

## <a name="scenarios"></a>Scenarios for managing devices, Microsoft Entra ID users, and mobile device users

The Warehouse Management mobile app uses Microsoft Entra ID to authenticate with Dynamics 365 Supply Chain Management. Choose one of two scenarios for managing Microsoft Entra ID accounts. In both scenarios, each warehouse worker has a *warehouse worker* record in the Warehouse management module with one or more *mobile device user accounts*.

### Use one Microsoft Entra ID user account per device

In this scenario, each mobile device has its own Microsoft Entra ID account. Workers don't need individual Microsoft Entra ID accounts.

It works like this:

1. The admin configures the app with [device code flow](#deviceCodeFlow) or [username/password](#usernamePasswordFlow) authentication by using the device's Microsoft Entra ID account.
1. After the app authenticates, workers sign in by using their mobile device user account credentials (user ID and password).
1. When a worker signs out, the app stays authenticated with Supply Chain Management and shows the sign-in page for the next worker.

This approach works best when multiple workers share devices at a location.

### Use one Microsoft Entra ID user account per worker

In this scenario, each worker has their own Microsoft Entra ID account linked to their warehouse worker record in Supply Chain Management.

It works like this:

1. The worker signs in with their Microsoft Entra ID credentials.
1. If a [default user ID](mobile-device-work-users.md#set-wma-users) is configured for the worker's warehouse worker account, this single sign-in authenticates the app and signs them in as a worker in one step.
1. The same Microsoft Entra ID session can be shared across other apps on the device (such as Microsoft Teams or Outlook).

This approach supports [single sign-on](#sso) (SSO) and is best when workers use dedicated devices or when you need tighter identity controls.

## <a name="deviceCodeFlow"></a>Device code flow authentication

When you use device code authentication, the Warehouse Management mobile app generates and shows a unique device code. The admin who is setting up the device must then enter this device code into an online form, together with the credentials (name and password) for a Microsoft Entra ID user account that represents either the device itself or the human worker who is signing in (depending on how the admin implements the system). In some cases, depending on how the Microsoft Entra ID user account is configured, an admin might also have to approve the sign-in. In addition to the unique device code, the mobile app shows the URL where the admin must enter the code and the credentials for the Microsoft Entra ID user account.

Device code authentication simplifies the authentication process, because users don't have to manage certificates or client secrets. However, it introduces a few extra requirements and restrictions:

- Create a unique Microsoft Entra ID user account for each device or human worker. In addition, *strictly limit these accounts so that they can perform only warehouse mobile device user activities*.
- While a worker is signing in by using the Warehouse Management mobile app, the app shows a generated device code. This code expires after 15 minutes and is then hidden by the app. If the code expires before sign-in is completed, the worker must generate a new code by selecting **Connect** again in the app.
- Devices are automatically signed out if they're not used or accessed for 90 days. Signed out devices must be reauthenticated before they can be used again. Learn more in [Refresh tokens in the Microsoft identity platform](/azure/active-directory/develop/refresh-tokens).
- Single sign-on (SSO) isn't supported when you use device code flow authentication together with a mobile mass deployment (MDM) system (such as Intune) to distribute the Warehouse Management mobile app. You can still use an MDM system to deliver the app to each mobile device and deliver a `connections.json` file that sets up connections using device code. The only difference is that workers must manually sign in when they start to use the app. (This step is required only once.)

## <a name="usernamePasswordFlow"></a>Username/password authentication

When you use username/password authentication, each human worker must enter the Microsoft Entra ID username and password associated either with the device or with themselves (depending on the [authentication scenario](#scenarios) you're using). They might also need to enter a mobile device user account ID and password, depending on their [warehouse worker record setup](mobile-device-work-users.md). This authentication method supports [single sign-on](#sso) (SSO), which also enhances the convenience of mobile mass deployment (MDM).

## <a name="create-service"></a>Manually create an application registration in Microsoft Entra ID

The Warehouse Management mobile app uses a Microsoft Entra ID application registration to authenticate and connect to your Supply Chain Management environment. You can use a global application that's provided and maintained by Microsoft, or you can register your own application in Microsoft Entra ID by following the procedure in this section.

> [!IMPORTANT]
> Use the global application if possible. It's easier to set up and maintain, and it supports most scenarios, including [Microsoft Entra Conditional Access](warehouse-app-conditional-access-enable.md). You only need a manually created application registration if you have specific requirements that the global application doesn't meet (for example, because you're using certain on-premises environment configurations).
>
> If you're able to use the global application, you can skip this section. For more information about how to use the global application, see [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md). If you require a manual application registration, continue with this section.

The following procedure shows one way to register an application in Microsoft Entra ID. For detailed information and alternatives, use the links after the procedure.

1. In a web browser, go to [https://portal.azure.com](https://portal.azure.com/).
1. Enter the name and password of the user who has access to the Azure subscription.
1. Use the search field at the top of the page to find and open the **Microsoft Entra ID** service.
1. Make sure that you're working with the instance of Microsoft Entra ID that's used by Supply Chain Management.
1. On the left navigation pane, expand **Manage** and select **App registrations**.
1. On the toolbar, select **New registration** to open the **Register an application** wizard.
1. Enter a name for the application, select the **Accounts in this organizational directory only** option, and then select **Register**.
1. Your new app registration opens. Make a note of the **Application (client) ID** value, because you need it later. This ID is referred to later in this article as the *client ID*.
1. In the **Manage** list, select **Authentication**.
1. On the **Authentication** page for the new app, open the **Settings** tab, set **Allow public client flows** to *Enabled*, and select **Save**.

1. Open the **Redirect URI configuration** tab and select **Add redirect URI**.

1. In the dialog, select **Mobile and desktop applications**.
1. Set the input field to the following value, where *{clientId}* is the client ID that you copied earlier in this procedure:

    ``` text
    ms-appx-web://microsoft.aad.brokerplugin/{clientId}
    ```

    > [!NOTE]
    > If you still have devices running the deprecated version 3.x of the app, you must also add the following redirect URI:
    >
    > `ms-appx-web://microsoft.aad.brokerplugin/S-1-15-2-3857744515-191373067-2574334635-916324744-1634607484-364543842-2321633333`

    Select **Configure** to save your settings and close the dialog to return to the **Authentication** page, which now shows your new platform configurations.

1. On the **Redirect URI configuration** tab, select **Add redirect URI**.

1. In the dialog, select **Android**. Then set the following fields:

    - **Package name** – Enter the following value (case sensitive):

        ``` text
        com.Microsoft.Warehousemanagement
        ```

    - **Signature hash** – Enter the following value:

        ``` text
        Xo8WBi6jzSxKDVR4drqm84yr9iU=
        ```

    Select **Configure** to save your settings and close the dialog to return to the **Authentication** page, which now shows your new platform configurations.

1. Repeat the previous two steps to add another Android platform configuration, but this time set the following values:

    - **Package name** – Enter the following value (case sensitive and different from the previous configuration):

        ``` text
        com.microsoft.warehousemanagement
        ```

    - **Signature hash** – Enter the following value:

        ``` text
        hpavxC1xAIAr5u39m1waWrUbsO8=
        ```

    > [!TIP]
    > - The first signature hash (`Xo8WBi6jzSxKDVR4drqm84yr9iU=`) enables brokered authentication and is required for features such as [Conditional Access](warehouse-app-conditional-access-enable.md) and [SSO](#sso). The second hash (`hpavxC1xAIAr5u39m1waWrUbsO8=`) supports older versions of the app. Include both to ensure full compatibility.
    > - The values for **Package name** are case sensitive and the required casing is different for each Android platform configuration. The values are otherwise similar.

1. On the **Redirect URI configuration** tab, select **Add redirect URI**.

1. In the dialog, select **iOS / macOS**.
1. Set the **Bundle ID** field to the following value:

    ``` text
    com.microsoft.WarehouseManagement
    ```

1. Select **Configure** to save your settings. Close the dialog to return to the **Authentication** page, which now shows your new platform configurations.
1. On the left navigation pane, expand **Manage** and select **API permissions**.
1. Select **Add a permission**.
1. In the **Request API permissions** dialog, on the **Microsoft APIs** tab, select the **Dynamics ERP** tile and then the **Delegated permissions** tile. Under **CustomService**, select the **CustomService.FullAccess** checkbox. Finally, select **Add permissions** to save your changes.
1. Use the search field at the top of the page to find and open the **Microsoft Entra ID** service.
1. On the left navigation pane, expand **Manage** and select **Enterprise applications**. Then, in the new **Manage** list, select **All applications**.
1. In the search form, enter the name that you entered for the app earlier in this procedure. Confirm that the **Application ID** value for the app matches the client ID that you copied earlier. Then select the link in the **Name** column to open the properties for the app.
1. On the left navigation pane, expand **Manage** and select **Properties**.
1. Set the **Assignment required?** option to *Yes* and the **Visible to users?** option to *No*. Then select **Save** on the toolbar.
1. On the left navigation pane, expand **Manage** and select **Users and groups**.
1. On the toolbar, select **Add user/group**.
1. On the **Add Assignment** page, select the link under the **Users** heading.
1. In the **Users** dialog, select each user that you use to authenticate devices with Supply Chain Management.
1. Select **Select** to apply your settings and close the dialog. Then select **Assign** to apply your settings and close the **Add Assignment** page.
1. In the **Security** list, select **Permissions**.
1. Select **Grant admin consent for \<*your tenant*\>**, and grant admin consent on behalf of your users. If you lack the necessary permissions, return to the **Manage** list, open **Properties**, and set the **Assignment required?** option to *False*. Each user can then provide consent individually.

For more information about how to register an application in Microsoft Entra ID, see the following resources:

- For instructions that show how to use Windows PowerShell to register an application in Microsoft Entra ID, see [Use Azure PowerShell to create a service principal with a certificate](/azure/active-directory/develop/howto-authenticate-service-principal-powershell).

- For complete details about how to manually register an application in Microsoft Entra ID, see the following articles:
    - [Register an application in Microsoft Entra ID](/azure/active-directory/develop/quickstart-register-app)
    - [Register a Microsoft Entra app and create a service principal](/azure/active-directory/develop/howto-create-service-principal-portal)

## <a name="user-azure-ad"></a>Set up employee, user, and warehouse worker records in Supply Chain Management

Before workers can sign in by using the mobile app, each Microsoft Entra ID account that you assign to the enterprise app in Azure must have a corresponding employee record, user record, and warehouse worker record in Supply Chain Management. For information about how to set up these records, see [Mobile device user accounts](mobile-device-work-users.md).

## <a name="sso"></a>Single sign-on

Single sign-on (SSO) lets workers sign in to the Warehouse Management mobile app without entering a password. It works by reusing credentials from another app on the device, such as Intune Company Portal, Microsoft Authenticator, or Microsoft Teams.

> [!NOTE]
> SSO requires [username/password](#usernamePasswordFlow) authentication. It doesn't work with [device code flow](#deviceCodeFlow).

### Enable SSO

To enable SSO, configure brokered authentication by using one of the following methods:

- **Manual connection setup** – Enable the **Brokered Authentication** option on the app's [**Edit connection** page](install-configure-warehouse-management-app.md#config-manually).
- **JSON file or QR code** – Include `"UseBroker": true` in your [connection configuration](install-configure-warehouse-management-app.md#connection-file-qr).

### Prerequisites for SSO

The following table lists the broker apps that must be installed on a device for SSO to work:

| Platform | Required broker app |
|---|---|
| **Android** | [Intune Company Portal](/mem/intune/user-help/sign-in-to-the-company-portal) or [Microsoft Authenticator](/mem/intune/user-help/sign-in-to-the-company-portal) |
| **iOS** | [Microsoft Authenticator](/mem/intune/user-help/sign-in-to-the-company-portal) |
| **Windows** | The worker must have a work account configured on the device |

> [!IMPORTANT]
>
> - To use mobile mass deployment (MDM), you must enable SSO.
> - The Warehouse Management mobile app *doesn't* support [shared device mode](/entra/identity-platform/msal-shared-devices).

## <a name="revoke"></a>Remove access for a device that uses user-based authentication

If a device is lost or compromised, revoke its access to Supply Chain Management immediately. Disabling the associated Microsoft Entra ID user account revokes access for all devices that use that account. This limitation is why the [one account per device](#scenarios) approach is recommended. It lets you isolate and revoke access for a single device without affecting others.

To revoke access, follow these steps:

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. On the left navigation pane, select **Microsoft Entra ID**, and ensure that you're in the correct directory.
1. In the **Manage** list, select **Users**.
1. To open the user's profile, find the user account associated with the device code, and select the name.
1. On the toolbar, select **Revoke sessions** to revoke the user account's sessions.

> [!NOTE]
> Depending on how you set up your authentication system, you might also want to change the user account's password or completely disable the user account.

## Related information

- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)
- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
