---
# required metadata

title: Set up the careers site in the HR Recruiting app 
description: This article explains how to set up the careers site in the HR Recruiting app in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 6/11/2026
ms.topic: how-to
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-12-03
ms.dyn365.ops.version: Human Resources

---

# Set up the careers site in the HR Recruiting app

This article explains how to install and configure the careers site in the HR Recruiting app in Microsoft Dynamics 365 Human Resources. You can change many aspects of your careers site, such as the background, introduction, images, privacy policy, and site name.

## Install
>
>[!NOTE]
>You must install the Dynamics 365 Human Resources recruiting add-on app in Dataverse.

To install the Dynamics 365 Human Resources careers, follow these steps:

1. Go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Sign in as administrator.
1. Select your environment.
1. Go to Dynamics 365 apps.
1. Select **Install app**.
1. Search for and install Dynamics 365 Human Resources careers.

### Troubleshooting installation failures

**Recruiting add-on not found** error:

  1. Go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
  1. Sign in as administrator.
  1. Select your environment.
  1. Go to Dynamics 365 apps.
  1. Select **Install app**.
  6. Search for and install the Dynamics 365 Human Resources recruiting add-on.

Installing the new version of Careers requires deleting the previous version:

  1. Go to Power Apps > **Solutions** > **Managed solutions**.
  2. Find the **HCM Recruiting portal** solution and delete it. Remove any dependencies if present.
  3. After the deletion is completed successfully, proceed to reinstall Dynamics 365 Human Resources Careers from Power platform admin center.

**Languages not selected for careers** error:

  1. Go to the URL mentioned in the error message to open the **Settings** page in the Recruiting add-on application.
  2. Select the preferred languages from the dropdown menu.
  3. Select **Save**.
  4. Retry installing Dynamics 365 Human Resources careers from Power platform admin center.

### Upgrade careers with custom settings

Upgrading to a new career version overwrites your customizations. To avoid data loss, back up and restore your settings by using the following steps.

