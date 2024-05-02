---
title: Install the business performance planning app
description: Learn how to install the business performance planning app in Microsoft Dynamics 365 Finance, including a process on deleting the app as well.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 11/28/2023
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: Human Resources
---

# Install the business performance planning app

This article describes how to install the business performance planning app. To fully use the app, you must also install Microsoft Power BI visuals. For more information about how to install Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals/).

## Install the app

Follow these steps to install the business performance planning app.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/), and then, on the navigation pane, select **Environments**.
1. Select the environment where you're installing the app.
1. Select **Resources** \> **Dynamics 365 apps**.
1. Select **Install app**, and then, in the list of apps, find and select **Dynamics 365 Finance business performance planning**.

    > [!IMPORTANT]
    > A standard Dynamics 365 Finance license is required to install the business performance planning app. To perform any planning operations, you must have a Finance premium license. For more information about Finance licensing, see [Finance pricing](https://dynamics.microsoft.com/finance/pricing/).

1. On the **Install** page, agree to the terms of service, and then select **Install**.
1. After installation is completed, select **Environments** on the left navigation pane, and then select the environment where you installed the app. In the **Details** section of the page, find and select the **Environment URL** value for your environment.
1. The **Apps** page is opened. Select the **Business performance planning** app.

    > [!IMPORTANT]
    > Before the app can be used, you must assign users to the **Business performance planning** roles. These roles aren't assigned to anyone by default, not even to the person who installed the planning application. For more information about how to assign security roles or people to a model-driven app, see [Assign security roles or people to a model-driven app](/power-apps/maker/model-driven-apps/share-model-driven-app#assign-security-roles-or-people-to-a-model-driven-app).

1. To assign the **Business performance planning** roles to users, in Power Platform admin center, select **Environments** on the navigation pane, and then select the environment where you installed the application.
1. On the home page of the environment, select **Security roles** \> **See all**. The following **Business performance planning** roles should be listed:

    - Business performance planning administrator
    - Business performance planning contributor
    - Business performance planning power user
    - Business performance planning viewer

1. Select the ellipsis (**&hellip;**) to the right of each role, and select users to add to the role. Alternatively, you can go to the **Users** page and add roles from there.

## Delete the app

If you must delete the business performance planning app, follow these steps.

1. In the app, delete all the cubes and then all the dimensions.
1. In Microsoft Power Platform, open the maker portal for the environment, and select **Solutions**.
1. Select to view all solutions.
1. To delete the whole solution, delete the solutions in the following order:

    1. Dynamics Extended Planning and Analysis Design
    1. Dynamics Extended Planning and Analysis Controls
    1. Dynamics Extended Planning and Analysts Power CAT
    1. Dynamics Extended Planning and Analysis Support
    1. Dynamics Extended Planning and Analysis SQL Functionality
    1. [Microsoft](https://make.preprod.powerapps.com/environments/072ff55f-8d3a-e292-b124-88c671ed04f1/solutions/b392f266-1d4b-4149-8b57-22d811e1741f) XPnA Anchor

> [!IMPORTANT]
> If the Finance premium license is terminated, data will be retained until the solution is removed.
