---
title: Set up a Microsoft Entra External ID for user site authentication in Commerce e-commerce
description: Learn how to set up a Microsoft Entra External ID for user site authentication in Microsoft Dynamics 365 Commerce e-commerce.
author: AditiPattanaik
ms.date: 11/07/2025
ms.topic: how-to
ms.search.region: Global
ms.author: adpattanaik
ms.search.validFrom: 2025-11-06
ms.custom: 
  - bap-template
---

# Set up a Microsoft Entra External ID for user site authentication

[!include [banner](../includes/banner.md)]

This article explains how to set up your Microsoft Entra External ID tenant for user site authentication in Microsoft Dynamics 365 Commerce.

Starting with version 10.0.45, Dynamics 365 Commerce e-commerce supports Microsoft Entra External ID, Microsoft's next-generation Customer Identity and Access Management (CIAM) solution. This enhancement ensures a modern, secure, and scalable identity experience for business-to-consumer (B2C) and business-to-business (B2B) scenarios.

> [!NOTE] 
> After the end of sale for Azure AD B2C, existing Azure AD B2C tenants continue to be supported until May 2030, with no new feature development. New deployments must be provisioned using Microsoft Entra External ID, because Azure AD B2C is no longer available for new tenants.

## Prerequisites to enable Microsoft Entra External ID in Commerce

Before you begin, you must first submit a request to the Commerce team to enable the feature flight, and then perform the following steps to create and enable Microsoft Entra External ID tenant user authentication. 

## Create a Microsoft Entra external tenant on Azure 

