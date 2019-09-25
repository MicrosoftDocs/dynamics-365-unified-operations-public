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

Once you have set up your AAD B2C tenant and associated it with your Commerce environment, in the Azure AD B2C page in the Azure portal, select **User flows (policies)** in the **Policies** section, as shown in the following screenshot.   

![B2C Custom Policies Menu](./media/B2C_CustomPage_PoliciesMenu.png)

The "Sign up and sign in," "Profile editing," and "Password reset" user login flows can then be configured as follows.

### Configure the "Sign up and sign in" policy

To configure the "Sign up and sign in" policy, do the following.

1. Click **New user flow**, then in the **Recommended** section, select the **Sign up and sign in** policy.
1. Enter a name for the policy (for example, "B2C_1_SignInSignUp"). 
1. Select the **Identity Providers** used for the policy (for example, **Email signup**). **Email signup** must be chosen at a minimum.
1. In the **Collect attribute** column, select **Email Address**, **Given Name**, and **Surname**.
1. In the **Return claim** column, select **Email addresses**, **Given Name**, **Identity Provider**, **Surname**, and **User's Object ID**.
1. Click **OK** to create the policy.
1. Double-click the new policy name, then in the navigation pane click **Properties.**
1. For **Enable JavaScript enforcing page layout (preview)**, select **On**.

>[!NOTE]
> The policy name will be fully referenced (with the 'B2C_1_' prefix included) in the Commerce environment. Policies cannot be renamed once created. If replacing an existing policy for your Commerce environment, you can delete the original and build a new policy with the same name. Or, if already provisioned, you can use a newly-named policy by submitting the new policy name using a service request.

The following image shows the **User attributes and claims** screen with the correct attributes and claims selected.   

![Sign Up Sign In Claims](./media/B2C_SignInSignUp_Attributes.png)

The following image show the policy **Properties** screen.   

![Sign Up Sign In Enable Javascript](./media/B2C_SignInSignUp_EnableJavascript.png)

We'll come back to this policy once we have built out the custom pages to finish the policy setup. Close out of the policy to return to the **User Flows (policies)** page of the Azure portal.

### Configure the "Profile editing" policy

To configure the "Profile editing" policy, do the following.

1. Click **New user flow**, then in the **Recommended** section, select the **Profile editing** policy.
1. Enter a name for the policy (for example, "B2C_1_EditProfile"). 
1. Select the **Identity Providers** used for the policy (for example, **Local Account SignIn**). **Local Account SignIn** must be chosen at a minimum.
1. In the **Collect attribute** column, select **Email Addresses** and **Surname**.
1. In the **Return claim** column, select **Email Addresses**, **Given Name**, **Identity Provider**, **Surname**, and **User's Object ID**.
1. Click **OK** to create the policy.
1. Double-click the new policy name, then in the navigation pane click **Properties.**.
1. For **Enable JavaScript enforcing page layout (preview)**, select **On**.

We'll come back to this policy once we have built out the custom pages to finish the Policy setup. Close out of the policy to return to the **User Flows (policies)** page in the Azure portal.

### Configure the "Password reset" policy

To configure the "Password reset" policy, do the following.

1. Click **New user flow**, then in the **Preview** section, select the **Password reset v1.1** policy.
1. Enter a name for the policy (for example, "B2C_1_ForgetPassword"). 
1. In the **Identity Providers** section, select **Reset password using email address**.
1. In the **Return claim**column, select **Email Addresses,** **Given Name**, **Surname**, and **User's Object ID**.
1. Click **OK** to create the policy.
1. Double-click the new policy name, then in the navigation pane click **Properties.**.
1. For **Enable JavaScript enforcing page layout (preview)**, select **On**.

The following image shows the **Preview** section of the **Select a user flow type** screen.   

 ![Password Reset v1.1 menu](./media/B2C_ForgetPassword_Menu.png)
The following image shows the **Application claims** screen with the correct claims selected.

![Password Reset Claims](./media/B2C_ForgetPassword_Attributes.png)

We'll come back to this policy once we have built out the custom pages to finish the Policy setup. Close out of the policy to return to the **User Flows (policies)** page in the Azure portal.

## Build the custom pages

To build the custom pages to handle user logins, do the following.

1. In Commerce authoring tools, navigate to your site. 
1. Build five templates and five pages as follows:
    - A 'Sign In' template and page that use the 'Sign in' module.
    - A 'Sign Up' template and page that use the 'Sign up' module.
    - A 'Password Reset' template and page that use the 'Password reset' module.
    - A 'Password Reset verification' template and page that use the 'Password reset verification' module.
    - A 'Profile Edit' template and page that use the 'Account profile edit' module

