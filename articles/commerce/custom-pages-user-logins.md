---
# required metadata

title: Set up custom pages for user logins
description: This topic describes how to build custom pages in Dynamics 365 Commerce that handle customized Azure Active Directory (AAD) business-to-consumer (B2C) tenant user logins.
author: brianshook
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

# Set up custom pages for user logins

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to build custom pages in Dynamics 365 Commerce that handle customized Azure Active Directory (AAD) business-to-consumer (B2C) tenant user logins.

## Overview

To use custom pages authored in Commerce to handle user login flows, you must set up the AAD policies that will be referenced in the Commerce environment. You can configure the "Sign in and sign up," "Profile editing," and "Password reset" AAD B2C policies using the AAD B2C application. The AAD B2C tenant and policy names can then be referenced for use during the Commerce environment provisioning that is done using Microsoft Lifecycle Services (LCS). 

The custom Commerce pages can be built using the sign in, edit profile, or password reset modules. The published page URLs for these custom pages should then be referenced in AAD B2C policy configurations in the Azure portal.

## Set up B2C policies

Once you have set up your AAD B2C tenant and associated it with your Commerce environment, in the Azure AD B2C page in the Azure Portal, select **User flows (policies)** in the **Policies** section, as shown in the following screenshot.   

![B2C Custom Policies Menu](./media/B2C_CustomPage_PoliciesMenu.png)

The "Sign up and sign in," "Profile editing," and "Password reset" user login flows can then be configured as follows.

### Configure the "Sign up and sign in" user login flow

To configure the "Sign up and sign in" user login flow, do the following.

1. Click **New user flow**, then in the **Recommended** section, select the **Sign up and sign in** policy.
1. Enter a name for the policy (for example, "B2C_1_SignInSignUp"). 

>[!NOTE]
> The policy name will be fully referenced (with the 'B2C_1_' prefix included) in the Commerce environment. Policies cannot be renamed once created. If replacing an existing policy for your Commerce environment, you can delete the original and build a new policy with the same name. Or, if already provisioned, you can use a newly-named policy by submitting the new policy name using a service request.

1. Select the **Identity Providers** used for the policy (for example, **Email signup**). **Email signup** must be chosen at a minimum.
1. Select the following attributes and claims:
    - Under **Collect attribute**: **Email Address**, **Given Name**, **Surname**
    - Under **Return claim**: **Email addresses**, **Given Name**, **Identity Provider**, **Surname**, **User's Object ID**
  
The following image shows the **User attributes and claims** screen with the correct attributes and claims selected.   

![Sign Up Sign In Claims](./media/B2C_SignInSignUp_Attributes.png)

1. Click **OK** to create the policy.
1. Double-click the new policy name, then in the navigation pane click **Properties.**
1. For **Enable JavaScript enforcing page layout (preview)**, select **On**.

The following image show the policy **Properties** screen.   

![Sign Up Sign In Enable Javascript](./media/B2C_SignInSignUp_EnableJavascript.png)

We'll come back to this policy once we have built out the custom pages to finish the policy setup. Close out of the policy to return to the **User Flows (policies)** page of the Azure portal.

### Configure the "Profile editing" user login flow 

To configure the "Profile editing" user login flow, do the following.

1. Click **New user flow**, then in the **Recommended** section, select the **Profile editing** policy.
1. Enter a name for the policy (for example, "B2C_1_EditProfile"). 
1. Select the **Identity Providers** used for the policy (for example, **Local Account SignIn**). **Local Account SignIn** must be chosen at a minimum.
1. Select the following attributes and claims:
    - Under **Collect attribute**: **Email Addresses**, **Surname**
    - Under **Return claim**: **Email Addresses**, **Given Name**, **Identity Provider**, **Surname**, **User's Object ID**
  
The following image show the (lorem ipsum).   

![Profile edit Claims](./media/B2C_ProfileEdit_Attributes.png)

1. Click **OK** to create the policy.
1. Double-click the new policy name, then in the navigation pane click **Properties.**.
1. For **Enable JavaScript enforcing page layout (preview)**, select **On**.

We'll come back to this policy once we have built out the custom pages to finish the Policy setup. Close out of the policy to return to the **User Flows (policies)** page in the Azure portal.

### Configure the "Password reset" user login flow

To configure the "Password reset" user login flow, do the following.

1. Click **New user flow**, then in the **Preview** section, select the **Password reset v1.1** policy.

The following image shows the **Preview** section of the **Select a user flow type** screen.   

 ![Password Reset v1.1 menu](./media/B2C_ForgetPassword_Menu.png)

1. Enter a name for the policy (for example, "B2C_1_ForgetPassword"). 
1. In the **Identity Providers** section, select **Reset password using email address**.
1. Select the following claims:
    - Under **Return claim**: **Email Addresses**, **Given Name,** **Surname,** **User's Object ID**

The following image shows the **Application claims** screen with the correct claims selected.

![Password Reset Claims](./media/B2C_ForgetPassword_Attributes.png)

1. Click **OK** to create the policy.
1. Double-click the new policy name, then in the navigation pane click **Properties.**.
1. For **Enable JavaScript enforcing page layout (preview)**, select **On**.

We'll come back to this policy once we have built out the custom pages to finish the Policy setup. Close out of the policy to return to the **User Flows (policies)** page in the Azure portal.

## Build the custom pages

In the Dynamics 365 Commerce authoring tools, navigate to your site and select a New Page. 

Build out 5 Templates and Pages total as follows:

- A 'Sign In' template and page using the 'Sign in' module.
- A 'Sign Up' template and page using the 'Sign up' module.

The following image show the (lorem ipsum).   

![Sign In Sign Up Modules](./media/B2C_SignInSignUp_Module.png)

- A 'Password Reset' template and page using the 'Password reset' module.
- A 'Password Reset verification' template and page using the 'Password reset verification' module.

The following image show the (lorem ipsum).   

![Password Reset Module](./media/B2C_PasswordReset_Modules.png)

- A 'Profile Edit' template and page using the 'Account profile edit' module

The following image show the (lorem ipsum).   

![Profile edit Module](./media/B2C_ProfileEdit_Module.png)

When building the pages:

- Use a layout and style that best suits your business needs per page/module
- **Do Not** re-use Universal Headers and Footers with relative links.  As these pages will be hosted in the AAD B2C domain when in use, only direct URLs should be used for any links.
- Publish all pages and URLs to utilize in the AAD B2C setup.

Once published, collect the URLs to use in the AAD B2C Policy remaining setup. Each URL will be used with a "?preloadscripts=true" suffix added.

## Set up custom pages in the AAD B2C policies

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

The following image show the (lorem ipsum).  

![Sign Up Page Policy Configuration](./media/B2C_SignUp_PageURLConfig.png)

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

The following image show the (lorem ipsum).  

![Sign Up Module Strings](./media/B2C_SignUp_ModuleFace.png)

The following image show the (lorem ipsum).  

![SDK Global JSON editing string labels for modules](./media/B2C_CustomizingStringsForModule.png)

Once completed, deploying the updated modules package will reflect the changes in the displaying module in the Commerce Authoring Tools and when published.
