---
title: Additional B2C information
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

# Additional B2C information

[!include [banner](includes/banner.md)]

### Customer migration

If you are considering migrating customer records from a previous identity provider platform, please work with the Dynamics 365 Commerce team to review your customer migration needs.

For additional Azure AD B2C documentation on customer migration, see [Migrate users to Azure Active Directory B2C](/azure/active-directory-b2c/active-directory-b2c-user-migration).

### Custom policies

For additional information regarding customizing Azure AD B2C interactions and policy flows beyond what is offered by B2C standard policies, see [Custom policies in Azure Active Directory B2C](/azure/active-directory-b2c/active-directory-b2c-overview-custom). 

### Secondary admin

An optional, secondary administrator account can be added in the **Users** section of your B2C tenant. This can be a direct account or a general account. If you need to share an account across team resources, a common account can also be created. Due to the sensitivity of the data stored in Azure AD B2C, a common account should be monitored closely per your company's security practices.

### Set up a custom sign-in domain

Azure AD B2C allows you to set up a custom sign-in domain for the Azure AD B2C tenant. For instructions, see [Enable custom domains for Azure Active Directory B2C](/azure/active-directory-b2c/custom-domain). 

If you use a custom sign-in domain, the domain must be entered into Commerce site builder.

To enter a custom sign-in domain in site builder, follow these steps.

1. In the top right corner of site builder, select the site switcher, and then select **Manage sites**.
1. In the left navigation pane, select **Tenant settings \> Site authentication setup**.
1. In the **Site authentication profiles** section, select **Manage**.
1. In the flyout menu on the right, select the **Edit** button (pencil symbol) next to the site authentication profile you want to enter a custom domain for.
1. In the **Edit site authentication profile** dialog box, under **Login custom domain**, enter your custom sign-in domain (for example, 'login.fabrikam.com').

> [!WARNING]
> When you update to a custom domain for the Azure AD B2C tenant, the change affects the tenant's issuer details for the token generated. Issuer details will then include the custom domain instead of the default domain provided by Azure AD B2C. A different **Issuer** configuration in Commerce headquarters (**Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters \> Identity Providers**) changes the system's interaction with site users, potentially creating a new customer record if a user is authenticating against the new issuer. Any custom domain changes should be thoroughly tested before switching to the custom domain in a live Azure AD B2C environment.







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
