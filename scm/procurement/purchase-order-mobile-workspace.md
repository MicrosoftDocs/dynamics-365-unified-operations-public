---
# required metadata

title: Purchase order approval mobile workspace
description: This topic describes how purchasing agents can use the Vendor portal to collaborate with external vendors during the purchase order confirmation process. This information applies only to the February 2016 &amp; May 2016 versions of Dynamics AX.
author: BibiSp
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: PurchTable, PurchVendorPortalRequests
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: bis
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 30211
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2017-06-15
ms.dyn365.ops.version: AX 7.0.2

---

# Purchase order approval mobile workspace

[!include[banner](../includes/banner.md)]


This topic provides information about the Purchase order approval mobile workspace that is available for the Microsoft Dynamics 365 for Operations mobile app. 
The workspace lets you view and respond to purchase orders with actions such as approve or reject.
 

# Overview of the Purchase order approval mobile workspace
Purchase orders that requires approval are taken through an approval workflow. The workflow can include different steps that require one or more people to take action. This could be to complete a task or approve a purchase order. 

The purchase order mobile workspace enable you to easily view and respond to purchase orders from your mobile device. The workspace also allows you to take the same workflow actions as from the Dynamics 365 for Financials and Operations web client.

## Prerequisites
Before you implement the Purchase order approval mobile workspace, make sure that your system administrator has completed the following prerequisites.

| Prerequisite  | Role | Description                                                               |
|---------------|------|---------------------------------------------------------------------|
| Microsoft Dynamics 365 for Operations version 1611 with platform update 3 or later must be implemented.  | System administrator | If you don’t already have Dynamics 365 for Operations deployed in your organization, your system administrator should refer to this article <a href="/dev-itpro/deployment/deploy-demo-environment.md"> [Deploy a Microsoft Dynamics 365 for Operations demo environment](../active-directory/deploy-demo-environment.md)
| xxx    | xxx |

## Download and install the Dynamics 365 for Operations mobile app
Download and install the Dynamics 365 for Financials and Operations mobile app from your mobile app store.
 - For Android: https://play.google.com/store/apps/details?id=com.microsoft.dynamics365.operations.
 - For iPhone: https://itunes.apple.com/us/app/dynamics-365-for-operations/id1180836730?mt=8

## Sign in to the Dynamics 365 for Financials and Operations mobile app

1. Start the app on your mobile device.
2. Enter your Dynamics 365 for Operations URL.
3. If this is the first time that you sign in, you’re prompted for the user name and password for your Dynamics 365 for Operations account. Enter your credentials.
4. Select the company code.
When you have signed in, you'll see the available workspaces for your company. Note that if your system administrator subsequently publishes a new workspace, you can pull to refresh the list of mobile workspaces.

[![po-workspaces](./media/po-workspaces.png)(./media/po-workspaces.png

## View orders assigned to me
1.	On your mobile device, select the **Purchase order approval** workspace.
2.	Select **Orders assigned to me** to show all the purchase orders where you have been requested to take an action in the purchase order approval workflow.
3. Select an order. On **Order details** you will see the order header information and lines. You can also find guidelines from the workflow task.
4.	Select **Accounting distributions** to see **Header accounting distributions**.
5.	Return to **Order details** and select a line. From the order line details, you can also explore the line-specific accounting distributions.

## Complete an action on the purchase order
When you have viewed the purchase order that is assigned to you and read the workflow instructions, you should be ready to complete an action.
1. On your mobile device, select the **Purchase order approval** workspace.
2.	Select **Orders assigned to me** to show all the purchase orders where you have been requested to take an action in the purchase order approval workflow.
3.	Select an order, and see the Order details page.
4.	Select **Actions** to display the following actions depending on the task that has been assigned to you: 

>| Task actions  | Approval actions |
>|---------------|------|
>| Complete | Approve |
>| Return | Reject |
>| Request change |Request change |
>| Delegate| Delegate|
5. Select the appropriate action.
6.	Enter a comment on the **Complete task** page. Note that if you choose to delegate, you must select a user to delegate the task to.
7.	Select **Done**. When you have refreshed, your workspace the purchase order will no longer be in your list. 
