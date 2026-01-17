---
title: Configure multiple B2C tenants in a Commerce environment
description: Learn how and when to set up multiple per-channel Microsoft Entra business-to-consumer (B2C) tenants for user authentication in a dedicated Microsoft Dynamics 365 Commerce environment.
author: BrianShook
ms.date: 01/16/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-02-12
ms.custom: 
  - bap-template
---

# Configure multiple B2C tenants in a Commerce environment

[!include [banner](includes/banner.md)]

This article describes how and when to set up multiple Microsoft Entra business-to-consumer (B2C) tenants per channel for user authentication in a dedicated Microsoft Dynamics 365 Commerce environment.

Dynamics 365 Commerce uses the Microsoft Entra B2C cloud identity service to support user credentials and authentication flows. Users can use the authentication flows to sign up, sign in, and reset their password. Microsoft Entra B2C stores a user's sensitive authentication information, such as the user name and password. The user record is unique to each B2C tenant, and it uses either user name (email address) credentials or social identity provider credentials.

In most cases, a single Microsoft Entra B2C tenant is used in a Commerce environment. Commerce customers can then create and publish multiple sites in the same Commerce environment, and the same customer credentials are used across these sites. However, if you want to treat the sites in the environment as different brands that appear to users as separate businesses, you can configure a B2C tenant for the channel that you use for the site and brand separation.

## Considerations when setting up multiple B2C tenants per channel

Often, when you treat each channel or site as a separate business, the best option is to use separate legal entities for user authentication flows in Commerce. However, if you want to keep each channel or site in the same environment and legal entity but want to have separate user authentication for each site, consider the following points before you proceed:

- Users have their own distinct credentials for each channel or site.

    The same person can have two separate accounts per channel or site, because each account is a unique entry into a separate B2C tenant.

- In the Microsoft Dynamics environment, separate customer records are returned for global record searches.

    If a user uses the same email address across channels or sites, global customer searches return results for each channel or site. A channel indicator is shown.

- Use the address book to help group users so that you can track them per channel.
- The number of customer records per channel might increase, and this increase might affect the performance of global customer searches.
- Carefully map B2C tenants to a channel to help prevent situations where customers sign up for an incorrect tenant. Otherwise, confusion or tracking problems can occur.

The following illustration shows multiple B2C tenants in a Commerce environment.

:::image type="content" source="media/MultiB2C_In_Environment.png" alt-text="Screenshot of multiple B2C tenants in a Commerce environment.":::

If you decide that your business requires distinct B2C tenants per channel in the same Commerce environment, complete the procedures in the following sections to request this feature.

## Configure B2C tenants in your environment

To configure B2C tenants in your environment, complete the relevant procedures in this section.

### Add a Microsoft Entra B2C tenant

To add a Microsoft Entra B2C tenant to your environment, follow these steps:

1. Sign in to Commerce site builder for your environment as a system admin. To configure Microsoft Entra B2C tenants, you must be a system admin for the Commerce environment.
1. In the left navigation pane, select **Tenant Settings** to expand it.
1. Select **B2C Settings**, and then select **Manage**.
1. Select **Add B2C Application**, and then enter the following information:

    - **Application Name**: Enter the name that you use for the application when managing it in Commerce. Use the application name that you chose when you set up the Microsoft Entra B2C application in the Azure portal. By using the same name, you reduce confusion when managing B2C tenants in Commerce.
    - **Tenant Name**: Enter the B2C tenant name as it appears in the Azure portal.
    - **Forget Password Policy ID**: Enter the policy ID (the name of the policy in the Azure portal).
    - **Signup Signin Policy ID**: Enter the policy ID (the name of the policy in the Azure portal).
    - **Client GUID**: Enter the Microsoft Entra B2C tenant ID as it appears in the Azure portal (not the application ID for the B2C tenant).
    - **Edit Profile Policy ID**: Enter the policy ID (the name of the policy in the Azure portal).

1. When you finish entering this information, select **OK** to save your changes. Your new Microsoft Entra B2C tenant appears in the list under **Manage B2C Applications**.

> [!NOTE]
> Leave fields such as **Scope**, **Non Interactive Policy ID**, **Non Interactive Client ID**, **Login Custom Domain**, and **Sign Up Policy ID** blank unless the Dynamics 365 Commerce team instructs you to set them.


### Manage or delete a Microsoft Entra B2C tenant

1. Sign in to Commerce site builder for your environment as a system admin. To configure Microsoft Entra B2C tenants, you must be a system admin for the Commerce environment.
1. In the left navigation pane, select **Tenant Settings** to expand it.
1. Select **B2C Settings**, and then select **Manage**.
1. To edit a B2C tenant, select the pencil symbol next to it. To delete a B2C tenant, select the trash can symbol next to it.
1. Select **Save**, and then select **Publish** to activate your changes.

> [!WARNING]
> When you configure a B2C tenant for a live or published site, users can register by using accounts that are present on the tenant. If you delete a configured tenant on the **Tenant Settings \> B2C Tenant** menu, you remove the association of that B2C tenant from sites that are associated with any channels of the tenant. In this case, your users might no longer be able to sign in to their accounts. Therefore, use extreme caution when you delete a configured tenant.
>
> When you delete a configured tenant, the B2C tenant and records are maintained, but the Commerce system configuration of that tenant is changed or removed. Users who try to register or sign in to the site create a new account record in the default or newly associated B2C tenant that's configured for the channel of the site.

## Configure your channel with a B2C tenant

1. Sign in to Commerce site builder for your environment as a system admin. To configure Microsoft Entra B2C tenants, you must be a system admin for the Commerce environment.
1. In the left navigation pane, select **Site Settings** to expand it.
1. Select **Channels**, and then select the channel to configure.
1. In the properties pane on the right, in the **Select B2C Application** field, select the configured Microsoft Entra B2C tenant to use for this channel.
1. On the command bar, select **Save and Publish** to commit the new or updated configuration.

> [!WARNING]
> If you change the B2C application that you assign to the channel, you remove the current references that you established for users who already registered in the environment. In this case, users can't access any credentials that are associated with the currently assigned B2C application. Therefore, change a channel Microsoft Entra B2C configuration only if you're setting up the channel for the first time, and no users can register. Otherwise, users might have to register again to establish a record in the new Microsoft Entra B2C tenant.

## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Deploy a new e-commerce tenant](deploy-ecommerce-site.md)

[Create an e-commerce site](create-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](dev-itpro/upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](dev-itpro/set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
