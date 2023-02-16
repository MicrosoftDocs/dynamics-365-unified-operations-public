---
# required metadata

title: Create and configure an Azure Active Directory application for account manager sign-in
description: This article describes how to create and configure an Azure Active Directory application for account manager sign-in for on behalf of functionality in Microsoft Dynamics 365 Commerce.
author:  mariash529
ms.date: 03/03/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: mashneer
ms.search.validFrom: 2023-02-27
ms.dyn365.ops.version: 10.0.33
---

# Create and configure an Azure Active Directory application for account manager sign-in

[!include[banner](../includes/banner.md)]

This article describes how to create and configure an Azure Active Directory (Azure AD) application for account manager sign-in for on behalf of functionality in Microsoft Dynamics 365 Commerce.

## Create an Azure AD application for account manager sign-in  

To create an Azure AD application for account manager sign-in, follow these steps.

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. Make sure you're using the directory that contains your Azure AD business-to-business (B2B) tenant that is being used for sign-in in headquarters.
1. In the row of Azure services, select **Azure Active Directory**.
1. In the **Manage** menu, select **App Registration**. Select **New Registrations**
1. Enter a Name for the application. For example, "Account Manager Employer Auth".
1. Under Supported account types, select **Accounts in any identity provider or organizational directory (for authenticating users with user flows)**
1. Under **Redirect URI**, select **Web**, and then enter `https://your-tenant-name.b2clogin.com/your-tenant-name.onmicrosoft.com/oauth2/authresp` in the URL text box. If you use a custom domain, enter `https://your-domain-name/your-tenant-name.onmicrosoft.com/oauth2/authresp` instead. Replace your-tenant-name with the name of your tenant, and your-domain-name with your custom domain. Use lowercase letters when entering your tenant’s name even if the tenant is defined with uppercase letters in Azure AD B2C. For example, `https://fabrikam-online.b2clogin.com/fabrikam-online.onmicrosoft.com/oauth2/authresp`.
1. Under **Permissions**, select the **Grant admin consent to openid and offline access permissions** option.
1. Select **Register**.
1. After registration is completed, you'll be redirected to the Azure AD B2C - App registrations page for the application you created, for example "Account Manager Employer Auth".
1. Capture and save **Application (Client) ID** GUID that is displayed in **Essentials** section. 
1. In the left menu, under **Manage**, select **Certificates & secrets**.
1. Select **New client secret**.
1. For **Description**, enter a description for the client secret (for example, "clientsecret1").
1. Under **Expires**, select a duration for which the secret is valid, and then select **Add**.
1. Record the secret's **value** for use in your client application code. Note, this secret value is never displayed again after you leave this page. You'll use this value as the application secret in your application's code.

## Configure an identity provider in your Azure B2C tenant for account manager sign-in to a B2B site

To configure an identity provider in your Azure B2C tenant for account manager sign-in to a B2B site, follow these steps.

1. Make sure you're using the directory that contains Azure AD B2C tenant. Select the **Directory + subscription** filter in the top menu and choose the directory that contains your **Azure AD B2C tenant**.
1. Choose **All services** in the top-left corner of the Azure portal, and then search for and select **Azure AD B2C**.
1. Select Identity providers, and then select **New OpenID Connect provider**.
1. Enter a Name. Name must be **Account Manager B2B Sign-in**.
1. For **Metadata URL**, enter the URL of the Azure B2B OpenID Connect Configuration document, for example, https://login.microsoftonline.com/TENANTID/v2.0/.well-known/openid-configuration The URL must be HTTPS. 
1. For **Client ID**, enter the application ID that you previously recorded.
1. For **Client secret**, enter the client secret that you previously recorded.
1. For **Scope**, enter the openid profile Azure B2B Application ID URI (for example, `https://APPLICATIONIDURI`). This should be the application ID URI of Azure B2B Azure AD application.
1. For **Response Mode**, select **form_post**.
1. For **Response Type**, select **code**.
1. Under **Identity provider claims mapping**, select the following claims:
    1. **User ID:** sub
    1. **Display name:** name
    1. **Given name:** given_name
    1. **Surname:** family_name
    1. **Email:** email
1. Select **Save**.

## Add the Azure identity provider to a user flow

To add the Azure identity provider to a user flow, follow these steps.

1. In your Azure AD B2C tenant, select **User flows**.
1. Select the user flow for which you want to add the identity provider.
1. Under the **Custom identity providers**, select the identity provider you added. For example, "Account Manager B2B Sign-in".
1. Select **Save**.

## Additional resources

[Set up a B2C tenant in Commerce](set-up-b2c-tenant.md)

[Set up custom pages for user sign-ins](custom-pages-user-logins.md)

