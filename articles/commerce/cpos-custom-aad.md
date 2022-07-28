---
# required metadata

title: Configure CPOS to use custom Azure AD app
description: This article explains how to configure Cloud POS (CPOS) to use a custom Azure Active Directory (Azure AD) app.
author: boycez
ms.date: 07/28/2022
ms.topic: article
ms.prod:
ms.technology: 
# optional metadata
# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: boycez
ms.search.validFrom:
ms.dyn365.ops.version: 10.0.21
---

# Configure CPOS to use custom Azure AD app

[!include [banner](includes/banner.md)]

By default, Cloud POS (CPOS) in Dynamics 365 Commerce points to a registered first party Microsoft app in Azure Active Directory (Azure AD) so that you can use CPOS without making any changes in Azure AD. However, you may want to point your instance of CPOS to a custom Azure AD app that you control. This article describes the steps to configure CPOS to use a custom Azure AD app.

## Set up custom Retail Server app in Azure AD

To create and configure a custom Retail Server app in Azure AD, follow these steps.

1. Sign in to the [Azure Active Directory admin center](https://aad.portal.azure.com) with any Azure AD user account. The user account doesn't need to have administrator permissions.
1. Select **Azure Active Directory**.
1. Select **App registrations**, then select **New registration** to open the **Register an application** dialog. Enter values for the following fields.
    
    - **Name** – Enter a custom name for the app. For instance, “Custom Retail Server”.
    - **Support account types** – Select the default option **Accounts in this organizational directory only (Microsoft only - Single tenant)**.
    - **Redirect URI** - This field is optional. Leave it empty.
    - **Service Tree ID** - This field is optional. Leave it empty.
	
1. Select **Register**. The configuration page for the newly registered app opens.
1. In the **Overview \> Essentials** section, select **Add an Application ID URI**, then select **Set** next to **Application ID URI**. Make a note of the suggested value, and then select **Save** to accept the value. 
1. Select **Add a scope**, and then enter values for the following fields.

    - **Scope name** – Enter a custom name for the scope. For example, “Legacy.Access.Full”.
    - **Who can consent** – Determine whether both admins and users can accept or only admins, based on your organization’s security policies. Select the appropriate value.
    - **Admin consent display name** – Enter a display name. For example, “Access Retail Server”.
    - **Admin consent description** – Enter a description. For example, “Gives access to Retail Server APIs”.

1. Select **Add scope** to complete the scope creation process.

## Set up custom CPOS app in Azure AD

To create and configure a custom CPOS app in Azure AD, follow these steps.

1. Sign in to the [Azure Active Directory admin center](https://aad.portal.azure.com) with any Azure AD user account. The user account doesn't need to have administrator permissions.
1. Select **Azure Active Directory**.
1. Select **App registrations**, then select **New registration** to open the **Register an application** dialog. Enter values for the following fields.
    
    - **Name** – Enter a name for the app. For example, “Custom Cloud POS”.
    - **Support account types** – Select the default option **Accounts in this organizational directory only (Microsoft only - Single tenant)**.
    - **Redirect URI** - Select **Single-page application (SPA)** in the dropdown and then enter your CPOS URI.
    - **Service Tree ID** - This field is optional. Leave it empty.

1. Select**Register**.The configuration page for the newly registered app opens.
1. In the **Manifest** section, set the **oauth2AllowIdTokenImplicitFlow** and **oauth2AllowImplicitFlow** parameters to **true** , and then select **Save**. 
1. In the **Token configuration** section, follow the steps below to add two claims.

    - Select **Add optional claim**. Set **Token type** to **ID**, and then select the **sid** claim. Select **Add**.
    - Select **Add optional claim**. Set **Token type** to **Access**, and then select the **sid** claim. Select **Add**.

1. In the **API permissions** section, select **Add a permission**. Select the **APIs my organization uses** tab, and then search for the Retail Server app you created in the [Set up custom Retail Server app in Azure AD](#Set-up-custom-Retail-Server-app-in-Azure-AD) section. Select **Add permissions**.
1. Under "Overview" section, take a note of the value from the field **Application (client) ID**.

## Update CPOS config file

Open CPOS config.jason file and make the following updates in the file.

1. Locate the key **AADClientId**, and replace its value with the **Application (client) ID** of the **custom CPOS application** created in previous steps.
1. Locate the key **AADRetailServerResourceId**, and replace its value with the **Application ID URI** of the **custom Retail Server application** created in previous steps.

Both parameters above will be used by CPOS when it sends a request to AAD to acquire a security token.

## Update identity providers settings in Commerce headquarters

To update identify providers settings in Commerce headquarters, follow these steps.

1. Go to **Commerce shared parameters** form and select the **Identity Providers** tab.
1. In the **Identity providers** data grid, select the row with **Type** as **Azure Active Directory** and **Issuer** pointing to **your** AAD tenant. By selecting it you are declaring that you are going to work with child grids containing the data related to the identity provider corresponding to your AAD tenant.
1. In the **Relying parties** data grid, click **Add** to add a new row and fill out the followings.
    
    - For the **ClientId** cell, enter the **Application (client) ID** of the **custom CPOS application** created in previous steps. 
    - For the **Type** cell, select **Public**.
    - For the **UserType** cell, select **Worker**.

1. Select the newly added relying party row and then navigate to the **Server resource IDs** data grid, this one contains Retail Server application IDs allowed to be accessed by the selected application in the **Relying parties** grid. 
1. Click **Add** to add a new row, and fill out the **Server Resource Id** cell with the **Application ID URI** of the **custom Retail Server application** created in previous steps.

    > [!NOTE]
    > All the values entered into the data grids above are case sensitive and must match exact values configured in Azure Active Directory admin center.

1. Go to **Retail and Commerce IT \> Distribution schedule** and then execute the **1110** (**Global configuration**) job.

With all above configurations completed, you should now be able to activate CPOS devices with your own AAD application.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