This section describes how to create a Microsoft Entra External tenant in the Microsoft Azure portal. Learn more in [Create a new tenant with external configurations](/entra/external-id/customers/quickstart-tenant-setup#create-a-new-tenant-with-external-configurations).

To create a Microsoft Entra External ID tenant in the Azure portal, follow these steps.

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. On the Azure portal page, under **Azure Services**, select **Create a resource**. Be sure to use the subscription and directory that you connect with your Commerce environment.
1. Go to **Identity \> Microsoft Entra External ID**.  
1. On the **Basics** tab, on the **Create a tenant** page, enter the following information.
    1. For **Tenant Name**, enter the tenant name (for example, "Contoso Customers").
    1. For **Domain Name** (for example, "Contosocustomers").
    1. For **Location**, select your geographic location. Ensure that it's correct, because you can't change this selection later.  
1. Select **Next: Add a subscription**.  
1. On the **Add a subscription** tab, enter the following information.
    1. For **Subscription**, select your subscription.
    1. For **Resource group**, select a resource group. If there are no available resource groups, select **Create new**, add a name, and then select **OK**.
    1. If **Resource group location** appears, select the geographic location of the resource group.
1. Select **Next: Review + create**.
1. If the information you entered is verified as correct, select **Create**. The tenant creation process can take up to 30 minutes. You can monitor the progress of the tenant creation process in the **Notifications** pane. Once the tenant is created, you can access it in both the Microsoft Entra administrator center and the Azure portal.

## Create a Microsoft Entra External ID application

After you create your External ID tenant, next you create an application within your new Microsoft Entra tenant to interact with Commerce.

To create the application, follow these steps.

1. In the Azure portal, navigate to the tenant you created.
1. Select **App registrations**, and then select **New registration**.
1. Under **Name**, enter the name for this application.
1. Under **Supported account types**, select **Accounts in this organizational directory only (&lt;Tenant Name&gt; only - Single tenant)**.
1. For **Redirect URI**, enter your dedicated reply URLs as type **Web**. For information on reply URLs and how to format them, see [Reply URLs](set-up-external-entra-id.md#reply-urls). A redirect URI/reply URL must be entered to enable redirections from Microsoft Entra External ID back to your site when a user authenticates. The reply URLs can be added during the registration process, or can be added later. To add reply URLs later, in the External ID application's **App Registration \> Manage \> Authentication** menu, in the **Web Redirect URIs** section, select **Add URI**.
1. Select **Register**.
1. Select the application you created, and then navigate to the **Authentication** menu.
1. If you entered a reply URL, under **Implicit grant and hybrid flows**, select both the **Access tokens** and **ID tokens** options to enable them for the application, and then select **Save**. You're now able to select both the **Access tokens** and **ID tokens** options. If a reply URL wasn't entered during registration, you can add on this page by selecting **Add a platform**, selecting **Web**, and then entering the redirect URI of the application.
1. On the **API Permissions** menu, add the following Microsoft graph permissions.
    - **email**
    - **offline_access**
    - **openid**
    - **profile**
    - **User.ReadWrite**
1. Select **Grant admin consent for &lt;TenantName&gt;**.
1. On the **Token Configuration** menu, select **Add optional claim**.
1. In the sidebar that opens, under **Token Type** select **ID**, and then under **Claims**, select **Family_name** and **Given_name**, and then select **Add**.  
1. Go to the **Overview** menu of the Azure portal and copy the **Application (client) ID**. Make a note of this ID (referenced later as the **Client GUID**) for use in later setup steps.

## Reply URLs

Reply URLs are important because they provide an allow list of the return domains when your site calls Microsoft Entra External ID to authenticate a user. This process permits the return of an authenticated user back to the domain from which they're signing into (your site domain).

On the **Microsoft Entra External ID - Applications \> New application** screen, in the **Reply URL** box, you must add separate lines for both your site domain and (once your environment is provisioned) the Commerce-generated URL. These URLs must always use a valid URL format and must be base URLs only, with no trailing forward slashes or paths. Next you must append the `\_msdyn365/authresp` string to the base URLs, as shown in the following examples.

- `https://www.fabrikam.com/_msdyn365/authresp` (The domain should match the e-commerce domain exactly. If you have multiple domains, you must add this URL for each domain.)
- `https://fabrikam-prod.commerce.dynamics.com/_msdyn365/authresp`

## Create user flow

User flows are the policies Microsoft Entra External ID uses to provide secure sign in, sign up, and forget password user experiences. Dynamics 365 Commerce uses these flows to perform the actions to interact with the Microsoft Entra External ID tenant. When a user interacts with these flows, they're redirected to the Microsoft Entra External ID tenant to perform the actions.

Currently, Microsoft Entra External ID only supports one type of flow, which is used for sign in, sign up, and password reset.

For information on customizing the default branding in user flows, see [Customize the neutral branding in your external tenant](/entra/external-id/customers/how-to-customize-branding-customers).

> [!NOTE] 
> Customizing the login screen further currently involves using [Native authentication in Microsoft Entra External ID](/entra/identity-platform/concept-native-authentication). Modules can be built to interact with these APIs directly.


To create user flow in External ID, follow these steps:

1. In the Microsoft Entra External ID tenant, navigate to **Microsoft Entra ID**.
1. On the left navigation pane, select the **External Identities** menu.
1. On the left navigation pane, under **Self-service signup**, select **User flows**.  
1. Select **+ New user flow.**
1. Under **Name**, enter a policy name.
1. Under **Identity providers**, select an identity provider.
1. Under **User attributes** select the user attributes to be collected during signup. You must select the mandatory **Email address**, **Given Name**, and **Surname** attributes for correct implementation and functionality of the policies.
1. Select **Create**.

## Update Commerce headquarters with the new Microsoft Entra External ID information

To update headquarters with the new Microsoft Entra External ID information, follow these steps.

1. In Commerce, go to **Commerce Shared Parameters**.
1. In the left navigation pane, select **Identity Providers**.
1. Under **Identity Providers**, for **Issuer**, enter the identity provider issuer string. For information on how to find your issuer string, see [Obtain issuer string for headquarters setup](set-up-external-entra-id.md#obtain-issuer-string-for-headquarters-setup).
1. For **Name**, enter a name for your issuer record.
1. For **Type**, enter "Open ID Connect".
1. Under **Relying Parties**, with the Microsoft Entra External ID identity provider selected, for **ClientID**, enter the Microsoft Entra External ID application ID you created in [Create a Microsoft Entra External ID application](set-up-external-entra-id.md#create-a-microsoft-entra-external-id-application).
1. For **Type**, enter "Public".
1. For **User Type**, enter "Customer".
1. On the action pane, select **Save**.
1. In the Commerce search box, search for "Distribution schedules".
1. On the left navigation pane of the **Distribution schedules** page, select **Job 1110 Global configuration**.
1. On the action pane, select **Run Now**.

### Obtain issuer string for headquarters setup

To obtain your identity provider issuer string, follow these steps.

1. Go to the Azure portal.
1. On the **Microsoft Entra External ID** page, navigate to your user flow.
1. In the **Overview section**, select **Run user flow**.
1. Confirm that you set the application to the intended Microsoft Entra External ID you created, and then under the **Run user flow** header, select the user flow link that includes `.../.well-known/openid-configuration?appid=<Application_ID>`. Don't select **Run user flow**. A new tab opens that displays the metadata for the policy to collect the issuer string.
1. On the metadata page displayed in your browser tab, copy the identity provider issuer string value that starts with `https://` and ends with `/v2.0/`. It should look similar to the following example:

    `https://ab12cd34ef56-9999-4bbb-846d-ed4b0283d8d7.ciamlogin.com/ab12cd34ef56-9999-4bbb-846d-ed4b0283d8d7/v2.0`.

### Set up an authentication profile in Commerce Site Builder

To set up an authentication profile in Commerce Site Builder, follow these steps.

1. In Commerce Site Builder, go to **Tenant settings** \> **Site authentication setup**.
1. Select **Manage**.
1. On the right flyout pane, select **Add site authentication profile**.

1. For **Application Name**, enter a name for the authentication profile.
1. For **Tenant Name**, enter the name of the Microsoft Entra External ID tenant you created in the Azure portal.
1. For **Client GUID**, enter the GUID of the app registration associated with the sign-in/sign-up user flow.

    > [!NOTE]
    > Once the authentication profile is created, it becomes available for use.

1. Go to **Site settings** \> **Channels**.
1. Select the channel where you want to update your authentication.
1. Select the authentication profile you created.
1. Save and publish your changes.

The Microsoft Entra External ID authentication setup is now complete and active for your site.

## Edit profile page configuration

Microsoft Entra External ID doesn't support custom HTML pages. By default, Microsoft Entra External ID only supports the edit profile page when it's associated with the "/editprofile" URL endpoint. You must create a new URL for the edit profile page with the **/editprofile** endpoint.

To create a new URL for the edit profile page with the "/editprofile" endpoint, follow these steps.

1. Go to **URLs** \> and select **+ New**.
1. On the **Create new URL** flyout, create a new URL with the "/editprofile" endpoint.
1. Select **Next**, and on the **Select a page** flyout pane, select **Profile edit**, and then select **Create**.
1. Save and publish your changes.
    > [!NOTE]
    > Modules changes supporting EEID are present in SSK version 9.55.8. Ensure you reference this version or later for full compatibility with Entra External ID features.
## Updates to the Account-Profile-Edit Module (Online SDK) 


With Azure Active Directory B2C, implementing profile editing required only an HTML page that followed a specific contract. Azure Active Directory B2C itself handled the actual rendering of the edit profile page.

With Microsoft Entra External ID, this approach isn't supported. To address this issue, the account-profile-edit module is enhanced to provide edit profile functionality directly within the Commerce environment, which removes the dependency on Microsoft Entra External ID for rendering. As a result, the module supports profile updates for both Azure Active Directory B2C and Microsoft Entra External ID environments.

When External Entra ID is enabled, the following changes are made to allow a profile update via the OneRF API in account-profile-edit module.

- **account-profile-edit.tsx**: New state variables and methods are added (for example, useEntraExternalId, \_renderEntraExternalIdAccount, \_handleOneRFSave) to manage External Entra ID logic and OneRF API calls.
- **account-profile-edit.view.tsx**: Conditional rendering using a dedicated entraContainer is added for External Entra ID scenarios.
- **account-profile-edit-input.tsx**: The input component is updated to include a disabled parameter.
- **update-profile-onerf.ts and retail-actions/index.ts**: A OneRF profile update action is added that exports its associated classes to support the API integration.



[!INCLUDE [footer-include](../../includes/footer-banner.md)]
