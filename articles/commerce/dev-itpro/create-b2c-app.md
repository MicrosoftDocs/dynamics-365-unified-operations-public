---
title: Create a B2C application
description: Learn how to create a Microsoft Dynamics 365 Commerce business-to-consumer (B2C) application in the Microsoft Azure portal.
author: BrianShook
ms.date: 02/13/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-02-13
ms.custom: 
  - bap-template
---

# Create a B2C application

[!include [banner](../includes/banner.md)]

This article describes how to create a Microsoft Dynamics 365 Commerce business-to-consumer (B2C) application in the Microsoft Azure portal.

After you create your B2C tenant, create a B2C application within your new Microsoft Entra tenant to interact with Commerce.

To create the B2C application, follow these steps:

1. In the Azure portal, select **App registrations**, and then select **New registration**.
1. Under **Name**, enter the name for this Microsoft Entra B2C application.
1. Under **Supported account types**, select **Accounts in any identity provider or organizational directory (for authenticating users with user flows)**.
1. For **Redirect URI**, enter your dedicated reply URLs as type **Web**. For information on reply URLs and how to format them, see [Reply URLs](#reply-urls). Enter a redirect URI/reply URL to enable redirections from Microsoft Entra B2C back to your site when a user authenticates. You can add the reply URL during the registration process, or add it later by selecting the **Add a Redirect URI** link from the **Overview** menu in the B2C application's **Overview** section.
1. For **Permissions**, select **Grant admin consent to openid and offline_access permissions**.
1. Select **Register**.
1. Select the newly created application and go to the **Authentication** menu. 
1. If you entered a reply URL, select both the **Access tokens** and **ID tokens** options to enable them for the application, and then select **Save**. If you didn't enter a reply URL during registration, add one on this page by selecting **Add a platform**, selecting **Web**, and then entering the redirect URI of the application. 
1. Go to the **Overview** menu of the Azure portal and copy the **Application (client) ID**. Note this ID for later setup steps (referenced later as the **Client GUID**).

For more information on App Registrations in Microsoft Entra ID B2C, see [The new App registrations experience for Microsoft Entra ID B2C](/azure/active-directory-b2c/app-registrations-training-guide)

### Reply URLs

Reply URLs are important because they provide an allow list of the return domains when your site calls Microsoft Entra B2C to authenticate a user. By using this list, the authenticated user can return to the domain from which they're signing into (your site domain). 

In the **Reply URL** box on the **Microsoft Entra ID B2c - Applications \> New application** screen, add separate lines for both your site domain and (once your environment is provisioned) the Commerce-generated URL. These URLs must always use a valid URL format and must be base URLs only (no trailing forward slashes or paths). Append the string ``/_msdyn365/authresp`` to the base URLs, as shown in the following examples.

- ``https://www.fabrikam.com/_msdyn365/authresp`` (The domain should match the e-commerce domain completely. If you have multiple domains, add this URL for each domain.)
- ``https://fabrikam-prod.commerce.dynamics.com/_msdyn365/authresp``

## Next steps

To continue setting up a B2C tenant in Commerce, see [Create user flow policies](create-user-flow-policies.md).

## Additional resources

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Create or link to an existing Microsoft Entra B2C tenant in the Azure portal](create-link-aad-b2c-tenant.md)

[Create user flow policies](create-user-flow-policies.md)

[Add social identity providers (Optional)](add-social-identity-providers.md)

[Update Commerce headquarters with the new Microsoft Entra B2C information](update-hq-aad-b2c-info.md)

[Configure your B2C tenant in Commerce site builder](config-b2c-tenant-site-builder.md)

[Additional B2C information](additional-b2c-info.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
