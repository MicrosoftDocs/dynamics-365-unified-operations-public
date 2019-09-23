---
# required metadata

title: Setting Up Custom Pages for User Logins with AAD B2C
description: This topic describes how to setup your B2C Tenant for Dynamics 365 Commerce environment using Custom Pages.
author: brshoo
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Setting Up Custom Pages for User Logins with AAD B2C

## Overview

This topic describes how to build custom pages in Dynamics 365 Commerce to use for customized User Logins with your Azure Active Directory (AAD) B2C tenant. 

## Getting Started

To use custom pages authored in the Dynamics 365 Commerce Authoring Tools to use for login flows, users will need to set up the AAD Policies to be referenced in the Commerce environment. Users can set up the different 'Sign in and sign up', 'Password Reset', and 'Edit Profile' AAD B2C policies in their AAD B2C Application. The AAD B2C tenant and policy names can then be referenced for use during the Commerce environment provisioning in LCS for your Dynamics 365 Commerce environment. Users can build out a custom page in the Commerce Authoring Tools using the Sign In, Password Reset, or Edit Profile modules. These published page URLs are then referenced in your AAD B2C policy configurations in the Azure Portal.

## Setting Up your B2C Policies

Once you have set up your AAD B2C tenant and associated to your Commerce environment, in the Azure AD B2C page in the Azure Portal, select the "User flows (policies) menu under the "Policies" section in the left navigation pane. 

![B2C Custom Policies Menu](/articles/commerce/media/B2C_CustomPage_PoliciesMenu.png "B2C Custom Policies Menu")

Build out the 'Sign up and sign in', 'Profile editing', and 'Password reset' flows by using the following configurations:

#### Sign up and sign in

- Select the "New user flow" button and choose the **Sign up and sign in** policy under the Recommended section.
- Name your policy (ex: B2C_1_SignInSignUp). 

**<u>Note</u>**: The policy name will be fully referenced (with the 'B2C_1_' prefix included) in the Dynamics 365 Commerce environment. Policies cannot be renamed once created. If replacing an existing policy for your Commerce environment, you can delete the original and build a new policy with the same name. Or, if already provisioned, you can use a newly named policy by submitting the new policy name with a service request.

- Choose the Identity Providers utilized for the policy (ex: Email signup). Email signup must be chosen at minimum.
- Select the following attributes and claims for the Sign in and sign up policy:
  - Collect Attributes: Email Address, Given Name, Surname
  - Return Claims: Email addresse**s**, Given Name, Identity Provider, Surname, User's Object ID

![Sign Up Sign In Claims](/articles/commerce/media/B2C_SignInSignUp_Attributes.png "Sign Up Sign In Claims")

- Click "Create" to create the policy.
- Select this newly created policy and double-click to update its configurations.
- Under "Properties", set "Enable JavaScript enforcing page layout (preview)" to 'On'.

![Sign Up Sign In Enable Javascript](/articles/commerce/media/B2C_SignInSignUp_EnableJavascript.png "Sign Up Sign In Enable Javascript")

We'll come back to this policy once we have built out the custom pages to finish the Policy setup. Close out of the policy (the upper-right 'x' button) to return to the User Flows (policies) page in the Azure Portal.



#### Edit Profile 

- Select the "New user flow" button and choose the **Profile editing** policy under the Recommended section.
- Name your policy (ex: B2C_1_EditProfile). 
- Choose the Identity Providers utilized for the policy (ex: Local Account SignIn). Local Account SignIn must be chosen at minimum
- Select the following attributes and claims for the Profile editing policy:
  - Collect Attributes: Email Addresse**s**, Surname
  - Return claim: Email Addresse**s**, Given Name, Identity Provider, Surname, User's Object ID

![Profile edit Claims](/articles/commerce/media/B2C_ProfileEdit_Attributes.png "Profile edit Claims")

- Click "Create" to create the policy.
- Select this newly created policy and double-click to update its configurations.
- Under "Properties", set "Enable JavaScript enforcing page layout (preview)" to 'On'.

We'll come back to this policy once we have built out the custom pages to finish the Policy setup. Close out of the policy (the upper-right 'x' button) to return to the User Flows (policies) page in the Azure Portal.



#### Password Reset v1.1

- Select the "New user flow" button and choose the **Password reset v1.1** policy under the **<u>Preview</u>** section.

 ![Password Reset v1.1 menu](/articles/commerce/media/B2C_ForgetPassword_Menu.png "Password Reset v1.1 menu")

- Name your policy (ex: B2C_1_ForgetPassword). 
- Select "Reset password using email address" under Identity Providers section
- Select the following claims for the Profile editing policy:
  - Return claim: Email Addresse**s**, Given Name, Surname, User's Object ID

![Password Reset Claims](/articles/commerce/media/B2C_ForgetPassword_Attributes.png "Password Reset Claims")

