---
title: Identity management pages and modules
description: Learn about identity management pages and modules in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 02/17/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2021-01-15
ms.custom: 
  - bap-template
---

# Identity management pages and modules

[!include [banner](../includes/banner.md)]

This article explains identity management pages and modules in Microsoft Dynamics 365 Commerce.

Identity management modules show elements on identity management pages that e-commerce site users use to interact with the identity management system that is associated with your Dynamics 365 Commerce environment. Specifically, identity management modules are used on sign-in, sign-up, password reset, and account profile edit pages. By default, Commerce modules are configured to use Microsoft Entra ID B2C as the identity provider.

> [!WARNING]
> Microsoft Entra ID B2C retires old (legacy) user flows by August 1, 2021. Plan to migrate your user flows to the new recommended version. The new version provides feature parity and new features. For more information, see [User flows in Microsoft Entra ID B2C](/azure/active-directory-b2c/user-flow-overview).

## Identity management pages

You build identity management pages in Commerce site builder. However, for security reasons, Microsoft Entra B2C servers host and serve these pages, not your Commerce site. As a best practice, build separate Microsoft Entra header and footer fragments for identity management pages, and include minimal page elements in them. Fragments that have relative links, or that make Commerce-specific calls (such as calls from the favorites button or shopping cart module), don't work from the Microsoft Entra B2C servers. The starter site that is released with your instance of Commerce includes sample Microsoft Entra header and footer fragments for reference.

For information about how to set up identity management pages in Microsoft Entra ID B2C, see [Set up custom pages for user sign-ins](../custom-pages-user-logins.md).

### Associate published identity management pages with the Microsoft Entra B2C user flow

Identity management pages use JavaScript that the Microsoft Entra B2C server initializes. Often, when you preview a page from site builder or an e-commerce site, a white loading bar appears in the middle of the page but isn't initialized. After you publish a page, associate the page with the Microsoft Entra B2C user flow as described in [Set up custom pages for user sign-ins](../custom-pages-user-logins.md). When you view the page that is served from Microsoft Entra ID B2C, the JavaScript initializes when page elements are rendered.

## Identity management modules

Use the following modules on identity management pages in Commerce.

### Sign-up module

Use the sign-up module on the sign-up page. It includes the form elements that site users use to complete the sign-up flow. A user provides an email address to use as their user name. The module then enables the Microsoft Entra B2C email verification flow to occur. In this flow, the user triggers the "send code," and the security personal identification number (PIN) that the user enters is verified. Information that you collect on the sign-up page is used to create a record in Microsoft Entra B2C and a customer record in Commerce.

### Sign-in module

Use the sign-in module on the sign-in page. It includes the form elements that users need to sign in to their accounts. The sign-in page also includes a button that users can use to open the sign-up page. By using this button, the page pairs directly with the "sign up and sign in" user flow in Microsoft Entra ID B2C.

### Password reset modules

The following two modules are associated with the password reset flow:

- **Password reset verification** – Use this module on the password reset verification page. It lets users trigger the sending of a security PIN email to the email address that is associated with the user account. The password reset verification page also lets users enter the security PIN that they receive to verify ownership of the account.
- **Password reset** – Use this module on the password reset page. It lets users set and confirm a new password after the account email address is verified on the password reset verification page.

### Account profile edit module

Use the account profile edit module on the account profile edit page. It lets users update their first name (given name) and family name (surname). These two values are shared between Microsoft Entra B2C and Commerce. If a user makes any updates through the account profile edit page, the values update in both the Microsoft Entra B2C system and the Commerce system.

On a Commerce e-commerce site, users access their account profile edit page by going to **My account \> My profile \> View details \> Name**. They can then select **Edit** to update their information.

### Microsoft Entra generic module

The Microsoft Entra generic module follows the recommended pattern for Microsoft Entra B2C, where a dedicated **\<div\>** element is set that Microsoft Entra ID B2C can use to render elements on a site page. The generic module is flexible, and a page that includes it can be used for page layouts for all Microsoft Entra B2C user flows.

Microsoft Entra ID B2C renders the different user flow elements in the module on the page. Therefore, there's slightly less control over the visual elements when the page is rendered. Although Cascading Style Sheets (CSS) styling applies, complex positioning of page elements can't be done as it can for other identity management modules.

A page that includes the generic module is more efficient to use, because extensibility adjustments to the module aren't required if you change Microsoft Entra B2C settings (for example, if you add more social identity providers for sign-in and sign-up) or if you use future Microsoft Entra B2C features.

## Additional resources

[Set up custom pages for user sign-ins](../custom-pages-user-logins.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]