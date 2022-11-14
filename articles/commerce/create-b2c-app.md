---
title: Create the B2C application
description: This article describes how to set up your Azure Active Directory (Azure AD) business-to-consumer (B2C) tenants for user site authentication in Dynamics 365 Commerce.
author: BrianShook
ms.date: 11/14/2022
ms.topic: article 
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2020-02-13

---

# Create the B2C application

[!include [banner](includes/banner.md)]

Once the B2C tenant has been created, you will create a B2C application within your new Azure AD B2C tenant to interact with Commerce.

To create the B2C application, follow these steps.

1. In the Azure portal, select **App registrations**, and then select **New registration**.
1. Under **Name**, enter the name to give this Azure AD B2C application.
1. Under **Supported account types**, select **Accounts in any identity provider or organizational directory (for authenticating users with user flows)**.
1. For **Redirect URI**, enter your dedicated reply URLs as type **Web**. For information on reply URLs and how to format them, see [Reply URLs](#reply-urls) below. A redirect URI/reply URL must be entered to enable redirections from Azure AD B2C back to your site when a user authenticates. The reply URL can be added during the registration process, or can be added later by selecting the **Add a Redirect URI** link from the **Overview** menu in the B2C application's **Overview** section.
1. For **Permissions**, select **Grant admin consent to openid and offline_access permissions**.
1. Select **Register**.
1. Select the newly created application and navigate to the **Authentication** menu. 
1. If a reply URL is entered, under **Implicit grant and hybrid flows** select both the **Access tokens** and **ID tokens** options to enable them for the application, and then select **Save**. If a reply URL was not entered during registration, it can also be added on this page by selecting **Add a platform**, selecting **Web**, and then entering the redirect URI of the application. The **Implicit grant and hybrid flows** section will then be available to select both the **Access tokens** and **ID tokens** options.
1. Go to the **Overview** menu of the Azure portal and copy the **Application (client) ID**. Note this ID for later setup steps (referenced later as the **Client GUID**).

For additional reference on App Registrations in Azure AD B2C, please see [The new App registrations experience for Azure Active Directory B2C](/azure/active-directory-b2c/app-registrations-training-guide)

### Reply URLs

Reply URLs are important as they provide an allow list of the return domains when your site calls Azure AD B2C to authenticate a user. This permits the return of the authenticated user back to the domain from which they are signing into (your site domain). 

In the **Reply URL** box on the **Azure AD B2c - Applications \> New application** screen, you need to add separate lines for both your site domain and (once your environment is provisioned) the Commerce-generated URL. These URLs must always use a valid URL format and must be base URLs only (no trailing forward slashes or paths). The string ``/_msdyn365/authresp`` then needs to be appended to the base URLs, as in the following examples.

- ``https://www.fabrikam.com/_msdyn365/authresp`` (The domain should match the e-commerce domain completely. If you have multiple domains, you need to add this URL for each domain.)
- ``https://fabrikam-prod.commerce.dynamics.com/_msdyn365/authresp``


Proceed to the next step: [Create user flow policies](create-user-flow-policies.md)


## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Deploy a new e-commerce tenant](deploy-ecommerce-site.md)

[Create an e-commerce site](create-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
