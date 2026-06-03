---
title: Mock the signed-in state during local development
description: Learn how to mock a signed-in user in a Microsoft Dynamics 365 Commerce online local development environment.
author: samjarawan
ms.date: 06/05/2026
ms.topic: how-to
audience: Developer
ms.reviewer: mirao
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom:
  - bap-template
  - sfi-image-nochange
  - sfi-ropc-blocked
---

# Mock the signed-in state during local development

[!include [banner](../includes/banner.md)]

This article describes how to mock a signed-in user in a Microsoft Dynamics 365 Commerce online local development environment.

When developing your e-commerce online site, you might need to develop and test scenarios for signed-in users. Instead of publishing these pages and testing against live pages, you can mock the signed-in state when running in developer mode.

## Configure your Microsoft Entra External ID tenant

Perform a one-time setup in your Microsoft Entra External ID (EEID) tenant to allow you to mock the signed-in user status. To proceed with the following steps, first sign in as a user with tenant administrator privileges.

### Create a native application

Create a native application that represents the Node application running during local development:

1. In the **Microsoft Entra External ID** tenant, go to **Entra ID** > **App registrations**, and then select **New registration**.
1. Enter a name for the application. For example, "local_node_app."
1. For **Supported account types**, select **Single tenant only - < your-tenant >**.
1. For **Redirect URIs**, add a redirect URI by following the steps in [Reply URLs](../dev-itpro/set-up-external-entra-id.md#reply-urls).
1. Select **Register** to complete the app registration.
1. Select the newly created application. Then, copy and save the value for **Application (client) ID** to use for `nativeApplicationId` and **Directory (tenant) ID** to use for `ciamTenant` in your **credentials.json** file.
1. In the left navigation pane under **Manage**, select **Authentication**.
1. Under settings, under **Implicit grant and hybrid flows** select the **ID token** and **Access token** checkboxes. Also, enable public client and native authentication flows.
1. Select **Save**.
1. In the left navigation pane under **Manage**, select **API permissions**.
1. Select **Grant admin consent for < tenant-name >**, and then select **Yes**.
1. Create a new user flow by going to **Manage** > **External Identities** > **User flows**.
1. Select **New user flow**.
1. On the **Create** page, enter a name for the user flow (for example, "local_auth_user_flow").
1. Under **Identity providers**, select the **Email Accounts** check box, and then select **Email with password option**.
1. Under **User attributes**, choose the **Given Name**, **Surname**, and **Display Name** attributes.
1. Select **Create** to create the user flow.
1. Open the user flow you created and in the left navigation pane, select **Applications**.
1. Select **Add application**.
1. From the list, select the application you created for local authentication in the previous steps. Then, select the **Select** button.
1. Add your EEID app details in Commerce headquarters as explained in [Update Commerce headquarters with the new Microsoft Entra External ID information](../dev-itpro/set-up-external-entra-id.md#update-commerce-headquarters-with-the-new-microsoft-entra-external-id-information).

Now, you have a new native application that represents your local Node application.

From the previous example, you have the following information:

| Property name | Example value |
| ------------- | ------------- |
| ciamTenant | commerceonboarding |
| nativeApplicationId | 25f6742d-f8b8-44d9-a6a0-f06d2854ac5f |

### Configure scope and register the native application

1. In the Microsoft Entra External ID settings, go to **App registrations**.
1. Open the application that the e-commerce rendering application currently uses. In the Azure portal, this application is the one whose client ID is used in the Microsoft Entra External ID configuration for your site. If Microsoft Entra External ID is already configured, you can find the application ID used for your e-commerce site in Commerce headquarters at **Commerce Shared Parameters** > **Identity Providers** in the **ClientId** field under **Relying Parties**. You can also find the application ID in Commerce site builder at **Tenant Settings** > **Site Authentication Setup** as the **Client GUID** within the EEID application configuration used for your site.
1. In the left navigation pane under **Manage**, select **Expose an API**, and verify that a **user_impersonation** scope exists. If it doesn't exist, select **Add a scope** to create one. When prompted for an **Application ID URI**, don't change the application ID URI. Add **user_impersonation** for the **Scope name**. Then, enter the values for **Admin consent display name** and **Admin consent description**.
1. Copy and save the full scope value. Use this information as the `userImpersonationScopeURL` property value in your **credentials.json** file.
1. Return to the native application you created. In the left navigation pane under **Manage**, select **API permissions**.
1. Select **Add a permission**, and then select the **APIs my organization uses** tab.
1. Search for and select the e-commerce rendering application that you created. Then, add **user_impersonation** as a permission.
1. Select **Add permissions**.
1. Select **Grant admin consent for < domain >** and select **Yes** to apply the consent. You should now see a green checkmark under **Status** for **user_impersonation**.

These steps complete the Microsoft Entra setup. You should now have all of the following values:

| Property name | Example value |
| ------------- | ------------- |
| ciamTenant | commerceonboarding |
| nativeApplicationId | 25f6742d-f8b8-44d9-a6a0-f06d2854ac5f |
| userImpersonationScopeURL | `https://commerceonboarding.onmicrosoft.com/b7ad3e87-d8b0-4c83-b08d-7c34c19f7933/user_impersonation` |

### Configure your Node application

After you finish configuring your Microsoft Entra External ID tenant, create a credentials file in your online software development kit (SDK) Node application.

The credentials file is located in the `secrets/` directory in your Node application. Create a `secrets/` directory in your application if it doesn't already exist, and then create a new file named **credentials.json** that's similar to the following example using the data you gathered previously.

```json
{
    "ciamTenant": "commerceonboarding",
    "nativeApplicationId": "25f6742d-f8b8-44d9-a6a0-f06d2854ac5f",
    "userImpersonationScopeURL": "https://commerceonboarding.onmicrosoft.com/b7ad3e87-d8b0-4c83-b08d-7c34c19f7933/user_impersonation",
    "defaultUser": {
        "name": "default",
        "email": "",
        "password": "",
        "customerAccountNumber": ""
    },
    "additionalUsers":[ 
        {
            "name": "test-user-1",
            "email": "test-user-1@example.com",
            "password": "password",
            "customerAccountNumber": ""
        }
    ]
}
```

## Configure your Microsoft Entra B2C tenant

Perform a one-time setup in your Microsoft Entra business-to-consumer (B2C) tenant to mock the signed-in user status. To proceed with the following steps, sign in as a user with tenant administrator privileges.

### Create a new resource owner password credentials (ROPC) flow

Create a new resource owner password credentials (ROPC) flow in your Microsoft Entra B2C tenant.

To create a new ROPC flow, follow these steps:

1. Sign in to the [Azure portal](https://ms.portal.azure.com/) as the tenant administrator of your Microsoft Entra B2C tenant, and then select the **Microsoft Entra B2C** service.
1. Select **User flows** and **New user flow**.
1. Select **Sign in using resource owner password credentials (ROPC)**, and then select **Create**.
1. Enter a name for the user flow (for example, "ROPC_Auth"). Copy and save the full name to use as the `ropcUserFlowName` value in your **credentials.json** file.
1. Under **Application claims**, select **Show more**.
1. Select the following application claims:
    - **Display Name**
    - **Email Addresses**
    - **Given Name**
    - **Identity provider**
    - **SurName**
    - **User's object ID**
1. Select **OK**, and then select **Create**.
1. Select the new user flow, and then select **Run user flow**.

You created a new ROPC policy to enable local sign-in. Under **Run user flow**, you should see an endpoint URL similar to `https://<LOGIN_DOMAIN>//<B2C_TENANT>.onmicrosoft.com/v2.0/.well-known/openid-configuration?p=B2C_1_ROPC_Auth`. Make a note of the **<LOGIN_DOMAIN>** and **<B2C_TENANT>** values from the URL, as you use this information in your **credentials.json** file.

In the following example image, the endpoint URL listed under **Run user flow** is `https://commerceonboardingb2c.b2clogin.com/commerceonboardingb2c.onmicrosoft.com/v2.0/.well-known/openid-configuration?p=B2C_1_ROPC_Auth`.

:::image type="content" source="media/local-sign-in-01.png" alt-text="Screenshot of the Run user flow example in Azure portal." lightbox="media/local-sign-in-01.png":::

From the previous example, you can obtain values for the `ropcUserFlowName`, `loginDomain`, and `b2cTenant` properties as follows:

| Property name | Example value |
| ------------- | ------------- |
| ropcFlowUserName | B2C_1_ROPC_Auth |
| loginDomain | commerceonboardingb2c.b2clogin.com |
| b2cTenant | commerceonboardingb2c |

### Create a native application

Next, create a native application that represents the Node application running during local development.

1. In the **Microsoft Entra B2C** settings, select **App Registrations**, and then select **New registration**.
1. Enter a name for the application. For example, "local_node_app."
1. For **Supported account types**, select **Accounts in any identity provider or organizational directory (for authenticating users with user flows)**.
1. For **Redirect URIs**, select **Public client/native (mobile & desktop)** from the drop-down list, and leave the URI as is.
1. Leave all other default values as is, and select **Register**.
1. Select the new application, and then copy and save the **Application (client) ID** value, as this ID is used later as the `nativeApplicationId` property value in your **credentials.json** file.
1. In the left navigation pane under **Manage**, select **Authentication**.
1. Select **Try out the new experience** (if displayed).
1. Under **Default client type**, select **Yes** for **Treat the application as a public client**. This setting is required for the ROPC flow.
1. Select **Save**.
1. In the left navigation pane under **Manage**, select **Manifest** to open the manifest editor.
1. Set the **oauth2AllowImplicitFlow** attribute to **True**, and then select **Save**.

You created a new native application that represents your local Node application.

From the previous examples, you obtained the following information:

| Property name | Example value |
| ------------- | ------------- |
| ropcFlowUserName | B2C_1_ROPC_Auth |
| loginDomain | commerceonboardingb2c.b2clogin.com |
| b2cTenant | commerceonboardingb2c |
| nativeApplicationId | 25f6742d-f8b8-44d9-a6a0-f06d2854ac5f |

### Configure scope and register the native application

1. In the Microsoft Entra B2C settings, go to **App registrations**.
1. Open the application that the e-commerce rendering application currently uses. In the Azure portal, this application is the one whose client ID you use in the Microsoft Entra B2C configuration for your site. If Microsoft Entra ID B2C is already configured, you can find the application ID used for your e-commerce site in Commerce headquarters at **Commerce Shared Parameters** > **Identity Providers** in the **ClientId** field under **Relying Parties**. You can also find the application ID in Commerce site builder at **Tenant Settings** > **B2C Settings** as the **Client GUID** within the B2C application configuration used for your site.
1. In the left navigation pane under **Manage**, select **Expose an API**, and verify that a **user_impersonation** scope exists. If it doesn't exist, select **Add a scope** to create one. When prompted for an **Application ID URI**, don't change the application ID URI. Add **user_impersonation** for the **Scope name**. Then, enter values for **Admin consent display name** and **Admin consent description**.
1. Copy and save the full scope value. Use this information as the `userImpersonationScopeURL` property value in your **credentials.json** file.
1. Return to the native application you created. In the left navigation pane under **Manage**, select **API permissions**.
1. Select **Add a permission**, and then select the **APIs my organization uses** tab.
1. Search for and select the e-commerce rendering application that you created. Add **user_impersonation** as a permission.
1. Select **Add permissions**.
1. Select **Grant admin consent for < domain >** and select **Yes** to apply the consent. You should now see a green checkmark under **Status** for **user_impersonation**.

These steps complete the Microsoft Entra setup. You should now have all of the following values:

| Property name | Example value |
| ------------- | ------------- |
| ropcFlowUserName | B2C_1_ROPC_Auth |
| loginDomain | commerceonboardingb2c.b2clogin.com |
| b2cTenant | commerceonboardingb2c |
| nativeApplicationId | 25f6742d-f8b8-44d9-a6a0-f06d2854ac5f |
| userImpersonationScopeURL | `https://commerceonboardingb2c.onmicrosoft.com/b7ad3e87-d8b0-4c83-b08d-7c34c19f7933/user_impersonation` |

### Configure your Node application

After you finish configuring your Microsoft Entra B2C tenant, create a credentials file in your online software development kit (SDK) Node application.

The credentials file is located in the `secrets/` directory in your Node application. Create a `secrets/` directory in your application if it doesn't already exist, and then create a new file named **credentials.json** that's similar to the following example using the data you gathered previously.

```json
{
    "loginDomain": "commerceonboardingb2c.b2clogin.com",
    "b2cTenant": "commerceonboardingb2c",
    "nativeApplicationId": "25f6742d-f8b8-44d9-a6a0-f06d2854ac5f",
    "ropcUserFlowName": "B2C_1_ROPC_Auth",
    "userImpersonationScopeURL": "https://commerceonboardingb2c.onmicrosoft.com/b7ad3e87-d8b0-4c83-b08d-7c34c19f7933/user_impersonation",
    "defaultUser": {
        "name": "default",
        "email": "",
        "password": "",
        "customerAccountNumber": ""
    },
    "additionalUsers":[ 
        {
            "name": "test-user-1",
            "email": "test-user-1@example.com",
            "password": "password",
            "customerAccountNumber": ""
        }
    ]
}
```

> [!NOTE]
> Add everything under the `secrets/` directory to your **.gitignore** file to help prevent credentials from being leaked online.

After you use the information collected in the Azure setup steps to populate your **credentials.json** file, add test accounts that you want to use during local development. The accounts you define here should be valid accounts that are already created in Dynamics 365 Commerce headquarters.

- **defaultUser**: The default user to use when the **mockUser** query parameter is set to **True**. The name value should be **default**.
- **additionalUsers**: An array of user objects that you can use to configure more users for testing. Each entry in this array should be an object with a name, email address, password, and customer account number. To sign in as one of these users, use the query parameter `mockUser=\<name>`.

### Mock a signed-in B2B user

To mock a signed-in business-to-business (B2B) user, use the **isB2bUser** property for a user credential and set it to **true**, as shown in the following example:

```json
{
    "loginDomain": "commerceonboardingb2c.b2clogin.com",
    "b2cTenant": "commerceonboardingb2c",
    "nativeApplicationId": "25f6742d-f8b8-44d9-a6a0-f06d2854ac5f",
    "ropcUserFlowName": "B2C_1_ROPC_Auth",
    "userImpersonationScopeURL": "https://commerceonboardingb2c.onmicrosoft.com/b7ad3e87-d8b0-4c83-b08d-7c34c19f7933/user_impersonation",
    "defaultUser": {
        "name": "default",
        "email": "",
        "password": "",
        "customerAccountNumber": "",
        "isB2bUser": true
    },
    "additionalUsers":[ 
        {
            "name": "test-user-1",
            "email": "test-user-1@example.com",
            "password": "password",
            "customerAccountNumber": ""
        }
    ]
}
```

## Mock sign-in status

After you complete all of the previous configuration steps, start your e-commerce Node application in local dev mode by using the **yarn start** command. The **mockUser** query parameter controls the sign-in status. It works to mock the signed-in state on mock pages and published pages. For example, you can use `https://localhost:4000?mock=homepage&mockUser=true` or `https://localhost:4000?mockUser=true`.

Use **mockUser=\<true|false|name>** to control the signed-in behavior. The following table describes the behavior of each of the query parameter values:

| mockUser value | Example | Sign in/Sign out | Description |
| -------------- | ------- | ---------------- | ----------- |
| true | mockUser=true | Sign in | Signs in as the default user. |
| name | mockUser=test-user-1 | Sign in | Signs in as the user specified in the query parameter. |
| false | mockUser=false | Sign out | Signs out the currently signed-in user. |

Use the **mockUser** query parameter to test pages as different users without signing out and signing back in again for each different user. For example, browsing `https://localhost:4000?mock=homepage&mockUser=true` and then `https://localhost:4000?mock=homepage&mockUser=test-user-1` allows you to test the homepage mock as different signed-in users.

When you hit a page with **mockUser** turned on and successfully sign in, the signed-in state persists across pages until you either sign in with a different user or sign out.

You can also make use of the sign-in and sign out buttons on the webpage itself to mock signed-in user behavior. The sign-in button signs you in as the default user, and the sign out button signs out the currently signed-in user.

## More resources

- [Request properties object](request-properties-object.md)
- [App settings](app-settings.md)
- [Platform settings file](platform-settings.md)
- [Extend a module definition file](extend-module-definition.md)
- [Cookie API overview](cookie-api-overview.md)
- [Interactive components overview](interactive-components.md)
- [Configure module properties to be shown based on context](configure-properties-context.md)
- [Globalize modules by using the CultureInfoFormatter class](globalize-modules.md)
- [Set up Azure Key Vault for secure key management](set-up-key-vault.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
