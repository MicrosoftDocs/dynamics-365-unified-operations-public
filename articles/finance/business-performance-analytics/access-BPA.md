---
title: Access Business performance analytics
description: Learn about how to access Business performance analytics, including an outline on how to share performance analytics with users.
author: jkhaira7
ms.author: jkhaira
ms.topic: conceptual
ms.custom:
ms.date: 05/12/2024
ms.reviewer: twheeloc 
audience: Application User
---

# Access Business performance analytics

[!include [banner](../includes/banner.md)]
[This article is prerelease documentation and is subject to change.]

This article explains how to access Business performance analytics.

## Access Business performance analytics as an administrator

After Business performance analytics is installed, there are several ways to access the app:

- In [Power Platform admin center](https://admin.powerplatform.microsoft.com/), go to the environment where you installed the app, and find the environment URL.
- In the Power Platform maker portal, go to **Apps**, and find and select **Business performance analytics**.

### Access Business performance analytics from finance and operations apps

A shortcut to access Business performance analytics in Dynamics 365 finance and operations are visible to users with one of the following duties assigned:  
 - View manage bank accounts workspace
 - Maintain budget plans
 - View cash flow all companies workspace
 - View cash flow current company workspace
 - View vendor invoice entry workspace
 - Maintain purchase orders
 - VendPaymentWorkspaceInquire
 - View vendor invoice entry workspace
 - View vendor profile
 - Maintain vendor requests for quotations replies
 - BudgetTrackingWorkspaceMaintain
 - Maintain vendor collaboration invoices
 - GeneralJournalEntryWorkspaceInquire
 - CustomerInvoiceWorkspaceView
 - CustPaymentWorkspaceView
 - Customer credit and collections
 - Configure Electronic reporting configuration
 - View CFO overview workspace
 - View financial insights current company
 - View financial period close processes
 - Inquire into fixed assets


To open Business performance analytics directly from Dynamics 365 finance and operations apps, confirm the following prerequisites are met:

1. Go to https://admin.powerplatform.microsoft.com/
2.	Select **Environments** from the left hand menu.
3.	Select the environment where business performance analytics is installed.
4.	Select **Settings** > **Users**
5.	For the users who should have access to Business performance analytics, ensure that the **Basic user** security role is assigned to them

If these prerequisites aren't met, click on the Business performance analytics icon in the apps section redirects the user to a public document explaining the Business performance analytics functionality. If these prerequisites are met, clicking on the Business performance analytics icon redirects the user to the Business performance analytics app. 
The administrator can adjust the who can view the Business performance analytics icon by removing the privileges associated with the duties assigned to a given user. Or, using feature management so that users can no longer view the Apps section. The administrator can also use security roles and privileges to assign access to the Business performance analytics icon to additional users and roles in Dynamics 365 finance and operations.


After these prerequisites are met, the administrator can use security roles and privileges to assign access to the **Business performance analytics** tile in finance and operations apps.

### Share Business performance analytics with users

To share the Business performance analytics app with users, first confirm that those users are set up as Business performance analytics users in the app, and that their security is set up.

1. In Business performance analytics, select **Business performance analytics (preview)**.
2. The dialog box that appears includes a **Published apps** list. Find **Business performance analytics (preview)** in the list, select the three dots, and then select **Manage roles**.
3. Expand **App URL suffix**, and enter a name to use in the custom URL that you share with Business performance analytics users.
4. Copy the URL that's generated, and share it with app users.
