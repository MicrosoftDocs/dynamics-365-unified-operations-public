---
title: Create and configure a Microsoft Entra application for account manager sign-in
description: Learn how to create and configure a Microsoft Entra application for account manager sign-in for on behalf of (OBO) functionality in Microsoft Dynamics 365 Commerce.
author: mariash529
ms.date: 07/16/2026
ms.topic: how-to
ms.reviewer: mirao
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2023-02-27
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Create and configure a Microsoft Entra application for account manager sign-in

[!include [banner](../includes/banner.md)]

This article describes how to create and configure a Microsoft Entra application for account manager sign-in for on behalf of functionality (OBO) in Microsoft Dynamics 365 Commerce.

You can use either Microsoft Entra External ID (EEID) or Microsoft Entra B2C. In the following sections, follow the configuration steps that match your identity solution.

## Create a Microsoft Entra application for account manager sign-in in the Azure B2B tenant

### [Azure AD B2C](#tab/azure-ad-b2c)

To create a Microsoft Entra application for account manager sign-in in the Azure business-to-business (B2B) tenant, follow these steps:

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. Go to the directory that contains the Microsoft Entra business-to-business (B2B) tenant that you use for sign-in in headquarters.
1. In the row of Azure services, select **Microsoft Entra ID**.
1. On the **Manage** menu, select **App Registration**, and then select **New Registration**.
1. Enter a name for the application (for example, **Account Manager Employer Auth**).
1. Under **Supported account types**, select **Accounts in this organizational directory only (`<YOUR-TENANT-NAME>` only - Single tenant)**, where `<YOUR-TENANT-NAME>` is the name of your tenant.
1. Under **Redirect URI**, select **Web**, and then, in the URL field, enter `https://<your-tenant-name>.b2clogin.com/<your-tenant-name>.onmicrosoft.com/oauth2/authresp`, where `<your-tenant-name>` is the name of your tenant. If you use a custom domain, enter `https://<your-domain-name>/<your-tenant-name>.onmicrosoft.com/oauth2/authresp`, where `<your-domain-name>` is your custom domain.

    > [!NOTE]
    > Use lowercase letters when you enter your tenant's name, even if the tenant is defined with uppercase letters in Microsoft Entra ID B2C. For example, enter `https://adventure-works.b2clogin.com/adventure-works.onmicrosoft.com/oauth2/authresp`.

1. Select **Register**.

:::image type="content" source="../media/obo-register-application2.png" alt-text="Screenshot of the registration of the Microsoft Entra B2B application." lightbox="../media/obo-register-application2.png":::

### [Microsoft Entra External ID](#tab/eeid)

To create a Microsoft Entra application for account manager sign-in in the Azure business-to-business (B2B) tenant, follow these steps:

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. Go to the directory that contains the Microsoft Entra business-to-business (B2B) tenant that you use for sign-in in headquarters.
1. In the row of Azure services, select **Microsoft Entra ID**.
1. On the **Manage** menu, select **App Registration**, and then select **New Registration**.
1. Enter a name for the application (for example, **Account Manager Employer Auth**).
1. Under **Supported account types**, select **Accounts in this organizational directory only (`<YOUR-TENANT-NAME>` only - Single tenant)**, where `<YOUR-TENANT-NAME>` is the name of your tenant.
1. Under **Redirect URI**, select **Web**, and then add the following redirect URLs:

    - `https://<EEID-tenant-subdomain>.ciamlogin.com/<EEID-tenant-ID>/federation/oauth2`
    - `https://<EEID-tenant-subdomain>.ciamlogin.com/<EEID-tenant-subdomain>.onmicrosoft.com/federation/oauth2`

    Replace `<EEID-tenant-subdomain>` with the subdomain of your **Microsoft Entra External ID (EEID) tenant** - This is the tenant where the consumer or customer user data resides, not the employee or B2B tenant. Replace `<EEID-tenant-ID>` with the EEID tenant's directory (tenant) ID. For example, if your EEID tenant subdomain is `contoso-customers` and the tenant ID is `aaaa1111-bb22-cc33-dd44-eeee5555ffff`, the redirect URIs would be `https://contoso-customers.ciamlogin.com/aaaa1111-bb22-cc33-dd44-eeee5555ffff/federation/oauth2` and `https://contoso-customers.ciamlogin.com/contoso-customers.onmicrosoft.com/federation/oauth2`.

    > [!NOTE]
    > Use lowercase letters when you enter your tenant's subdomain, even if the tenant is defined with uppercase letters in Microsoft Entra ID.