1. Back up the careers customization. For more information, see [Power platform pages](/power-platform/developer/cli/reference/pages#pac-pages-download).
1. Reinstall the current version:
1. Go to **Power Apps** > **Solutions** > **Managed solutions**.
1. Search for HCM Recruiting careers (msdyn_HCMRecruitingCareers) and delete it.
1. Remove any dependencies if present. Deleting msdyn_HCMRecruitingCareers enables you to reinstall the careers.
1. Install or update the Dynamics 365 Human Resources careers app from Power platform admin center.
1. To restore your customization, upload the previously downloaded code from step one. For more information, see [Power platform pages](/power-platform/developer/cli/reference/pages#pac-pages-upload). This action overrides the current code in the environment.

For more information, see [Microsoft Power Platform CLI pages command group](/power-platform/developer/cli/reference/pages).

### Enable careers to access Dynamics 365 Human resources virtual entities

To assign roles to the **Portal anonymous** user in Dynamics 365 Human Resources, follow these steps:

1. In Dynamics 365 Human Resources, go to **Users**.
1. Select the user, and assign roles. If this user doesn't exist, select another user or create a new one.
Assign the following roles:

- **Dataverse Virtual entity anonymous user**
- **Portal authenticated user for Recruitment**

>[!NOTE]
> The **Portal authenticated user for Recruitment** role is available in Dynamics 365 Human Resources version 10.0.45. For version 10.0.44, use the **Recruiting application** role.

1. Go to **System administration** > **Setup** > **System parameters** > **Power Apps Portals**.
1. Enter the user in the **Anonymous access user id** field.
1. Select **Save**.

[![System parameters.](./media/careerpara.png)](media/careerpara.png)
  
>[!Note]
> If the user is already assigned in the preceding screen, assign them the specified roles.

## Activate the careers site

**Prerequisites**

Dataverse must have the following installed:

- The Recruiting add-on app
- The Dynamics 365 Human Resources careers app  

To activate the careers site, follow these steps:

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/) as an admin.
1. Select your environment.
1. Select the **Inactive sites** tab.

> [!NOTE]
> If you can't view the inactive site, create a temporary site by using any available template. After creating a temporary site, you can access the inactive site.

1. Select **Reactivate** for **Recruiting-careers site** to activate the site.
1. Enter a name and web address for the website, and then select **Done**.
    > [!NOTE]
    > To ensure that future updates can be installed, don't modify the input of the **Reactivated website** field.

Site activation might take up to 10 minutes. After the site activates, it's available on the **Active sites** tab.

> [!IMPORTANT]
> After your site is activated, confirm that the version number is at least 9.6. If it's earlier than 9.6, contact Microsoft. To find the version, execute {siteUrl}/_services/about in the browser.

### Enable local login

To enable local login, follow these steps:

1. Sign in to Power Pages.
1. Select your active site, select the ellipsis (…), and then select **Power pages management**.
1. In the left pane, select **Site settings**.
1. Set the following sites to **True** if they're currently set to **False**:

- Authentication/Registration/Enabled
- Authentication/Registration/LocalLoginEnabled
- Authentication/Registration/OpenRegistrationEnabled

1. Save and publish the changes. Local sign-in and registration pages are visible on your Careers site.

For more information, see [Local authentication, registration, and other settings](/power-pages/security/authentication/set-authentication-identity).

### Set up Compliance link

To set up a compliance link, follow these steps:

1. Sign in to Power Pages.
1. Select your active site, select the ellipsis (…), and then select **Power pages management**.
1. In the left pane, select **Content snippets**.

- Add a Privacy link to the sign-in page
  - Search for and select **Account/SignIn/PrivacyLink**.
  - Enter the link in the **Value** section.

- Add a Privacy link in footer
  - Search for and select **Footer/PrivacyLink**.
  - Enter the link in the **Value** section.

- Add Terms link in footer
  - Search for and select **Footer/TermsOfUseLink**.
  - Enter the link in the **Value** section.

- Add copyright in footer
  - Search for and select **Footer/CopyrightLabel**.
  - Enter the link in the **Value** section.

## Configure external identity providers

Users can sign in by using different out-of-box identity providers on the website. The administrator must configure these identity providers so that they appear on the sign-in page.

To configure external identity providers, follow these steps:

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/).
1. Select your active site, and then select **Edit**.
1. In the left pane, select **Security**.
1. Select **Identity providers**.
1. You can enable or disable any provider. The **Local sign in** and **Azure Active Directory** configurations for the providers contain "dummy" values.

For more information about how to set up identity providers, see [Set up an OAuth 2.0 provider](/power-pages/security/authentication/oauth2-provider).

## Enable email accounts to send notifications

**Prerequisites:**

- You finish setting up your email accounts
- Local authentication is enabled

You can send email notifications in different situations on the careers site. For example, you can send them when users forget their password, for confirmation, or when users create email accounts.

To enable email accounts to send notifications, follow these steps:

1. Sign in to [Power Apps](https://make.powerapps.com/).
1. Select the environment where your Recruiting add-on app is installed.
1. In the left pane, select **Solutions**.
1. In the list of solutions, select **Default Solution**.
1. In the left pane, select **Processes**.
1. In the list, select **Send Password Reset To Contact**.
1. Deactivate the process.
1. Select **Set properties**.
1. On the **Send email** page, change the value of the **From** field.
1. Select the user that you created in the prerequisite step.
1. Select **Save** and then **Close**.
1. Reactivate the process.
1. Follow steps 6 through 12 for the **Send Email Confirmation To Contact** process.

### Reinstall careers with language change

>[!Note]
> Reinstalling erases all site components and removes any customizations.

To update career portal languages after installing Dynamics 365 Human Resources, delete the Dynamics 365 Human Resources careers solution.  

To delete the HCM Recruiting careers solution, follow these steps:

1. Go to Power Apps > **Solutions** > **Managed solutions**.
1. Search for **HCM Recruiting careers** and delete it. Remove any dependencies if present.
1. After deletion, update and save the languages list in the Dynamics 365 Human Resources Recruiting add-on **Settings** page.
1. Install the app again from Power platform admin center.
