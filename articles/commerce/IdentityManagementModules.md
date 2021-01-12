---
# required metadata

title:Identity Management pages and modules
description: This topic reviews setting up an e-Commerce page with the Identity Management modules.
author: BrianShook
manager: BrendanSullivanMSFT
ms.date: 01/15/2021
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
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

This topic covers identity management pages and modules in Microsoft Dynamics 365 Commerce. Out of the box, Commerce modules are built to work with Azure ActiveDirectory B2C as the identity provider.

[!WARNING] Please note that AAD B2C will be retiring legacy user flows as noted in the User Flows page in the AAD B2C resource in Azure Portal.  As noted, all legacy preview user flows are on a path to deprecation by August 1, 2021. Plan to migrate your preview user flows to their Recommended version. This version offers you feature parity and is a home for new features. [Learn more.](https://aka.ms/userflowtype). Commerce users can utilize the below identity modules from Commerce version 10.0.15 and up to use with the current AAD B2C Recommended user flows.

## Overview

Identity management modules are used to display elements end-users will utilize for interaction with the identity management system paired to the Dynamics 365 Commerce environment. This includes pages for sign-in, sign-up, password reset, and edit profile. These pages are build in Commerce, but are hosted and served from the identity provider's servers for security. These modules can be seen in Site Builder under the 'AzureActiveDirectoryModules' category in the module picker.

To set up these pages in Azure ActiveDirectory (AAD) B2C, refer to the [Set up custom pages for user sign-ins - Commerce](https://docs.microsoft.com/en-us/dynamics365/commerce/custom-pages-user-logins) article.

## Sign-up

The sign-up page includes the form elements for an end user to complete the sign-up flow. The user will provide an email address for their username. The module allows for the AAD B2C email verification flow, triggering the 'send code' and input for the received security pin to be input. Information collected in the sign-in page is used to create a record in AAD B2C as well as a customer record in Commerce.

## Sign-in

The sign-in page includes the form elements for an end user to sign-in to their account. The sign-in page is combined with the buttons to navigate to the sign-up page experience; pairing directly with the 'Sign up and sign in' user flow in AAD B2C.

## Password-Reset

There are two pages associated with the password reset flow, 'password-reset' and 'password-reset-verification'.

- **Password reset verification** - This page and module allows the user to trigger the sending of the security pin email to the email address associated to the login account. The page also includes input for the received security pin to verify the ownership of the account.
- **Password reset** - This page and module allow for the user to set and confirm the new password once the account email address has been verified in the previous verification page.

## User profile edit

The profile edit page and 'user profile edit' module allow for the user to update their first name (given Name) and last name (surname). These two elements are shared between AAD B2C and Commerce, and the user update in this page will update the values across both systems.



## AAD Generic

The AAD Generic module follows the AAD B2C recommended pattern of setting a dedicated 'div' for AAD B2C to render elements within the page. This module is the most flexible and the same page with this module can be used for all AAD B2C user flow page layouts. AAD B2C will render the different user flow elements within the module in the page. This provides slightly less control of the visual elements when the page is rendered (CSS will apply; but complex page positioning of the different elements will not be the same level of control as with the above noted identity modules.). This page is also more efficient to use in that extensibility adjustments to the module are not needed if you are changing AAD B2C settings (such as adding more Social Identity Providers for sign-in and sign-up, or using future new AAD B2C features).



## Additional Information

- Note that these pages are built in Commerce site builder, but will be served from the AAD B2C servers, and not from your Commerce site. Commerce recommends building a separate AAD Header and AAD Footer fragments with minimal page elements to use for these specific pages. Any fragments included that have relative links, or make Commerce-specific calls (such as the favorites button, or shopping cart module) will not work from the AAD B2C servers. The starter site shipped with your instance of Commerce includes example AAD Header and AAD Footer fragments for reference.
- These pages utilize JavaScript initialized from the AAD B2C server. When previewing the page from site builder or directly at the Commerce site endpoint- it is common to see the white loading bar in the middle of the page which never initializes. Once the page is published, associate the page to the AAD B2C user flow as described in the [Set up custom pages for user sign-ins - Commerce](https://docs.microsoft.com/en-us/dynamics365/commerce/custom-pages-user-logins) article. Viewing the page as served from AAD B2C will render the elements with the initialized JavaScript.

