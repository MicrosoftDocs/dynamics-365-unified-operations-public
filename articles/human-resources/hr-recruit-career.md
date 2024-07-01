---
# required metadata

title: Configure the careers site in the HR recruit app
description: This article describes how to configure the careers site in the HR recruit app.
author: twheeloc
ms.date: 07/01/2024
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

# Configure the careers site in the HR recruit app

[This article is prerelease documentation and is subject to change.]

This article describes how to configure the careers site in the HR recruit app

You can change many aspects of your careers site, such as the background, introduction, images, privacy policy, site name and so on. To do this, follow these steps:

1.	Go to Power Page. 
2.	Select your active site 
3.	Click on **…** 
4.	Select **Power Pages management**.
5.	Select **Content snippet** from left menu panel.
6.	To add the privacy link, search for ‘Account/SignIn/PrivacyLink’ .
7.	Click **Account/SignIn/PrivacyLink**, provide the value.
8.	Search for **Site name**.
9.	Click **Site name** and change the value to your company name.

You can update the **Sign-in** page, **Identity providers**, ans **Candidate profile** page labels.

### External identity providers

Users can sign in with different put-of-box identity providers on the website. The administrator needs to set these up to show on the login page. 

To configure, follow these steps:
1.	Go to Power Page. 
2.	Select your active site and click **Edit**.
3.	Go to **Setup** on left panel and select **Identity providers**.
4.	You can enable or disable any provider. The **Local sign in** and **Azure Active Directory** configuration for the providers contain dummy values. 
For more informationabout how to setup providers, see [Set up an OAuth 2.0 provider](xxxxxx).

### Enable email accounts to send notifications

To send email alerts in different situations in the Careers site, forgot password, confirm or create email accounts, follow these steps:
Prerequisite: You must finish setting up your email accounts.
1.	Sign in to Power Apps and select the environment with your Recruiting add-on app installed.
2.	In the left pane, select **Solutions**. From the list of solutions, select **Default solution**.
3.	In the left pane, select **Processes**. From the list, open **Send password reset to contact**.
4.	Deactivate the process.
5.	Open **Set properties**.
6.	Change the **From** field in the **Send email** page. 
7.  Select the user created in prerequisite step. 
8.  Click **Save** and **Close**.
9.	Activate back the process.
10.	Follow steps 5-8 for the **Send email confirmation to contact** process.

