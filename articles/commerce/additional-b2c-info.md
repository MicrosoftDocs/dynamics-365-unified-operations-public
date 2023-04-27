---
title: Additional B2C information
description: This article provides additional information on how to set your business-to-consumer (B2C) tenant in Microsoft Dynamics 365 Commerce.
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

This article provides additional information on how to set your business-to-consumer (B2C) tenant in Microsoft Dynamics 365 Commerce.

### Customer migration

If you are considering migrating customer records from a previous identity provider platform, please work with the Dynamics 365 Commerce team to review your customer migration needs.

For additional Azure AD B2C documentation on customer migration, see [Migrate users to Azure Active Directory B2C](/azure/active-directory-b2c/active-directory-b2c-user-migration).

### Custom policies

For additional information regarding customizing Azure AD B2C interactions and policy flows beyond what is offered by B2C standard policies, see [Custom policies in Azure Active Directory B2C](/azure/active-directory-b2c/active-directory-b2c-overview-custom). 

### Secondary admin

An optional, secondary administrator account can be added in the **Users** section of your B2C tenant. This can be a direct account or a general account. If you need to share an account across team resources, a common account can also be created. Due to the sensitivity of the data stored in Azure AD B2C, a common account should be monitored closely per your company's security practices.

### AAD B2C Phone Sign-up and Sign-in 

To enable AADB2C phone sign-up and sign-in for Dynamics 365 e-Commerce follow the instructions in this [article](https://learn.microsoft.com/en-us/azure/active-directory-b2c/phone-authentication-user-flows). Please note, it is recommended to use a generic AAD Identity Module in Dynamics. Also, if there is a need to include the style, the use of generic AAD Identity Module is required.

Both options **Phone signup** and **Phone/Email signup** are supported. 

When selecting return values for **Phone signup** note that it is recommended to choose **Email Address** as a required value, because D365 Commerce utilizes email for receipts and other purposes.

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

[Set up a B2C tenant in Commerce](set-up-b2c-tenant.md)

[Create or link to an existing Azure AD B2C tenant in the Azure portal](create-link-aad-b2c-tenant.md)

[Create the B2C application](create-b2c-app.md)

[Create user flow policies](create-user-flow-policies.md)

[Add social identity providers (Optional)](add-social-identity-providers.md)

[Update Commerce headquarters with the new Azure AD B2C information](update-hq-aad-b2c-info.md)

[Configure your B2C tenant in Commerce site builder](config-b2c-tenant-site-builder.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
