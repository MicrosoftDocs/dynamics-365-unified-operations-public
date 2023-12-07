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

This article describes how to install the Business performance planning application. You must also install Power BI visuals to fully use the planning application. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals/).

## Install the planning application
Complete the following steps to install the planning application.

1, In the **Power Platform Admin Center**, in the navigation page, select **Environments**.
2. Select the environment on which you will install the planning application.
3. Select **Resources** > **Dynamics 365 apps**.
4. Select **Install app**, and in the list of apps, find and select **Dynamics 365 Finance business performance planning**.

> [!IMPORTANT]
> A standard Finance license is required to install the Business performance planning application.  To perform any planning operations, you will need a finance premium license. For more information about finance licensing, see [Finance pricing](https://dynamics.microsoft.com/en-us/finance/pricing/).

5. On the **Install** page, agree to the terms of service and select **Install**.
6. After installation is complete, navigate back to the **Environments** page in the **Power Power admin center**  and select the **Environment URL** for your environment. To find this, on the left navigation pane, select **Environments** and then select the environment where you installed the planning application. The environment URL is located in the **Details** section of the page.
7. Once the environment URL is selected, the **Apps** page is displayed.  
8. Select the **Business performance planning** application.

> [!IMPORTANT]
> Before the planning application can be used, you must assign users to the **Business performance planning** role. The planning roles aren't assigned to anyone by default, including whoever performed the install. For more details about assigning security roles or people to the model-driven app, see [Assign security roles or people to a model-driven app](/power-apps/maker/model-driven-apps/share-model-driven-app#assign-security-roles-or-people-to-a-model-driven-app). 

9. To assign the business performance planning roles to users, in the **Power Platform Admin Center**, in the navigation pane, select **Environments** and then select the environment on which you installed the planning application.
10. On the home page of the environment, select **Security roles** > **See all**. The following **Business performance planning** roles should be listed:

    - Business performance planning administrator
    - Business performance planning contributor
    - Business performance planning power user
    - Business perfromance planning viewer


11. Select the ellipses to the right of each role, and select users to add to the role. Alternatively, you can navigate to the **Users** page, and add roles from there.

## Delete the planning application
If you need to delete the planning application, follow these steps.

1.  In the planning application, delete all of the cubes.
2.  In the planning application, delete all of the dimensions.
3.  In **Microsoft Power Platform**, go to the **Maker Portal** for the environment, and then select **Solutions**.
4.  Select to view all solutions.
5.  To delete the entire solution, delete the solutions in the following order:
    1.  Dynamics Extended Planning and Analysis Design
    2.  Dynamics Extended Planning and Analysis Controls
    3.  Dynamics Extended Planning and Analysts Power CAT
    4.  Dynamics Extended Planning and Analysis Support
    5.  Dynamics Extended Planning and Analysis SQL Functionality
    6.  [Microsoft](https://make.preprod.powerapps.com/environments/072ff55f-8d3a-e292-b124-88c671ed04f1/solutions/b392f266-1d4b-4149-8b57-22d811e1741f) XPnA Anchor

> [!IMPORTANT]
> If the finance premium license is terminated, data will be retained until the solution is removed.
