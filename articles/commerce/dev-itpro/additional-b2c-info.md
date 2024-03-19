---
title: Additional B2C information
description: This article provides additional information on how to set your business-to-consumer (B2C) tenant in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 03/15/2024
ms.topic: article 
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2020-02-13

---

# Additional B2C information

[!include [banner](../includes/banner.md)]

This article provides additional information on how to set your business-to-consumer (B2C) tenant in Microsoft Dynamics 365 Commerce.

### Customer migration

If you're considering migrating customer records from a previous identity provider platform, work with the Dynamics 365 Commerce team to review your customer migration needs.

For additional Microsoft Entra B2C documentation on customer migration, see [Migrate users to Microsoft Entra ID B2C](/azure/active-directory-b2c/active-directory-b2c-user-migration).

### Custom policies

For more information regarding customizing Microsoft Entra B2C interactions and policy flows beyond what is offered by B2C standard policies, see [Custom policies in Microsoft Entra ID B2C](/azure/active-directory-b2c/active-directory-b2c-overview-custom). 

### Secondary admin

An optional, secondary administrator account can be added in the **Users** section of your B2C tenant. This account can be a direct account or a general account. If you need to share an account across team resources, a common account can also be created. Due to the sensitivity of the data stored in Microsoft Entra B2C, a common account should be monitored closely per your company's security practices.

### Enable Microsoft Entra B2C phone sign-up and sign-in 

To enable Microsoft Entra B2C phone sign-up and sign-in for Commerce, follow the instructions in [Set up phone sign-up and sign-in for user flows](/azure/active-directory-b2c/phone-authentication-user-flows). Microsoft recommends that you use a generic Commerce Microsoft Entra identity module. If you need to include the style, you must use the generic Microsoft Entra identity module.

Both the **Phone signup** and **Phone/Email signup** options are supported. When you select return values for **Phone signup**, Microsoft recommends that you select **Email Address** as a required value, because Commerce uses email for receipts and other purposes.

### Set up a custom sign-in domain

Microsoft Entra ID B2C allows you to set up a custom sign-in domain for the Microsoft Entra B2C tenant. For instructions, see [Enable custom domains for Microsoft Entra ID B2C](/azure/active-directory-b2c/custom-domain). 

If you use a custom sign-in domain, the domain must be entered into Commerce site builder.

To enter a custom sign-in domain in site builder, follow these steps.

1. In the top right corner of site builder, select the site switcher, and then select **Manage sites**.
1. In the left navigation pane, select **Tenant settings \> Site authentication setup**.
1. In the **Site authentication profiles** section, select **Manage**.
1. In the flyout menu on the right, select the **Edit** button (pencil symbol) next to the site authentication profile you want to enter a custom domain for.
1. In the **Edit site authentication profile** dialog box, under **Login custom domain**, enter your custom sign-in domain (for example, 'login.fabrikam.com').

> [!WARNING]
> When you update to a custom domain for the Microsoft Entra B2C tenant, the change affects the tenant's issuer details for the token generated. Issuer details will then include the custom domain instead of the default domain provided by Microsoft Entra B2C. A different **Issuer** configuration in Commerce headquarters (**Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters \> Identity Providers**) changes the system's interaction with site users, potentially creating a new customer record if a user is authenticating against the new issuer. Any custom domain changes should be thoroughly tested before switching to the custom domain in a live Microsoft Entra B2C environment.

### Configure a sign-in link with a custom return URL

To define a return URL from your Microsoft Entra B2C sign-in page, use a URL in the following format:

`{domainurl}/_msdyn365/signin?ru={channelUrl}`

For example, `https://www.adventure-works.com/_msdyn365/signin?ru=https://www.adventure-works.com/kiama-classic-surfboard/68719518371.p`.

You can use this URL format in emails or other web communications to link users to a Microsoft Entra B2C sign-in screen and directly return them to a specific page on your site after they sign in.

## Additional resources

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Create or link to an existing Microsoft Entra B2C tenant in the Azure portal](create-link-aad-b2c-tenant.md)

[Create the B2C application](create-b2c-app.md)

[Create user flow policies](create-user-flow-policies.md)

[Add social identity providers (Optional)](add-social-identity-providers.md)

[Update Commerce headquarters with the new Microsoft Entra B2C information](update-hq-aad-b2c-info.md)

[Configure your B2C tenant in Commerce site builder](config-b2c-tenant-site-builder.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
