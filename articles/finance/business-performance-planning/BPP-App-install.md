---
# required metadata

title: Install Microsoft Dynamics 365 Finance business performance planning application
description: This article describes how to install the Microsoft Dynamics 365 Finance business performance planning application.
author: ShielaSogge
ms.date: 11/28/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2023-12-03
ms.dyn365.ops.version: Human Resources

---
# Installing the business performance planning application

This article describes how to install the business performance planning application. You must also install the Power BI visuals to fully use business performance planning. Please review the Power BI visual install documentation here: **xxxx.xxxx – link to that doc.**

## Install business performance planning

In **Power Platform admin center** navigate to the environment that you would like to install planning on by selecting **Environments** in the navigation pane.

Select the environment that you would like to install planning on.

Select **Resources** from the menu, and then select Dynamics 365 apps

Select **Install app** from the menu.

Select **Dynamics 365 Finance business performance planning** from the list of apps.

Important! You must have purchased a Finance license to view and select the Dynamics 365 for Finance business performance planning application for install. Without having a Finance license, the app will not be visible in the Power Platform Admin Center. Learn more about Finance licensing here: [Finance Pricing \| Microsoft Dynamics 365](https://dynamics.microsoft.com/en-us/finance/pricing/)

Once in the installation form, the agreement to the **terms of service** must be selected before the **install** button will be enabled.

Once the installation has completed, navigate to the **Environment URL** for your environment. (This can be found by selecting Environments in the left navigation pane, and then selecting the environment where planning is installed. The environment URL will be in the Details section of the form.)

Select the environment URL. The Apps form of the environment will display the **Business performance planning** app. Select the application.

The home screen should appear.

Important! Before other users can use the business performance planning app it must be shared. Please review the documentation on assign security roles or people to the model-driven app here: [https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/share-model-driven-app\#assign-security-roles-or-people-to-a-model-driven-app](../../power-apps/maker/model-driven-apps/share-model-driven-app#assign-security-roles-or-people-to-a-model-driven-app). The security roles that should be associated with the business performance planning app are: Business performance planning administrator, Business performance planning contributor, Business performance planning power user, Business performance planning viewer

Important! The planning roles are not assigned to users by default, including the user who performed the install. You must assign users a Business performance planning role before accessing the application. If a role is not assigned you may not be able to access the home page or you may not be able create dimensions or cubes.

To assign the business performance planning roles to users, navigate to the home page of the environment by selecting the **Environment** option in the navigation pane within the **Power Platform Admin Center**. On the right side of the Environment form select **See all** under **Security roles.** The following planning roles will be listed:

Business performance planning administrator

Business performance planning contributor

Business performance planning power user

Business performance planning viewer

To assign users to the roles select the ellipses to the right of the role and choose members. You can add people to the role. Alternatively, you can navigate to the users form, and add roles from there.

## Delete Business performance planning

If you must delete Business performance planning, follow these steps.

1.  In the planning application, delete all cubes.
2.  In the planning application, delete all dimensions.
1.  In the Microsoft Power Platform, go to the Maker Portal for the environment, and then select Solutions
2.  Select to view All Solutions
3.  To complete delete the solution, delete the solutions in the follow order:
    1.  Dynamics Extended Planning and Analysis Design
    2.  Dynamics Extended Planning and Analysis Controls
    3.  Dynamics Extended Planning and Analysts Power CAT
    4.  Dynamics Extended Planning and Analysis Support
    5.  Dynamics Extended Planning and Analysis SQL Functionality
    6.  [Microsoft](https://make.preprod.powerapps.com/environments/072ff55f-8d3a-e292-b124-88c671ed04f1/solutions/b392f266-1d4b-4149-8b57-22d811e1741f) XPnA Anchor
