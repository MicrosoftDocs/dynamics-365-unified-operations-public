---
title: Create a custom application registration for the Warehouse Management mobile app
description: Learn how to register your own Microsoft Entra ID application for the Warehouse Management mobile app when the global application provided by Microsoft doesn't meet your requirements.
author: pefreita
ms.author: pefreita
ms.topic: how-to
ms.date: 09/07/2026
ms.reviewer: kamaybac
ms.search.form: SysAADClientTable
ms.custom:
  - bap-template
---

# Create a custom application registration for the Warehouse Management mobile app

[!INCLUDE [banner](../includes/banner.md)]

The Warehouse Management mobile app uses a Microsoft Entra ID application registration to authenticate and connect to your Supply Chain Management environment. By default, it uses a global application that Microsoft provides and maintains, and no extra setup is required.

> [!IMPORTANT]
> Most deployments don't need this article. Use the global application if possible. It's easier to set up and maintain, and it supports most scenarios, including [Microsoft Entra Conditional Access](warehouse-app-conditional-access-enable.md). When you use the global application, you don't have to provide a client ID or tenant in the app's connection settings.

You need your own app registration (and therefore a client ID) only in the following cases:

- You connect to a Dynamics 365 Finance + Operations (on-premises) environment.
- You connect to a cloud other than Azure Global (for example, a sovereign cloud such as Microsoft Azure operated by 21Vianet in China).
- You have specific requirements that the global application doesn't meet.

If none of these cases apply to you, use the global application instead. For more information, see [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md).

When you use a custom app registration, set `"AuthCloud": "Manual"` in your connection settings, and provide your client ID in `"ActiveDirectoryClientAppId"`. Learn more in [Connection settings reference](warehouse-app-connection-settings.md#connection-file-qr).

<a name="create-service"></a>

## Register the application in Microsoft Entra ID

The following procedure shows one way to register an application in Microsoft Entra ID. For detailed information and alternatives, use the links at the end of this article.

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

1. In the dialog, select **Android**. Then set the following fields:

    - **Package name** – Enter the following value (case sensitive):

        ``` text
        com.Microsoft.WarehouseManagement
        ```

    - **Signature hash** – Enter the following value:

        ``` text
        hpavxC1xAIAr5u39m1waWrUbsO8=
        ```

    Select **Configure** to save your settings and close the dialog to return to the **Authentication** page, which now shows your new platform configurations.

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

## More ways to register an application

For more information about how to register an application in Microsoft Entra ID, see the following resources:

- For instructions that show how to use Windows PowerShell to register an application in Microsoft Entra ID, see [Use Azure PowerShell to create a service principal with a certificate](/entra/identity-platform/howto-authenticate-service-principal-powershell).

- For complete details about how to manually register an application in Microsoft Entra ID, see the following articles:
    - [Register an application in Microsoft Entra ID](/entra/identity-platform/quickstart-register-app)
    - [Register a Microsoft Entra app and create a service principal](/entra/identity-platform/howto-create-service-principal-portal)

## Related information

- [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md)
- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Brokered authentication and Conditional Access](warehouse-app-conditional-access-enable.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
