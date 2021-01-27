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
> Please note that Azure AD B2C will be retiring legacy user flows as noted in the User Flows page in the Azure AD B2C resource in Azure portal. All legacy preview user flows are on a path to deprecation by August 1, 2021. Plan to migrate your preview user flows to their recommended version. This version offers you feature parity and is a home for new features. For more information, see [User flows in Azure Active Directory B2C](https://docs.microsoft.com/azure/active-directory-b2c/user-flow-overview). Commerce users can use the following identity management modules with the current Azure AD B2C recommended user flows as of the Commerce version 10.0.15 release.

## Sign-up page

The sign-up page includes the form elements for a site user to complete the sign-up flow. The user provides an email address to use as their username. The module allows for the Azure AD B2C email verification flow, triggering the 'send code' and input for the received security pin to be input. Information collected in the sign-in page is used to create a record in Azure AD B2C as well as a customer record in Commerce.

## Sign-in page

The sign-in page includes the form elements for a site user to sign in to their account. The sign-in page is combined with the buttons to navigate to the sign-up page experience; pairing directly with the 'Sign up and sign in' user flow in Azure AD B2C.

## Password reset pages

There are two pages associated with the password reset flow, 'password-reset' and 'password-reset-verification'.

- **Password reset verification** - This page and module allows the user to trigger the sending of the security pin email to the email address associated to the login account. The page also includes input for the received security pin to verify the ownership of the account.
- **Password reset** - This page and module allow for the user to set and confirm the new password once the account email address has been verified in the previous verification page.

## Profile edit page and account profile edit module

The account profile edit module used on the profile edit page allows users to update their first name (given name) and last name (surname). These two elements are shared between Azure AD B2C and Commerce, and any user updates made via the profile edit page will update the values across both the Azure AD B2C and Commerce systems.

## Azure AD generic module

The Azure AD generic module follows the Azure AD B2C recommended pattern of setting a dedicated 'div' for Azure AD B2C to render elements within the page. This module is the most flexible and the same page with this module can be used for all Azure AD B2C user flow page layouts. Azure AD B2C will render the different user flow elements within the module in the page. This provides slightly less control of the visual elements when the page is rendered (CSS will apply; but complex page positioning of the different elements will not be the same level of control as with the above noted identity modules.). This page is also more efficient to use in that extensibility adjustments to the module are not needed if you are changing Azure AD B2C settings (such as adding more Social Identity Providers for sign-in and sign-up, or using future new Azure AD B2C features).

## Additional information

- Note that these pages are built in Commerce site builder, but will be served from the Azure AD B2C servers, and not from your Commerce site. Commerce recommends building a separate Azure AD Header and Azure AD Footer fragments with minimal page elements to use for these specific pages. Any fragments included that have relative links, or make Commerce-specific calls (such as the favorites button, or shopping cart module) will not work from the Azure AD B2C servers. The starter site shipped with your instance of Commerce includes example Azure AD Header and Azure AD Footer fragments for reference.
- These pages utilize JavaScript initialized from the Azure AD B2C server. When previewing the page from site builder or directly at the Commerce site endpoint- it is common to see the white loading bar in the middle of the page which never initializes. Once the page is published, associate the page to the Azure AD B2C user flow as described in the [Set up custom pages for user sign-ins - Commerce](https://docs.microsoft.com/en-us/dynamics365/commerce/custom-pages-user-logins) article. Viewing the page as served from Azure AD B2C will render the elements with the initialized JavaScript.

## Additional resources

