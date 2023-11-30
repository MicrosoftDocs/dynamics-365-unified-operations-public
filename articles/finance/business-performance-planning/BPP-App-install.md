---
# required metadata

title: Install the Business performance planning application
description: This article describes how to install the Business performance planning application in Microsoft Dynamics 365 Finance.
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
# Install the Business performance planning application

This article describes how to install the Business performance planning application. You must also install Power BI visuals to fully use the planning application. To learn more about installing Power BI visuals, see [Power BI visuals](power-bi/developer/visuals/).

## Install the planning application
Complete the following steps to install the planning application.

1, In the **Power Platform Admin Center**, in the navigation page, select **Environments**.
2. Select the environment on which you will install the planning application.
3. Select **Resources** > **Dynamics 365 apps**.
4. Select **Install app**, and in the list of apps, find and select **Dynamics 365 Finance business performance planning**.

> [!IMPORTANT]
> A Finance license is required to install the Business performance planning application. For more information about finance licensing, see [Finance pricing](https://dynamics.microsoft.com/en-us/finance/pricing/).

5. On the **Install** page, agree to the terms of service and select **Install**.
6. After installation is complete, navigate to and select the **Environment URL** for your environment. To find this, on the left navigation pane, select **Environments** and then select the environment where you installed the planning application. The environment URL is located in the **Details** section of the page.
7. The **Apps** page of the environment is available in the planning application. Select the application.

The home screen should appear.

Important! Before other users can use the business performance planning app it must be shared. Please review the documentation on assign security roles or people to the model-driven app here: [https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/share-model-driven-app\#assign-security-roles-or-people-to-a-model-driven-app](../../power-apps/maker/model-driven-apps/share-model-driven-app#assign-security-roles-or-people-to-a-model-driven-app). The security roles that should be associated with the business performance planning app are: Business performance planning administrator, Business performance planning contributor, Business performance planning power user, Business performance planning viewer

Important! The planning roles are not assigned to users by default, including the user who performed the install. You must assign users a Business performance planning role before accessing the application. If a role is not assigned you may not be able to access the home page or you may not be able create dimensions or cubes.

To assign the business performance planning roles to users, navigate to the home page of the environment by selecting the **Environment** option in the navigation pane within the **Power Platform Admin Center**. On the right side of the Environment form select **See all** under **Security roles.** The following planning roles will be listed:

Business performance planning administrator

Business performance planning contributor

Business performance planning power user

Business performance planning viewer

To assign users to the roles select the ellipses to the right of the role and choose members. You can add people to the role. Alternatively, you can navigate to the users form, and add roles from there.

## Delete the planning application
If you need to delete the planning application, follow these steps.

1.  In the planning application, delete all of the cubes.
2.  In the planning application, delete all of the dimensions.
1.  In **Microsoft Power Platform**, go to the **Maker Portal** for the environment, and then select **Solutions**.
2.  Select to view all solutions.
3.  To complete delete the solution, delete the solutions in the follow order:
    1.  Dynamics Extended Planning and Analysis Design
    2.  Dynamics Extended Planning and Analysis Controls
    3.  Dynamics Extended Planning and Analysts Power CAT
    4.  Dynamics Extended Planning and Analysis Support
    5.  Dynamics Extended Planning and Analysis SQL Functionality
    6.  [Microsoft](https://make.preprod.powerapps.com/environments/072ff55f-8d3a-e292-b124-88c671ed04f1/solutions/b392f266-1d4b-4149-8b57-22d811e1741f) XPnA Anchor
