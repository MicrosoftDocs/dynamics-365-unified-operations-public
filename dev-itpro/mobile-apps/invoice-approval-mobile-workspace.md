---
# required metadata

title: Invoice approvals mobile workspace
description: This topic provides information about the Invoice approvals mobile workspace. This workspace provides a list of invoices that have been assigned to you through the vendor invoice header workflow process. 
author: abruer 
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: sericks
# ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: abruer
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Enterprise edition, July 2017 update 
---

# Invoice approvals mobile workspace

[!include[banner](../includes/banner.md)]

This topic provides information about the **Invoice approvals** mobile workspace. This workspace provides a list of invoices that have been assigned to you through the vendor invoice header workflow process. 

This mobile workspace is intended to be used with the Microsoft Dynamics 365 for Unified Operations mobile app.

## Overview

The **Invoice approvals** mobile workspace lets Accounts payable clerks and managers view invoices that have been assigned to them as part of the vendor invoice header workflow process. You can view the invoice information, and even the line and distribution details, to help you make informed approval decisions. From the workspace, you can take action to move the invoice through the workflow process. 

## Prerequisites

Before you can use this mobile workspace, the following prerequisites must be met.

<table>
<thead>
<tr class="header">
<th>Prerequisite</th>
<th>Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update must be deployed in your organization.</td>
<td>System administrator</td>
<td>See <a href="../deployment/deploy-demo-environment.md">Deploy a demo environment</a>.
</td>
</tr>
<tr class="even">
<td>The <strong>Invoice approvals</strong> mobile workspace must be published.</td>
<td>System administrator</td>
<td>See <a href="/dynamics365/operations/dev-itpro/mobile-apps/publish-mobile-workspace">Publish a mobile workspace</a>.</td>
</tr>
</tbody>
</table>

## Download and install the mobile app

Download and install the Dynamics 365 for Unified Operations mobile app:

-   [For Android phones](https://go.microsoft.com/fwlink/?linkid=850662)
-   [For iPhones](https://go.microsoft.com/fwlink/?linkid=850663)

## Sign in to the mobile app

1.  Start the app on your mobile device.
2.  Enter your Microsoft Dynamics 365 URL.
3.  The first time that you sign in, you're prompted for your user name and password. Enter your credentials.
4.  After you sign in, the available workspaces for your company are shown. Note that if your system administrator publishes a new workspace later, you will have to refresh the list of mobile workspaces.

    [![Pull to refresh](./media/pull-to-refresh-list-of-workspaces-183x300.png)](./media/pull-to-refresh-list-of-workspaces.png)

## Approve invoices by using the Invoice approvals mobile workspace
1.	On your mobile device, select the **Invoice approvals** workspace.
2.	Select the invoice that has been assigned to you by the vendor invoice header workflow process.
3.	On the **Invoice details** page, review the invoice header information, such as the vendor and date information.
4.	Select a line on the invoice to view more detailed information about it in the **Invoice line details** view.
5.	In the **Invoice line details** view, select **Distributions** to show the line distributions. Here, you can view the accounting for the invoice line. The information that is shown includes the financial dimensions and the main account.
6.	On the **Invoice details** page, select **Distributions** to show all distributions. Here, you can view the accounting for the whole invoice. The information that is shown includes the financial dimensions and the main accounts. 
7.	Select **Attachments** to view any notes or files that are attached to the invoice.
8.	On the **Invoice details** page, select the appropriate workflow action to complete your review process.
9.	Select **Done**.
