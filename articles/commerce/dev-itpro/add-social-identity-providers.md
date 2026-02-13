---
title: Add social identity providers
description: Learn how to add social identity providers in the Microsoft Azure portal.
author: BrianShook
ms.date: 02/11/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-02-13
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Add social identity providers

[!include [banner](../includes/banner.md)]

This article describes how to add social identity providers in the Microsoft Azure portal.

By using social identity providers, users can use their social accounts for authentication. Adding social identity provider authentication is optional in Dynamics 365 Commerce. 

If you don't add social identity provider authentication, the default Microsoft Entra B2C profiles are the main profiles for your user base. Users select their own username (their preferred email address) and set a password. Microsoft Entra ID B2C authenticates users directly. 

If you add social identity provider authentication and a user chooses one of the social identity providers offered, an entity is still created in the Microsoft Entra B2C tenant. Microsoft Entra ID B2C then authenticates the user's credentials by using the social identity provider.

> [!NOTE]
> The identity provider sign-in creates a record in the B2C tenant, but in a different format than local accounts since it calls the external social identity provider reference for authentication. The user can use the same email address across social identity providers, meaning that the email username used for authentication isn't unique to the tenant. Microsoft Entra ID B2C only enforces that users have a unique email address on local B2C accounts.

Before you can add a social identity provider for authentication, go to the identity provider's portal and set up an identity provider application as instructed in the Microsoft Entra B2C documentation. A list of links to the documentation is provided in the following list.

- [Amazon](/azure/active-directory-b2c/active-directory-b2c-setup-amzn-app)
- [Microsoft Entra ID (Single Tenant)](/azure/active-directory-b2c/active-directory-b2c-setup-oidc-azure-active-directory)
- [Microsoft Account](/azure/active-directory-b2c/active-directory-b2c-setup-msa-app)
- [Facebook](/azure/active-directory-b2c/active-directory-b2c-setup-fb-app)
- [GitHub](/azure/active-directory-b2c/active-directory-b2c-setup-github-app)
- [Google](/azure/active-directory-b2c/active-directory-b2c-setup-goog-app)
- [LinkedIn](/azure/active-directory-b2c/active-directory-b2c-setup-li-app)
- [OpenID Connect](/azure/active-directory-b2c/active-directory-b2c-setup-oidc-idp)
- [Twitter](/azure/active-directory-b2c/active-directory-b2c-setup-twitter-app)

### Add and set up a social identity provider

> [!NOTE]
> Adding social identity providers is an optional step when setting up a business-to-consumer (B2C) tenant in Microsoft Dynamics 365 Commerce.

To add and set up a social identity provider, follow these steps:  

1. In the Azure portal, go to **Identity Providers**.
1. Select **Add**. The **Add identity provider** screen appears.
1. Under **Name**, enter the name to display to users on your sign-in screen.
1. Under **Identity provider type**, select an identity provider from the list.
1. Select **OK**.
1. Select **Set up this identity provider** to access the **Set up the social identity provider** screen.
1. Under **Client ID**, enter the client ID that you got from the identity provider application setup.
1. Under **Client secret**, enter the client secret that you got from the identity provider application setup.
1. Attach user flow for sign-in and sign-up policies:
1. Go to **Microsoft Entra B2C – User flows (policies) \> {your sign-in sign-up policy} \> Identity providers**.
1. To attach the sign-in and sign-up user flow policy, select each identity provider you set up for your account. To test the flows, select **Run user flow** for each identity provider. A new tab displays the sign-in page with the new identity provider selection box.

The following image shows examples of the **Add identity provider** and **Set up the social identity provider** screens in Microsoft Entra ID B2C.

:::image type="content" source="../media/B2CImage_14.png" alt-text="Screenshot of the Add identity provider and Set up the social identity provider screens in Microsoft Entra ID B2C.":::

The following image shows an example of how to select identity providers on the Microsoft Entra B2C **Identity Providers** page.

:::image type="content" source="../media/B2CImage_16.png" alt-text="Screenshot of selecting social identity providers to enable on the Microsoft Entra B2C Identity Providers page.":::

The following image shows an example of a default sign-in screen with a social identity provider sign-in button displayed.

> [!NOTE]
> If you use the custom pages built in Commerce for your user flows, add the buttons for social identity providers by using the extensibility features of the Commerce module library. Additionally, when setting up your applications with a specific social identity provider, in some cases URL or configuration strings might be case sensitive. For more information, see your social identity provider's connection instructions.
 
:::image type="content" source="../media/B2CImage_17.png" alt-text="Screenshot of the default sign-in screen with a social identity provider sign-in button displayed.":::

## Next steps

To continue setting up a B2C tenant in Commerce, see [Update Commerce headquarters with the new Microsoft Entra B2C information](update-hq-aad-b2c-info.md).

## Additional resources

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Create or link to an existing Microsoft Entra B2C tenant in the Azure portal](create-link-aad-b2c-tenant.md)

[Create the B2C application](create-b2c-app.md)

[Create user flow policies](create-user-flow-policies.md)

[Update Commerce headquarters with the new Microsoft Entra B2C information](update-hq-aad-b2c-info.md)

[Configure your B2C tenant in Commerce site builder](config-b2c-tenant-site-builder.md)

[Additional B2C information](additional-b2c-info.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
