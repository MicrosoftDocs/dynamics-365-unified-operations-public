---
# required metadata

title: Identity management pages and modules
description: This topic covers identity management pages and modules in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 03/01/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2021-01-15
ms.dyn365.ops.version: 

---

# Identity management pages and modules

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers identity management pages and modules in Microsoft Dynamics 365 Commerce.

Identity management modules show elements on identity management pages that e-commerce site users use to interact with the identity management system that is associated with your Dynamics 365 Commerce environment. Specifically, identity management modules are used on sign-in, sign-up, password reset, and account profile edit pages. By default, Commerce modules are configured to use Azure Active Directory B2C (Azure AD B2C) as the identity provider.

> [!WARNING]
> Azure AD B2C will retire old (legacy) user flows by August 1, 2021. Therefore, you should plan to migrate your user flows to the new recommended version. The new version provides feature parity and new features. For more information, see [User flows in Azure Active Directory B2C](/azure/active-directory-b2c/user-flow-overview).

## Identity management pages

Identity management pages are built in Commerce site builder. However, for security reasons, they are hosted and served from Azure AD B2C servers, not from your Commerce site. As a best practice, you should build separate Azure AD header and footer fragments for identity management pages, and include minimal page elements in them. Fragments that have relative links, or that make Commerce-specific calls (such as calls from the favorites button or shopping cart module), won't work from the Azure AD B2C servers. The starter site that is released with your instance of Commerce includes sample Azure AD header and footer fragments for reference.

For information about how to set up identity management pages in Azure AD B2C, see [Set up custom pages for user sign-ins](custom-pages-user-logins.md).

### Associate published identity management pages with the Azure AD B2C user flow

Identity management pages use JavaScript that is initialized from the Azure AD B2C server. Often, when a page is previewed from site builder or an e-commerce site, a white loading bar appears in the middle of the page but is never initialized. After a page is published, you must associate the page with the Azure AD B2C user flow as described in [Set up custom pages for user sign-ins](custom-pages-user-logins.md). Then, when you view the page that is served from Azure AD B2C, the JavaScript will be initialized when page elements are rendered.

## Identity management modules

The following modules are used on identity management pages in Commerce.

### Sign-up module

The sign-up module is used on the sign-up page. It includes the form elements that site users use to complete the sign-up flow. A user provides an email address to use as their user name. The module then enables the Azure AD B2C email verification flow to occur. In this flow, the "send code" is triggered, and the security personal identification number (PIN) that the user enters is verified. Information that is collected on the sign-up page is used to create a record in Azure AD B2C and a customer record in Commerce.

### Sign-in module

The sign-in module is used on the sign-in page. It includes the form elements that users use to sign in to their accounts. The sign-in page also includes a button that users can use to open the sign-up page. In this way, the page is paired directly with the "sign up and sign in" user flow in Azure AD B2C.

### Password reset modules

The following two modules are associated with the password reset flow:

- **Password reset verification** – This module is used on the password reset verification page. It lets users trigger the sending of a security PIN email to the email address that is associated with the user account. The password reset verification page also lets users enter the security PIN that they receive to verify ownership of the account.
- **Password reset** – This module is used on the password reset page. It lets users set and confirm a new password after the account email address has been verified on the password reset verification page.

### Account profile edit module

The account profile edit module is used on the account profile edit page. It lets users update their first name (given name) and last name (surname). These two values are shared between Azure AD B2C and Commerce. If a user makes any updates via the account profile edit page, the values will be updated in both the Azure AD B2C system and the Commerce system.

On a Commerce e-commerce site, users access their account profile edit page by going to **My account \> My profile \> View details \> Name**. They can then select **Edit** to update their information.

### Azure AD generic module

The Azure AD generic module follows the recommended pattern for Azure AD B2C, where a dedicated **\<div\>** element is set that Azure AD B2C can use to render elements on a site page. The generic module is flexible, and a page that includes it can be used for page layouts for all Azure AD B2C user flows.

Azure AD B2C will render the different user flow elements in the module on the page. Therefore, there is slightly less control over the visual elements when the page is rendered. Although Cascading Style Sheets (CSS) styling will apply, complex positioning of page elements can't be done as it can for other identity management modules.

A page that includes the generic module is more efficient to use, because extensibility adjustments to the module aren't required if you change Azure AD B2C settings (for example, if you add more social identity providers for sign-in and sign-up) or if you use future Azure AD B2C features.

## Additional resources

[Set up custom pages for user sign-ins](custom-pages-user-logins.md)