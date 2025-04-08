---
# required metadata

title: Configure the careers site in the HR Recruiting app (preview)
description: This article explains how to configure the careers site in the HR Recruiting app in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 08/23/2024
ms.topic: article
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

# Configure the careers site in the HR Recruiting app (preview)

[This article is prerelease documentation and is subject to change.]

This article explains how to configure the careers site in the HR Recruiting app in Microsoft Dynamics 365 Human Resources.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

You can change many aspects of your careers site, such as the background, introduction, images, privacy policy, and site name.

To configure the careers site, follow these steps.

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/).
1. Select your active site, select the ellipsis (**&hellip;**), and then select **Power Pages Management**.
1. In the left pane, select **Content Snippets**.
1. To add a privacy link, search for **Account/SignIn/PrivacyLink**.
1. Select **Account/SignIn/PrivacyLink**, and provide the value.
1. Search for **Site name**.
1. Select **Site name**, and change the value to your company name.

You can update the sign-in page, identity providers, and labels on the **Candidate profile** page.

## Configure external identity providers

Users can sign in by using different out-of-box identity providers on the website. The administrator must configure these identity providers so that they appear on the sign-in page.

To configure external identity providers, follow these steps.

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/).
1. Select your active site, and then select **Edit**.
1. In the left pane, select **Security**.
1. Select **Identity providers**.
1. You can enable or disable any provider. The **Local sign in** and **Azure Active Directory** configurations for the providers contain "dummy" values.

For more information about how to set up identity providers, see [Set up an OAuth 2.0 provider](/power-pages/security/authentication/oauth2-provider).

## Enable email accounts to send notifications

**Prerequisite:** You must finish setting up your email accounts.

Email notifications can be sent in different situations on the careers site. For example, they can be sent when users forget their password, for confirmation, or when users create email accounts.

To enable email accounts to send notifications, follow these steps.

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