1. Select **Register**.

---

## Configure a Microsoft Entra application for account manager sign-in in the Azure B2B tenant

### [Azure AD B2C](#tab/azure-ad-b2c)

After you complete the registration, find the application that you created (for example, **Account Manager Application**).

1. In the **Essentials** section, copy and save the **Application (Client) ID** value. This value is a globally unique identifier (GUID) (for example, "00001111-aaaa-2222-bbbb-3333cccc4444").
1. Select **Add an Application ID URI**.
1. Select **Add a scope**. The portal generates an application ID URI for you.
1. Select **Save and continue**.
1. For **Scope name**, enter "user_impersonation".
1. For **Admin consent display name**, enter "obo user impersonation", or any other name.
1. For **Admin consent description**, enter "obo user impersonation", or any other description.
1. Select **Save**.
1. In the left menu, under **Manage**, select **Certificates & secrets**.
1. Select **New client secret**.
1. In the **Description** field, enter a description of the client secret (for example, "clientsecret1").
1. Under **Expires**, select the date when the secret expires.
1. Select **Add**.
1. Copy and save the secret value to use later.

    > [!IMPORTANT]
    > Make sure you copy the secret value. It doesn't appear again after you leave the **Certificates & secrets** page.

:::image type="content" source="../media/obo-add-scope2.png" alt-text="Screenshot of an example of adding a scope." lightbox="../media/obo-add-scope2.png":::

### [Microsoft Entra External ID](#tab/eeid)

After you complete the registration, find the application that you created (for example, **Account Manager Application**).

1. In the **Overview** section, copy and save the **Application (Client) ID** value. This value is a globally unique identifier (GUID) (for example, "00001111-aaaa-2222-bbbb-3333cccc4444").
1. In the left menu, under **Manage**, select **Certificates & secrets**.
1. Select **New client secret**.
1. In the **Description** field, enter a description of the client secret (for example, "clientsecret1").
1. Under **Expires**, select the date when the secret expires.
1. Select **Add**.
1. Copy and save the secret value to use later.

    > [!IMPORTANT]
    > Make sure you copy the secret value. It doesn't appear again after you leave the **Certificates & secrets** page.

---

## Configure an identity provider in your Azure B2C tenant for account manager sign-in to a B2B site

### [Azure AD B2C](#tab/azure-ad-b2c)

To configure an identity provider in your Azure B2C tenant for account manager sign-in to a B2B site, follow these steps:

1. Go to the directory that contains your Microsoft Entra B2C tenant. On the top menu, select the **Directory + subscription** filter, and then select the directory that contains your Microsoft Entra B2C tenant.
1. In the upper-left corner of the Azure portal, select **All services**. Search for and select **Microsoft Entra ID B2C**.
1. Select **Identity providers**, and then select **New OpenID Connect provider**.
1. In the **Name** field, enter **StoreManagerB2BSignin**. You must use this exact name; don't modify it.

    > [!IMPORTANT]
    > For on behalf of sign-in to work, the identity provider name must match the ID used in your sign-in module. The default value is **StoreManagerB2BSignin**.

1. In the **Metadata url** field, enter the URL of the Azure B2B OpenID Connect (OIDC) configuration document. For example, use `https://login.microsoftonline.com/<TENANT-ID>/v2.0/.well-known/openid-configuration`, where `<TENANT-ID>` is the ID of your Microsoft Entra B2B tenant.

    > [!IMPORTANT]
    > The OIDC configuration document URL must use HTTPS.

