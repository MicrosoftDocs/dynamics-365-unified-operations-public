---
# required metadata

title: Create and configure an Azure Active Directory application for account manager sign-in
description: This article describes how to create and configure an Azure Active Directory application for account Manager sign-in for On Behalf Of functionality.
author:  mariash529
ms.date: 02/27/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: mashneer
ms.search.validFrom: 2023-02-27
ms.search.form:
ms.dyn365.ops.version:
---

# Create and configure an Azure Active Directory application for account manager sign-in

[!include[banner](../includes/banner.md)]

This article describes how to create an Azure Active Directory application for account manager Sign-in for On Behalf Of functionality in Dynamics 365 Commerce.

## Create an Azure Active Directory application for account manager sign-in:   

To enable sign-in for account manager with an employee’s AAD account in Azure Active Directory:

1.	Sign in to the [Azure portal](https://portal.azure.com/).
1.	Make sure you are using the directory that contains your Azure AD B2B tenant which is being used for sign-in in HQ.
1.	In the row of Azure services, click on **Azure Active Directory**.
1.	In the “Manage” menu, click **App Registration**. Click **New Registrations**
1.	Enter a Name for the application. For example, “Account Manager Employer Auth”.
1.  Under Supported account types, select **Accounts in any identity provider or organizational directory (for authenticating users with user flows)**
1.  Under **Redirect URI**, select **Web**, and then enter https://your-tenant-name.b2clogin.com/your-tenant-name.onmicrosoft.com/oauth2/authresp in the URL text box.If you use a custom domain, enter https://your-domain-name/your-tenant-name.onmicrosoft.com/oauth2/authresp. Replace your-tenant-name with the name of your tenant, and your-domain-name with your custom domain. Use lowercase letters when entering your tenant’s name even if the tenant is defined with uppercase letters in Azure AD B2C. For example, “https://fabrikam-online.b2clogin.com/fabrikam-online.onmicrosoft.com/oauth2/authresp”.
1.  Under Permissions, select the **Grant admin consent to openid and offline access permissions** option.
1.	Click **Register**.
1.	After registration is completed, you will be redirected to the In the Azure AD B2C - App registrations page, with the application you created, for example “Account Manager Employer Auth”.
1.	Capture and save **Application (Client) ID** GUID that is displayed in Essentials section. 
1.	In the left menu, under Manage, select **Certificates & secrets**.
1.	Select **New client secret**.
1.	Enter a **description** for the client secret in the Description box. For example, clientsecret1.
1.	Under Expires, select a duration for which the secret is valid, and then select **Add**.
1.	Record the secret's Value for use in your client application code. Note, this secret value is never displayed again after you leave this page. You will use this value as the application secret in your application's code.

## Configure an identity provider in Azure B2C tenant for account manager sign-in for B2B site
1.	Make sure you're using the directory that contains Azure AD B2C tenant. Select the **Directory + subscription** filter in the top menu and choose the directory that contains your **Azure AD B2C tenant**.
1.	Choose **All services** in the top-left corner of the Azure portal, and then search for and select **Azure AD B2C**.
1.	Select Identity providers, and then select **New OpenID Connect provider**.
1.	Enter a Name. Name must be **Account Manager B2B Sign-in**.
