---
# required metadata

title: Access business performance analytics
description: This article explains how to access business performance analytics.
author: jkhaira7
ms.author: jkhaira
ms.reviewer: twheeloc 
ms.date: 09/20/2023
ms.topic: conceptual
ms.prod: 
ms.technology:
ms.custom:
audience: Application User
ms.application-unique-name: msdyn_BusinessPerformanceAnalytics
ms.audience: administrator
---

# Access business performance analytics

[!include [banner](../includes/banner.md)]

This article explains how to access business performance analytics.

## Access business performance analytics as an administrator

After business performance analytics is installed, there are several ways to access the app:

- In [Power Platform admin center](https://admin.powerplatform.microsoft.com/), go to the environment where you installed the app, and find the environment URL.
- In the Power Platform maker portal, go to **Apps**, and find and select **Business performance analytics**.

### Access business performance analytics from finance and operations apps

To open business performance analytics directly from Dynamics 365 finance and operations apps, first confirm that the following prerequisites are met:

- In Power Platform admin center, **Finance and Operations in Dataverse** must be enabled.
- The **Basic user** role must be assigned to the user in Dataverse.
- The user must be a business performance analytics app user.

After these prerequisites are met, the administrator can use security roles and privileges to assign access to the **Business performance analytics** tile in finance and operations apps.

### Share business performance analytics with users

To share the business performance analytics app with users, first confirm that those users are set up as business performance analytics users in the app, and that their security is set up.

1. In business performance analytics, select **Business performance analytics (preview)**.
2. The dialog box that appears includes a **Published apps** list. Find **Business performance analytics (preview)** in the list, select the three dots, and then select **Manage roles**.
3. Expand **App URL suffix**, and enter a name to use in the custom URL that you share with business performance analytics users.
4. Copy the URL that's generated, and share it with app users.
