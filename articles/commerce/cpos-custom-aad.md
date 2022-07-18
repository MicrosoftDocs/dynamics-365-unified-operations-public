---
# required metadata

title: Configure Cloud POS to use custom Azure AD application
description: This article explains how to configure Cloud POS to use custom AAD application.
author: boycez
ms.date: 07/18/2022
ms.topic: article
ms.prod:
ms.technology: 
# optional metadata
# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: boycez
ms.search.validFrom:
ms.dyn365.ops.version: 10.0.21
---

# Configure Cloud POS to use custom Azure AD application

[!include [banner](includes/banner.md)]

The out-of-the-box Cloud POS is pointing to the pre-registered Microsoft first party application in Azure Active Directory (AAD). This way anyone can just start using it without making any changes in AAD which is convenient. However, there could be circumstances which you might want to point your instance of CPOS to the custom AAD application you control. This article describes the required configuration steps to achieve that.

## Set up custom Retail Server application in AAD

To create and configure a custom Retail Server application in AAD, follow these steps.

1. Login into [Azure Active Directory admin center](https://aad.portal.azure.com) with any AAD user account. The user doesn't have to be an administrator of any kind.
1. Click **Azure Active Directory** on the navigation pane.
1. Click **App registrations**, then click **New registration** to open the **Register an application** dialog. Provide values for the following fields.
    
    - **Name** – Enter a custom name for the application. For instance, “Custom Retail Server”.
    - **Support account types** – Select the default option **Accounts in this organizational directory only (Microsoft only - Single tenant)**.
    - **Redirect URI** - Optional field, leave it as blank.
    - **Service Tree ID** - Optional field, leave it as blank.
	
1. Click the **Register** button, which opens the configuration page for the newly registered application.
1. Under **Overview \> Essentials** section, click the **Add an Application ID URI** link, then click **Set** besides the “Application ID URI”, take a note of the suggested value, and then click **Save** to accept the value. 
1. Click **Add a scope** and provide values for the following fields:

    - **Scope name** – Enter a custom name for the scope. For instance, “Legacy.Access.Full”.
    - **Who can consent** – Based on your organization’s security policies, decide if both admins and users can accept or only admins can, then make proper selection.
    - **Admin consent display name** – Enter the display name of the consent. For instance, “Access Retail Server”.
    - **Admin consent description** – Enter the description of the consent. For instance, “Gives access to Retail Server APIs”.

1. Click the **Add scope** button to complete the scope creation.

## Set up custom CPOS application in AAD

To create and configure a custom CPOS application in AAD, follow these steps.

1. Login into [Azure Active Directory admin center](https://aad.portal.azure.com) with any AAD user account. The user doesn't have to be an administrator of any kind.
1. Click **Azure Active Directory** on the navigation pane.
1. Click **App registrations**, then click **New registration** to open the **Register an application** dialog. Provide values for the following fields.
    
    - **Name** – Enter a custom name for the application. For instance, “Custom Cloud POS”.
    - **Support account types** – Select the default option **Accounts in this organizational directory only (Microsoft only - Single tenant)**.
    - **Redirect URI** - Select **Single-page application (SPA)** in the dropdown and enter your CPOS URI in the input box.
    - **Service Tree ID** - Optional field, leave it as blank.

1. Click the **Register** button, which opens the configuration page for the newly registered application.
1. Under **Manifest** section, set **oauth2AllowIdTokenImplicitFlow** and **oauth2AllowImplicitFlow** parameters to **true** , and then click **Save** to save the changes. 
1. Under **Token configuration** section, following the steps below to add two claims.

    - Click **Add optional claim**. In the prompt dialog, set **Token type** to **ID**, and then select the **sid** claim. Click **Add** button.
    - Click **Add optional claim**. In the prompt dialog, set **Token type** to **Access**, and then select the **sid** claim. Click **Add** button.

1. Under **API permissions** section, click **Add a permission**. In the prompt dialog, select **APIs my organization uses** tab, then type and search the Retail Server application you created in the previous steps (“Customized Retail Server”), and click **Add permissions**.
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