1. In the **Client ID** field, enter the application ID that you copied earlier.
1. In the **Client secret** field, enter the client secret that you copied earlier.
1. In the **Scope** field, enter `openid profile <Azure-B2B-Application-ID-URI>/user_impersonation`, where `<Azure-B2B-Application-ID-URI>` is the ID of the Azure B2B Microsoft Entra application. For example, use `openid profile api://00001111-aaaa-2222-bbbb-3333cccc4444/user_impersonation`. The **Scope** field format must be `openid profile <scope-name>`, where `<scope-name>` is the scope name you created in the [Create a Microsoft Entra application for account manager sign-in in the Azure B2B tenant](#create-a-microsoft-entra-application-for-account-manager-sign-in-in-the-azure-b2b-tenant) procedure.
1. In the **Response type** field, select **code**.
1. In the **Response mode** field, select **form_post**.  
1. Under **Identity provider claims mapping**, select the following claims:
    1. For **User ID**, select **sub**.
    1. For **Display name**, select **name**.
    1. For **Given name**, select **given_name**.
    1. For **Surname**, select **family_name**.
    1. For **Email**, select **email**.
1. Select **Save**.

### [Microsoft Entra External ID](#tab/eeid)

To configure your Microsoft Entra B2B tenant as a custom OpenID Connect (OIDC) identity provider in your external tenant, follow these steps:

1. On the Azure portal, go to the directory that contains your Microsoft Entra External ID tenant.
1. Browse to **Entra ID** > **External Identities** > **All identity providers**.
1. Select the **Custom** tab, and then select **Add new** > **Open ID Connect**.
1. In the **Display name** field, enter **StoreManagerB2BSignin** or a custom name for the OBO signin page.
1. In the **Well-known endpoint** field, enter the URL of the Azure B2B OpenID Connect (OIDC) configuration document. For example, use `https://login.microsoftonline.com/organizations/v2.0/.well-known/openid-configuration`.

    > [!IMPORTANT]
    > The OIDC configuration document URL must use HTTPS.

1. In the **OpenID Issuer URI** field, enter the issuer of your Microsoft Entra B2B tenant. For example, use `https://login.microsoftonline.com/<TENANT-ID>/v2.0`, where `<TENANT-ID>` is the ID of your Microsoft Entra B2B tenant.
1. In the **Client ID** field, enter the application ID that you copied earlier.
1. In the **Client secret** field, enter the client secret that you copied earlier.
1. For **Client authentication**, select **client_secret_post**.
1. In the **Scope** field, enter `openid profile`.
1. In the **Response type** field, select **code**.
1. Select **Next: Claims mapping**, and then map the following claims:
    1. For **Name**, replace value with **oid**.
1. Select **Review + create** to add your identity provider.

---

## Add the Azure identity provider to a user flow

### [Azure AD B2C](#tab/azure-ad-b2c)

To add the Azure identity provider to a user flow, follow these steps:

1. In your Microsoft Entra B2C tenant, select **User flows**.
1. Select the user flow that you want to add the identity provider to.
1. Under **Custom identity providers**, select the identity provider that you added in the [Create a Microsoft Entra application for account manager sign-in in the Azure B2B tenant](#create-a-microsoft-entra-application-for-account-manager-sign-in-in-the-azure-b2b-tenant) step.
1. In **Application Claims**, select **Identity Provider Access Token**, **Identity Provider**, **Email address**, **Given Name**, and **Surname**.
1. Select **Save**.

### [Microsoft Entra External ID](#tab/eeid)

To add the OIDC identity provider to a user flow, follow these steps:

1. In your external tenant, go to **Entra ID** > **External Identities** > **User flows**.
1. Select the user flow that's configured for sign-in or sign-up on your B2B e-commerce site.
1. Under **Settings**, select **Identity providers**.
1. Under **Other Identity Providers**, select the **StoreManagerB2BSignin** OIDC identity provider that you added in the [Configure an identity provider in your Azure B2C tenant for account manager sign-in to a B2B site](#configure-an-identity-provider-in-your-azure-b2c-tenant-for-account-manager-sign-in-to-a-b2b-site) step.
1. Select **Save**.
1. Under **Customize**, select **Page layouts**. On the **User Flow Attributes** tab, select the **username** attribute. In the **Edit Username** pane, clear the **Collect from user** and **Editable** checkboxes, and then select **OK**.

---

## Create an app registration that exposes the user impersonation scope

### [Azure AD B2C](#tab/azure-ad-b2c)

In Azure AD B2C, the user impersonation scope is exposed directly on the application you created in previous steps. It doesn't need any separate configuration.

### [Microsoft Entra External ID](#tab/eeid)

For Microsoft Entra External ID, the on behalf of (OBO) flow requires a separate Microsoft Entra application created in your external (EEID) tenant that exposes a user impersonation scope. You then grant the app registration used for sign-in into the site permission to that scope. To create this application and expose the scope, follow these steps:

1. On the Azure portal, go to the directory that contains your Microsoft Entra External ID tenant.
1. Go to **Entra ID** > **App registrations**, and then select **New registration**.
1. Enter a name for the application (for example, **OBO Impersonation AppReg**).
1. Under **Supported account types**, select **Accounts in this organizational directory only (`<YOUR-TENANT-NAME>` only - Single tenant)**, where `<YOUR-TENANT-NAME>` is the name of your external tenant.
1. Select **Register**.
1. In the **Essentials** section, copy and save the **Application (Client) ID** value. You need this value when you grant the scope to the sign-in application.
1. On the **Manage** menu, select **Expose an API**.
1. Next to **Application ID URI**, select **Add**, accept the generated URI (`api://<client-id>`), and then select **Save**.
1. Select **Add a scope**.
1. For **Scope name**, enter "user_impersonation".
1. For **Who can consent?**, select **Admins only**.
1. For **Admin consent display name**, enter "obo user impersonation", or any other name.
1. For **Admin consent description**, enter "obo user impersonation", or any other description.
1. For **State**, select **Enabled**.
1. Select **Add scope**.

---

## Add the user impersonation scope to the app registration used for sign-in into the site

### [Azure AD B2C](#tab/azure-ad-b2c)

In Azure AD B2C, the user impersonation scope is added directly on the OIDC provider in the previous steps. You don't need any separate configuration.

### [Microsoft Entra External ID](#tab/eeid)

After you expose the scope, grant it to the Microsoft Entra External ID app registration that the B2B ecommerce site uses for sign-in. To grant the scope, follow these steps:

1. In your external (EEID) tenant, go to **Entra ID** > **App registrations**, and then open the app registration used for sign-in into the site.
1. On the **Manage** menu, select **API permissions**.
1. Select **Add a permission**, and then select the **APIs my organization uses** tab.
1. Select the application that exposes the scope (for example, **OBO Impersonation AppReg**).
1. Select **Delegated permissions**, select the **user_impersonation** scope, and then select **Add permissions**.
1. Select **Grant admin consent for `<YOUR-TENANT-NAME>`**, and then select **Yes** to confirm. Verify that the **Status** column shows **Granted for `<YOUR-TENANT-NAME>`**.

---

## Add the user impersonation scope to the site authentication profile in Commerce site builder

### [Azure AD B2C](#tab/azure-ad-b2c)

This step isn't required for Azure AD B2C setup.

### [Microsoft Entra External ID](#tab/eeid)

You also need to add the scope to the site authentication profile that your site uses, so that the OBO token requested at sign-in includes the user impersonation scope. To add the scope, follow these steps:

1. In Commerce site builder, go to **Tenant settings** > **Site authentication setup**.
1. Select the site authentication profile that your site uses (for example, **EntraExternal**) to open the **Edit site authentication profile** dialog box.
1. In the **Scope** field, enter the user impersonation scope that you exposed earlier, in the format `api://<obo-api-client-id>/user_impersonation`, where `<obo-api-client-id>` is the **Application (Client) ID** of the app registration that exposes the scope (for example, **Account Manager OBO API**).
1. Select **OK**, and then select **Save**.

---

## More resources

- [Create and modify pages for on behalf of (OBO) functionality](obo-add-pages-site-builder.md)
- [Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)
- [Set up custom pages for user sign-ins](../custom-pages-user-logins.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
