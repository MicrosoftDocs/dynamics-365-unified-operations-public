---
# required metadata

title: Identity management pages and modules
description: This topic covers identity management pages and modules in Dynamics 365 Commerce.
author: BrianShook
manager: annbe
ms.date: 01/28/2021
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

Identity management modules display elements that e-commerce site users use to interact with the identity management system associated with the Dynamics 365 Commerce environment. This includes pages for sign-in, sign-up, password reset, and profile edit. These pages are built in Commerce, but are hosted and served from the identity provider's servers for security. Commerce modules are configured by default to work with Azure Active Directory (Azure AD) business-to-consumer (B2C) as the identity provider. These modules can be seen in Commerce site builder under the "AzureActiveDirectoryModules" category in the module picker.

To set up identity management pages in Azure AD B2C, see [Set up custom pages for user sign-ins](custom-pages-user-logins.md).

> [!WARNING] 
> Azure AD B2C will be retiring legacy user flows as noted in the User Flows page in the Azure AD B2C resource in Azure portal. All legacy preview user flows are on a path to deprecation by August 1, 2021. Plan to migrate your preview user flows to their recommended version. This version offers you feature parity and is a home for new features. For more information, see [User flows in Azure Active Directory B2C](https://docs.microsoft.com/azure/active-directory-b2c/user-flow-overview). Commerce users can use the following identity management modules with the current Azure AD B2C recommended user flows as of the Commerce version 10.0.15 release.

## Sign-up page

The sign-up page includes the form elements for a site user to complete the sign-up flow. The user provides an email address to use as their username. The module allows for the Azure AD B2C email verification flow, triggering the "send code" and verifying the security PIN the user enters. Information collected on the sign-in page is used to create a record in Azure AD B2C, as well as a customer record in Commerce.

## Sign-in page

The sign-in page includes the form elements for a site user to sign in to their account. The sign-in page also displays buttons for users to navigate to the sign-up page, pairing directly with the "sign up and sign in" user flow in Azure AD B2C.

## Password reset pages

There are two pages associated with the password reset flow, "password reset verification" and "password reset."

- **Password reset verification** - The password reset verification page and module allow the user to trigger the sending of a security PIN email to the email address associated with the user account. The password reset verification page also allows users to enter the received security PIN to verify the ownership of the account.
- **Password reset** - The password reset page and module allow the user to set and confirm a new password once the account email address has been verified in the previous verification page.

## Profile edit page and account profile edit module

The account profile edit module used on the profile edit page allows users to update their first name (given name) and last name (surname). These two values are shared between Azure AD B2C and Commerce, and any user updates made via the profile edit page will update the values in both the Azure AD B2C and Commerce systems.

## Azure AD generic module

The Azure AD generic module follows the Azure AD B2C recommended pattern of setting a dedicated "div" for Azure AD B2C to render elements within a page. The generic module is flexible and a page employing it can be used for all Azure AD B2C user flow page layouts. Azure AD B2C will render the different user flow elements within the module on the page. This provides slightly less control of the visual elements when the page is rendered (CSS will apply, but complex page positioning of the different elements will not be possible as with other identity modules.). A page using the generic module is also more efficient to use since extensibility adjustments to the module are not needed if you are changing Azure AD B2C settings such as adding more social identity providers for sign-in and sign-up, or using future Azure AD B2C features).

## Additional information

- Identity management pages are built in Commerce site builder, but will be served from Azure AD B2C servers and not from your Commerce site. Commerce recommends building a separate Azure AD header and footer fragments with minimal page elements to use for these specific pages. Any fragments that have relative links, or make Commerce-specific calls (such as the favorites button or shopping cart module) will not work from the Azure AD B2C servers. The starter site shipped with your instance of Commerce includes example Azure AD header and footer fragments for reference.
- Identity management pages use JavaScript initialized from the Azure AD B2C server. When previewing a page from site builder or the Commerce site, it is common to see a white loading bar in the middle of the page that never initializes. Once a page is published, you must associate the page with the Azure AD B2C user flow as described in [Set up custom pages for user sign-ins](custom-pages-user-logins.md). Viewing a page as served from Azure AD B2C will render the page elements with the initialized JavaScript.

## Additional resources

[Set up custom pages for user sign-ins](custom-pages-user-logins.md)
