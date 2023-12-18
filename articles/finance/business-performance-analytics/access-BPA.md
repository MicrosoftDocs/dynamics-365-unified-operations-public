---
# required metadata

title: Access business performance analytics
description: This article explains how to access business performance analytics.
author: jkhaira7
ms.author: jkhaira
ms.reviewer: twheeloc 
ms.date: 12/12/2023
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

A shortcut to access business performance analytics in Dynamics 365 finance and operations will be visible to users with one of the following duties assigned:  
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


To open business performance analytics directly from Dynamics 365 finance and operations apps, first confirm that the following prerequisites are met:

- In Power Platform admin center, **Finance and Operations in Dataverse** must be enabled.
- The **Basic user** role must be assigned to the user in Dataverse.
- The user must be a business performance analytics app user.

If these prerequisites aren't met, click on the business performance analytics icon in the apps section redirects the user to a public document explaining the business performance analytics functionality. If these prerequisites are met, clicking on the business performance analytics icon redirects the user to the business performance analytics app. 
The administrator can adjust the who can view the business performance analytics icon by removing the privileges associated with the duties assigned to a given user. Or, using feature management so that users can no longer view the Apps section. The administrator can also use security roles and privileges to assign access to the Business performance analytics icon to additional users and roles in Dynamics 365 finance and operations.


After these prerequisites are met, the administrator can use security roles and privileges to assign access to the **Business performance analytics** tile in finance and operations apps.

### Share business performance analytics with users

To share the business performance analytics app with users, first confirm that those users are set up as business performance analytics users in the app, and that their security is set up.

1. In business performance analytics, select **Business performance analytics (preview)**.
2. The dialog box that appears includes a **Published apps** list. Find **Business performance analytics (preview)** in the list, select the three dots, and then select **Manage roles**.
3. Expand **App URL suffix**, and enter a name to use in the custom URL that you share with business performance analytics users.
4. Copy the URL that's generated, and share it with app users.
