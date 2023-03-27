---
# required metadata

title: Configure Store Commerce for web to use a custom Azure AD app
description: This article explains how to configure Microsoft Dynamics 365 Commerce Store Commerce for web to use a custom Azure Active Directory (Azure AD) app.
author: boycez
ms.date: 01/30/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: global
ms.author: boycez
ms.search.validFrom: 2017-06-20

---

# Configure Store Commerce for web to use a custom Azure AD app

[!include [banner](includes/banner.md)]

This article explains how to configure Microsoft Dynamics 365 Commerce Store Commerce for web to use a custom Azure Active Directory (Azure AD) app

By default, Store Commerce for web points to a registered first-party Microsoft app in Azure Active Directory (Azure AD). Therefore, you can use Store Commerce for web without having to make any changes in Azure AD. However, you might want to point your instance of Store Commerce for web to a custom Azure AD app that you control. This article explains how to configure Store Commerce for web to use a custom Azure AD app. 

> [!NOTE] 
> This article only applies to self-hosted Commerce Scale Unit (CSU) installations or development using a self-hosted CSU. 


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

## Set up a custom app for Store Commerce for web in Azure AD

> [!IMPORTANT]
> If you're upgrading an existing custom Store Commerce for web Azure AD app that was created before Commerce version 10.0.21, follow the steps in [Upgrade an existing custom Store Commerce for web Azure AD app created before Commerce version 10.0.21](#upgrade-an-existing-custom-store-commerce-for-web-azure-ad-app-created-before-commerce-version-10021).

To create and configure a custom app for Store Commerce for web in Azure AD, follow these steps.

1. Sign in to the [Azure Active Directory admin center](https://aad.portal.azure.com) by using any Azure AD user account. The user account doesn't have to have administrator permissions.
1. Select **Azure Active Directory**.
1. Select **App registrations**, and then select **New registration** to open the **Register an application** dialog box.
1. Set the following fields:

    - **Name** – Enter a name for the app. For example, enter **Custom Store Commerce for web**.
    - **Support account types** – Select the default option, **Accounts in this organizational directory only (Microsoft only - Single tenant)**.
    - **Redirect URI** – Select **Single-page application (SPA)** in the drop-down list, and then enter your Cloud POS URL.
    - **Service Tree ID** – This field is optional. Leave it blank.

1. Select **Register**. The configuration page for the newly registered app appears.
1. In the **Manifest** section, set the **oauth2AllowIdTokenImplicitFlow** and **oauth2AllowImplicitFlow** parameters to **true**, and then select **Save**.
1. In the **Token configuration** section, follow these steps to add two claims:

    1. Select **Add optional claim**. Set the **Token type** field to **ID**, and then select the **sid** claim. Select **Add**.
    1. Select **Add optional claim**. Set the **Token type** field to **Access**, and then select the **sid** claim. Select **Add**.

1. In the **API permissions** section, select **Add a permission**.
1. On the **APIs my organization uses** tab, search for the Retail Server app that you created in the [Set up a custom Retail Server app in Azure AD](#set-up-a-custom-retail-server-app-in-azure-ad) section. Then select **Add permissions**.
1. In the **Overview** section, make a note of the value in the **Application (client) ID** field.

### Upgrade an existing custom Store Commerce for web Azure AD app created before Commerce version 10.0.21

To upgrade an existing custom Store Commerce for web Azure AD app created before Commerce version 10.0.21, follow these steps. 

1. Open your custom Store Commerce for web Azure AD app in the Azure portal.
1. Select the **Authentication** tab.
1. Copy and save the original redirect URI from the **Web** type for use later, and then delete it.
1. Select **Add a platform**, and then select **Single-page application (SPA)**.
1. Add the original web redirect URI copied above to the SPA platform.
1. In the **Token configuration** section, follow these steps to add two claims:
    1. Select **Add optional claim**. Set the **Token type** field to **ID**, and then select the **sid** claim. Select **Add**.
    1. Select **Add optional claim**. Set the **Token type** field to **Access**, and then select the **sid** claim. Select **Add**.

## Update the Store Commerce for web configuration file

The following steps only apply to a CSU (self-hosted) that uses the Retail SDK. If you are using a sealed CSU installer, this process is completed automatically during the installation process. Open the Store Commerce for web config.json file, and make the following changes.

1. Replace the **AADClientId** key value with the **Application (client) ID** value of the custom Store Commerce for web app that you created in the [Set up a custom Store Commerce for web app in Azure AD](#set-up-a-custom-app-for-store-commerce-for-web-in-azure-ad) section.
1. Replace the **AADRetailServerResourceId** key value with the **Application ID URI** value of the custom Retail Server app that you created in the [Set up a custom Retail Server app in Azure AD](#set-up-a-custom-retail-server-app-in-azure-ad) section.

Store Commerce for web will use both parameters when it sends requests to Azure AD to acquire a security token.

## Update identity providers settings in Commerce headquarters

Next, you must update identity providers settings in Commerce headquarters.

1. In Commerce headquarters, open the **Commerce shared parameters** page.
1. On the **Identity Providers** tab, in the **Identity providers** section, select the row where the **Type** field is set to **Azure Active Directory** and the **Issuer** field points to your Azure AD tenant. This setting declares that you'll work with child grids that contain the data that's related to the identity provider that corresponds to your Azure AD tenant.
1. In the **Relying parties** section, select **Add** to add a row.
1. Set the following fields:

    - **ClientId** – Enter the **Application (client) ID** value of the custom Store Commerce for web app that you created in the [Set up a custom Store Commerce for web app in Azure AD](#set-up-a-custom-app-for-store-commerce-for-web-in-azure-ad) section.
    - **Type** – Select **Public**.
    - **UserType** – Select **Worker**.

1. Select the row that you added. The **Server Resource IDs** section below the **Relying Parties** section shows the Retail Server app IDs that can be accessed by the app that you selected in the **Relying Parties** grid.
1. In the **Server Resource IDs** section, select **Add** to add a row.
1. In the **Server Resource Id** field, enter the **Application ID URI** value of the custom Retail Server app that you created in the [Set up a custom Retail Server app in Azure AD](#set-up-a-custom-retail-server-app-in-azure-ad) section.

    > [!IMPORTANT]
    > All the fields that are mentioned in the preceding steps are case-sensitive. The values that you enter must exactly match the values that are configured in the Azure AD admin center.

1. Go to **Retail and Commerce IT \> Distribution schedule**, and run the **1110** (**Global configuration**) job.

You can now activate Store Commerce for web devices by using your own Azure AD app.

## Additional resources

[Point of sale (POS) device activation](dev-itpro/retail-device-activation.md)

[Manage activation accounts and validate devices](set-up-activation-accounts-validate-devices-hq.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