When building the pages, do the following.

- Use a layout and style that best suits your business needs per page or module.
- Publish all pages and URLs to utilize in the AAD B2C setup.
- Once published, collect the URLs to use for the AAD B2C policy configurations. Each URL will be used with a `?preloadscripts=true` suffix added.

>[!IMPORTANT]
>Do not reuse universal headers and footers with relative links. As these pages will be hosted in the AAD B2C domain when in use, only absolute URLs should be used for any links.

## Configure AAD B2C policies with custom page information 

Navigate back to the Azure Portal AAD B2C page and go to the **User Flows (policies)** menu.

### Update the "Sign up and sign in" policy with custom page information

To update the "Sign up and sign in" policy with custom page information, do the following.

1. In the previously-built **Sign in and sign up** policy, go to the **Page layouts** section. 
1. Select the **Unified sign up or sign in page** layout.
1. For **Use custom page content**, select **Yes**.
1. In the **Custom page URI** box, enter your full sign-in URL with the "?preloadscripts=true" suffix (for example, `www.<*my domain*>.com/sign-in?preloadscripts=true`).
1. In the **Page Layout Version (Preview)** dropdown list, select **1.2.0**.
1. Select the **Local account sign up page** layout.
1. For **Use custom page content**, select **Yes**.
1. In the **Custom page URI** box, enter your full sign-in URL with the "?preloadscripts=true" suffix (for example, `www.<*my domain*>.com/sign-in?preloadscripts=true`).
1. In the **Page Layout Version (Preview)** dropdown list, select **1.2.0**.
1. In the **User attributes** section, do the following.
    1. For **Email Address**, **Given Name**, and **Surname**, select **No** for **Requires Verification".
    1. For **Given Name** and **Surname**, select **No** for **Optional**.

The following image show the **Page layouts** screen.  

![Sign Up Page Policy Configuration](./media/B2C_SignUp_PageURLConfig.png)

### Update the "Profile editing" policy with custom page information

To update the "Profile editing" policy with custom page information, do the following.

1. In the previously-built **Profile Editing** policy, go to the **Page layouts** section.
1. Select the **Profile edit page"** layout.
1. For **Use custom page content**, select **Yes**.
1. In the **Custom page URI** box, enter your full sign-in URL with the "?preloadscripts=true" suffix (for example, `www.<*my domain*>.com/sign-in?preloadscripts=true`).
1. In the **Page Layout Version (Preview)** dropdown list, select **1.2.0**.
1. In the **User attributes** section, do the following.
    1. For **Email Address**, **Given Name**, select **No** for **Requires Verification".
    1. For **Given Name** and **Surname**, select **No** for **Optional**.
    
### Update the "Password reset" policy with custom page information

To update the "Password reset" policy with custom page information, do the following.

1. In the previously-built **Password Reset** policy, go to the **Page layouts** section.
1. Select the **New password page** layout.
1. For **Use custom page content**, select **Yes**.
1. In the **Custom page URI** box, enter your full sign-in URL with the "?preloadscripts=true" suffix (for example, `www.<*my domain*>.com/sign-in?preloadscripts=true`).
1. In the **Page Layout Version (Preview)** dropdown list, select **1.2.0**.
1. Select the **Account verification page" Layout
1. For **Use custom page content**, select **Yes**
1. In the **Custom page URI** box, enter your full sign-in URL with the "?preloadscripts=true" suffix (for example, `www.<*my domain*>.com/sign-in?preloadscripts=true`).
1. In the **Page Layout Version (Preview)** dropdown list, select **1.2.0**.

## Customize default text strings for labels and descriptions

Starter kit login modules are prepopulated with default text strings for the labels and descriptions. These items can be customized in the SDK by updating the values in the login module's global.json file.

For example, the text for the forget password link showing as "Forgotten password?" can be edited in the the starter kit login module's global.json file of  to "Forgot Password?".

The following image shows default "Forgotten password?" text string on the sign-in screen.  

![Sign Up Module Strings](./media/B2C_SignUp_ModuleFace.png)

The following image shows where text strings can be edited in the login module's global.json file.  

![SDK Global JSON editing string labels for modules](./media/B2C_CustomizingStringsForModule.png)

Once updated and published, the changes will appear in the displaying module both in Commerce and on the live sign-in page.
