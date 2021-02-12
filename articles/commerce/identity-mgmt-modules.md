---
# required metadata

title: Identity management pages and modules
description: This topic covers identity management pages and modules in Dynamics 365 Commerce.
author: BrianShook
manager: annbe
ms.date: 02/12/2021
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
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

Identity management modules display elements that e-commerce site users use to interact with the identity management system associated with the Dynamics 365 Commerce environment. Identity management modules are used on sign-in, sign-up, password reset, and account profile edit pages. Although these pages are built in Commerce, for security reasons they are hosted and served from the identity provider's servers. Commerce modules are configured by default to work with Azure Active Directory (Azure AD) business-to-consumer (B2C) as the identity provider. 

Identity management pages are built in Commerce site builder, but are served from Azure AD B2C servers and not from your Commerce site. Commerce recommends building separate Azure AD header and footer fragments with minimal page elements to use for identity management pages. Any fragments that have relative links, or make Commerce-specific calls (such as the favorites button or shopping cart module) will not work from the Azure AD B2C servers. The starter site shipped with your instance of Commerce includes example Azure AD header and footer fragments for reference.

To set up identity management pages in Azure AD B2C, see [Set up custom pages for user sign-ins](custom-pages-user-logins.md).

> [!WARNING] 
> Azure AD B2C will be retiring legacy user flows by August 1, 2021. Plan to migrate your user flows to the new recommended version, which provides feature parity and new features. For more information, see [User flows in Azure Active Directory B2C](https://docs.microsoft.com/azure/active-directory-b2c/user-flow-overview). 

### Preview, publish, and associate identity management pages with the Azure AD B2C user flow

Identity management pages use JavaScript initialized from the Azure AD B2C server. When previewing a page from site builder or an e-commerce site, it is common to see a white loading bar in the middle of the page that never initializes. Once a page is published, you must associate the page with the Azure AD B2C user flow as described in [Set up custom pages for user sign-ins](custom-pages-user-logins.md). Viewing a page as served from Azure AD B2C will then render the page elements with the initialized JavaScript.

## Sign-up module

The sign-up module is used on the sign-up page and includes the form elements for a site user to complete the sign-up flow. The user provides an email address to use as their username. The module allows for the Azure AD B2C email verification flow, triggering the "send code" and verifying the security PIN the user enters. Information collected on the sign-in page is used to create a record in Azure AD B2C, as well as a customer record in Commerce.

## Sign-in module

The sign-in module is used on the sign-in page and includes the form elements for users to sign in to their accounts. The sign-in page also displays buttons for users to navigate to the sign-up page, pairing directly with the "sign up and sign in" user flow in Azure AD B2C.

## Password reset modules

The following 2 modules are associated with the password reset flow.

- **Password reset verification** - This module is used on the password reset verification page to allow users to trigger the sending of a security PIN email to the email address associated with the user account. The password reset verification page also allows users to enter the received security PIN to verify the ownership of the account.
- **Password reset** - This module is used on the password reset page to allow the user to set and confirm a new password once the account email address has been verified on the password reset verification page.

## Account profile edit module

The account profile edit module is used on the profile edit page to allows users to update their first name (given name) and last name (surname). These two values are shared between Azure AD B2C and Commerce, and any user updates made via the profile edit page will update the values in both the Azure AD B2C and Commerce systems. On a Commerce e-commerce site, users can access the profile edit page (hosted by the identity provider) by going to **My account \> My profile \> View details \> Name**, and can then select **Edit** to update their information.

## Azure AD generic module

The Azure AD generic module follows the Azure AD B2C recommended pattern of setting a dedicated "div" element for Azure AD B2C to render elements within a site page. The generic module is flexible and a page employing it can be used for all Azure AD B2C user flow page layouts. Azure AD B2C will render the different user flow elements within the module on the page. This provides slightly less control of the visual elements when the page is rendered. CSS styling will apply, but complex positioning of page elements will not be possible as with other identity modules. A page using the generic module is more efficient to use since extensibility adjustments to the module are not needed if you are changing Azure AD B2C settings such as adding more social identity providers for sign-in and sign-up, or using future Azure AD B2C features.

## Additional resources

[Set up custom pages for user sign-ins](custom-pages-user-logins.md)