- Click "Create" to create the policy.
- Select this newly created policy and double-click to update its configurations.
- Under "Properties", set "Enable JavaScript enforcing page layout (preview)" to 'On'.

We'll come back to this policy once we have built out the custom pages to finish the Policy setup. Close out of the policy (the upper-right 'x' button) to return to the User Flows (policies) page in the Azure Portal.



## Building the Custom Pages

In the Dynamics 365 Commerce authoring tools, navigate to your site and select a New Page. 

Build out 5 Templates and Pages total as follows:

- A 'Sign In' template and page using the 'Sign in' module.
- A 'Sign Up' template and page using the 'Sign up' module.

![Sign In Sign Up Modules](/articles/commerce/media/B2C_SignInSignUp_Module.png "Sign In Sign Up Modules")

- A 'Password Reset' template and page using the 'Password reset' module.
- A 'Password Reset verification' template and page using the 'Password reset verification' module.

![Password Reset Module](/articles/commerce/media/B2C_PasswordReset_Modules.png "Password Reset module")

- A 'Profile Edit' template and page using the 'Account profile edit' module

![Profile edit Module](/articles/commerce/media/B2C_ProfileEdit_Module.png "Profile edit Module")

When building the pages:

- Use a layout and style that best suits your business needs per page/module
- **Do Not** re-use Universal Headers and Footers with relative links.  As these pages will be hosted in the AAD B2C domain when in use, only direct URLs should be used for any links.
- Publish all pages and URLs to utilize in the AAD B2C setup.

Once published, collect the URLs to use in the AAD B2C Policy remaining setup. Each URL will be used with a "?preloadscripts=true" suffix added.



## Setting Up Custom Pages in the AAD B2C Policies

Navigate back to the Azure Portal AAD B2C Page and go to the "User Flows (policies)" menu.

#### Sign up and sign in

- Select your earlier built **Sign in and sign up** policy. 
- Navigate to the 'Page layouts' section. 
- Select the "Unified sign up or sign in page" Layout
  - Set "Use custom page content" to "Yes"
  - In the "Custom page URI" textbox, enter your full Sign In URL with the preloadscripts=true suffix. (Ex: "www.<my domain>.com/sign-in?preloadscripts=true")
  - Set the Page Layout Version (Preview) to 1.2.0
- Select the "Local account sign up page" Layout
  - Set "Use custom page content" to "Yes"
  - In the "Custom page URI" textbox, enter your full Sign In URL with the preloadscripts=true suffix. (Ex: "www.<my domain>.com/sign-up?preloadscripts=true")
  - Set the Page Layout Version (Preview) to 1.2.0
  - In the User attributes section:
    - Set Email Address, Given Name, and Surname fields for "Requires Verification" to "No"
    - Set Given Name and Surname fields for "Optional" to "No"

![Sign Up Page Policy Configuration](/articles/commerce/media/B2C_SignUp_PageURLConfig.png "Sign Up Page Policy Configuration")

#### Password Reset

- Select your earlier built **Password Reset** policy. 
- Navigate to the 'Page layouts' section. 
- Select the "New password page" Layout
  - Set "Use custom page content" to "Yes"
  - In the "Custom page URI" textbox, enter your full Sign In URL with the preloadscripts=true suffix. (Ex: "www.<my domain>.com/password-reset?preloadscripts=true")
  - Set the Page Layout Version (Preview) to 1.2.0
- Select the "Account verification page" Layout
  - Set "Use custom page content" to "Yes"
  - In the "Custom page URI" textbox, enter your full Sign In URL with the preloadscripts=true suffix. (Ex: "www.<my domain>.com/password-reset-verification?preloadscripts=true")
  - Set the Page Layout Version (Preview) to 1.2.0

#### Profile Editing

- Select your earlier built **Profile Editing** policy. 
- Navigate to the 'Page layouts' section. 
- Select the "Profile edit page" Layout
  - Set "Use custom page content" to "Yes"
  - In the "Custom page URI" textbox, enter your full Sign In URL with the preloadscripts=true suffix. (Ex: "www.<my domain>.com/profile-edit?preloadscripts=true")
  - Set the Page Layout Version (Preview) to 1.2.0
  - In the User attributes section:
    - Set Given Name, and Surname fields for "Requires Verification" to "No"
    - Set Given Name and Surname fields for "Optional" to "No"

The login modules as seen in the Starter Kit have default strings set for the labels and descriptions. These items can be customized in the SDK by updating the values in the module's global.json.

For example, the text for the forget password link showing as "Forgotten password?" can be edited in the Module's global.json of the starter kit to "Forgot Password?".

![Sign Up Module Strings](/articles/commerce/media/B2C_SignUp_ModuleFace.png "Sign Up Module Strings")


![SDK Global JSON editing string labels for modules](/articles/commerce/media/B2C_CustomizingStringsForModule.png "SDK Global JSON editing string labels for modules")

Once completed, deploying the updated modules package will reflect the changes in the displaying module in the Commerce Authoring Tools and when published.
