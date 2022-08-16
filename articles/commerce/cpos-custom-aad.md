---
# required metadata

title: Configure CPOS to use a custom Azure AD app
description: This article explains how to configure Cloud POS (CPOS) to use a custom Azure Active Directory (Azure AD) app.
author: boycez
ms.date: 08/02/2022
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

# Configure CPOS to use a custom Azure AD app

[!include [banner](includes/banner.md)]

By default, Cloud POS (CPOS) in Microsoft Dynamics 365 Commerce points to a registered first-party Microsoft app in Azure Active Directory (Azure AD). Therefore, you can use CPOS without having to make any changes in Azure AD. However, you might want to point your instance of CPOS to a custom Azure AD app that you control. This article explains how to configure CPOS to use a custom Azure AD app.

## Set up a custom Retail Server app in Azure AD

To create and configure a custom Retail Server app in Azure AD, follow these steps.

1. Sign in to the [Azure Active Directory admin center](https://aad.portal.azure.com) by using any Azure AD user account. The user account doesn't have to have administrator permissions.
1. Select **Azure Active Directory**.
1. Select **App registrations**, and then select **New registration** to open the **Register an application** dialog box.
1. Set the following fields:

    - **Name** – Enter a custom name for the app. For example, enter **Custom Retail Server**.
    - **Support account types** – Select the default option, **Accounts in this organizational directory only (Microsoft only - Single tenant)**.
    - **Redirect URI** – This field is optional. Leave it blank.
    - **Service Tree ID** – This field is optional. Leave it blank.
	
1. Select **Register**. The configuration page for the newly registered app appears.
1. In the **Overview \> Essentials** section, select **Add an Application ID URI**, and then select **Set** next to **Application ID URI**. Make a note of the suggested value, and then select **Save** to accept that value. 
1. Select **Add a scope**, and then set the following fields:

    - **Scope name** – Enter a custom name for the scope. For example, enter **Legacy.Access.Full**.
    - **Who can consent** – Specify whether both admins and users or only admins can give consent, based on your organization's security policies.
    - **Admin consent display name** – Enter a display name. For example, enter **Access Retail Server**.
    - **Admin consent description** – Enter a description. For example, enter **Gives access to Retail Server APIs**.

1. Select **Add scope** to complete the scope creation process.

## Set up a custom CPOS app in Azure AD

To create and configure a custom CPOS app in Azure AD, follow these steps.

1. Sign in to the [Azure Active Directory admin center](https://aad.portal.azure.com) by using any Azure AD user account. The user account doesn't have to have administrator permissions.
1. Select **Azure Active Directory**.
1. Select **App registrations**, and then select **New registration** to open the **Register an application** dialog box.
1. Set the following fields:

    - **Name** – Enter a name for the app. For example, enter **Custom Cloud POS**.
    - **Support account types** – Select the default option, **Accounts in this organizational directory only (Microsoft only - Single tenant)**.
    - **Redirect URI** – Select **Single-page application (SPA)** in the drop-down list, and then enter your CPOS URI.
    - **Service Tree ID** – This field is optional. Leave it blank.

1. Select **Register**. The configuration page for the newly registered app appears.
1. In the **Manifest** section, set the **oauth2AllowIdTokenImplicitFlow** and **oauth2AllowImplicitFlow** parameters to **true**, and then select **Save**.
1. In the **Token configuration** section, follow these steps to add two claims:

    - Select **Add optional claim**. Set the **Token type** field to **ID**, and then select the **sid** claim. Select **Add**.
    - Select **Add optional claim**. Set the **Token type** field to **Access**, and then select the **sid** claim. Select **Add**.

1. In the **API permissions** section, select **Add a permission**.
1. On the **APIs my organization uses** tab, search for the Retail Server app that you created in the [Set up a custom Retail Server app in Azure AD](#set-up-a-custom-retail-server-app-in-azure-ad) section. Then select **Add permissions**.
1. In the **Overview** section, make a note of the value in the **Application (client) ID** field.

## Update the CPOS configuration file

Open the CPOS config.json file, and make the following updates in it.

1. Replace the **AADClientId** key value with the **Application (client) ID** value of the custom CPOS app that you created in the [Set up a custom CPOS app in Azure AD](#set-up-a-custom-cpos-app-in-azure-ad) section.
1. Replace the **AADRetailServerResourceId** key value with the **Application ID URI** value of the custom Retail Server app that you created in the [Set up a custom Retail Server app in Azure AD](#set-up-a-custom-retail-server-app-in-azure-ad) section.

CPOS will use both parameters when it sends requests to Azure AD to acquire a security token.

## Update identity providers settings in Commerce headquarters

Next, you must update identity providers settings in Commerce headquarters.

1. In Commerce headquarters, open the **Commerce shared parameters** page.
1. On the **Identity Providers** tab, in the **Identity providers** section, select the row where the **Type** field is set to **Azure Active Directory** and the **Issuer** field points to your Azure AD tenant. This setting declares that you will work with child grids that contain the data that is related to the identity provider that corresponds to your Azure AD tenant.
1. In the **Relying parties** section, select **Add** to add a row.
1. Set the following fields:

    - **ClientId** – Enter the **Application (client) ID** value of the custom CPOS app that you created in the [Set up a custom CPOS app in Azure AD](#set-up-a-custom-cpos-app-in-azure-ad) section.
    - **Type** – Select **Public**.
    - **UserType** – Select **Worker**.

1. Select the row that you added. The **Server Resource IDs** section below the **Relying Parties** section shows the Retail Server app IDs that can be accessed by the app that you selected in the **Relying Parties** grid.
1. In the **Server Resource IDs** section, select **Add** to add a row.
1. In the **Server Resource Id** field, enter the **Application ID URI** value of the custom Retail Server app that you created in the [Set up a custom Retail Server app in Azure AD](#set-up-a-custom-retail-server-app-in-azure-ad) section.

    > [!IMPORTANT]
    > All the fields that are mentioned in the preceding steps are case-sensitive. The values that you enter must exactly match the values that are configured in the Azure AD admin center.

1. Go to **Retail and Commerce IT \> Distribution schedule**, and run the **1110** (**Global configuration**) job.

You can now activate CPOS devices by using your own Azure AD app.

## Additional resources

[Point of sale (POS) device activation](dev-itpro/retail-device-activation.md)

[Manage activation accounts and validate devices](set-up-activation-accounts-validate-devices-hq.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
