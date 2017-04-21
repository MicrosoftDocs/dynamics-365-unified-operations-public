---
# required metadata

title: Expense management mobile workspace
description: This topic provides information about the Expense management mobile workspace that is available for the Microsoft Dynamics 365 for Operations mobile app. This workspace lets users capture and upload a receipt, so that they can attach it to an expense report later. The mobile workspace also lets users quickly create an expense line by using an attached receipt.
author: annbe
manager: AnnBe
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: end user, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 274023
ms.assetid: 3605eda1-a7ed-4675-8031-5279c5a8f5e4
ms.search.region: Global
# ms.search.industry: 
ms.author: annbe
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Expense management mobile workspace
"[!include[banner](../includes/banner.md)]"


This topic provides information about the Expense management mobile workspace that is available for the Microsoft Dynamics 365 for Operations mobile app. This workspace lets users capture and upload a receipt, so that they can attach it to an expense report later. The mobile workspace also lets users quickly create an expense line by using an attached receipt.

Overview of the Expense management mobile workspace
---------------------------------------------------

Many organizations require that a copy of a receipt be attached to a travel-related or business-related expense report that an employee submits for reimbursement. The **Expense management** mobile workspace lets users quickly create new expense lines on the mobile device of their choice by using an attached photo of a receipt. Alternatively, users can capture a photo of a�receipt and then attach it to an expense report later. Specifically, the **Expense management** mobile workspace enables a user to:

-   Take a photo of a receipt, and upload it to Microsoft Dynamics�365 for Operations. A user�can then attach that photo to an expense report later.
-   Upload a file as a captured receipt. A user can then attach that file to an expense report later.
-   Create a new expense line by using an attached receipt. A user can then add the line item to an expense report later, and submit it for approval and reimbursement.

The remaining sections of this topic explain how to implement and use the **Expense management** mobile workspace.

## Prerequisites
Before you implement the **Expense management** mobile workspace, make sure that your system administrator has completed the following prerequisites.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Prerequisite</th>
<th>Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Microsoft Dynamics�365 for Operations version�1611 with platform update�3 or later must be implemented.</td>
<td>System administrator</td>
<td>If you don�t already have Dynamics�365 for Operations deployed in your organization, your system administrator should see <a href="http://ax.help.dynamics.com/en/wiki/deploy-an-ax7-demo-environment/">Deploy a Microsoft Dynamics�365 for Operations demo environment</a>.</td>
</tr>
<tr class="even">
<td>KB�4019015 must be implemented.</td>
<td>System administrator</td>
<td>KB�4019015 (an X++ update or metadata hotfix) contains four mobile workspaces for supply chain management. To implement�KB 4019015, your system administrator must follow these steps:
<ol>
<li>Download KB�4019015 from Microsoft Dynamics Lifecycle Services (LCS).</li>
<li><a href="https://ax.help.dynamics.com/en/wiki/configuring-and-installing-a-metadata-hotfix-package/">Install the metadata hotfix</a>.</li>
<li><a href="https://ax.help.dynamics.com/en/wiki/create-and-apply-a-deployable-package/">Create a deployable package</a> that contains the <strong>ApplicationSuite</strong> and <strong>ExpenseMobile</strong> model, and then upload the deployable package to LCS.</li>
<li><a href="https://ax.help.dynamics.com/en/wiki/apply-a-deployable-package-on-a-dynamics-ax-system/">Apply the deployable package</a> to your Dynamics�365 for Operations system.</li>
</ol></td>
</tr>
<tr class="odd">
<td>The <strong>Expense management</strong> mobile workspace must be published to the Dynamics�365 for Operations mobile app.</td>
<td>System administrator</td>
<td><ol>
<li>Start Dynamics�365 for Operations in your browser.</li>
<li>On the <strong>System parameters</strong> page, select <strong>Manage mobile workspaces</strong>.</li>
<li>Select the <strong>Expense management</strong>�workspace.</li>
<li>Click <strong>Publish mobile workspace</strong>.</li>
</ol></td>
</tr>
</tbody>
</table>

## Download and install the Dynamics�365 for Operations mobile app
Download and install the Dynamics 365 for Operations mobile app from your mobile app store.

-   For Android: [Dynamics 365 for Operations on the Google Play Store](https://play.google.com/store/apps/details?id=com.microsoft.dynamics365.operations.mobile)
-   For iPhone: [Dynamics 365 for Operations on the iTunes apps store](https://itunes.apple.com/us/app/dynamics-365-for-operations/id1180836730?mt=8)
-   For Windows phone (Universal Windows Platform \[UWP\]): Coming soon!

## Sign in to the Dynamics�365 for Operations mobile app
1.  Start the app on your mobile device.
2.  Enter your Dynamics�365 for Operations URL.
3.  Enter the company to sign in to. For example, enter **USMF**.
4.  The first time that you sign in, you�re prompted for the user name and password for your Dynamics�365 for Operations account. Enter your credentials.
5.  After you sign in, you see the available workspaces for your company. Note that if your system administrator publishes a new workspace later, you can pull to refresh the list of mobile workspaces. [![Pull to refresh](./media/pull-to-refresh-list-of-workspaces-183x300.png)](./media/pull-to-refresh-list-of-workspaces.png)

## Capture a receipt by using the Expense management mobile workspace
1.  On your mobile device, select the **Expense management** workspace.
2.  Select **Capture receipt**.
3.  Select **Take photo** or **Choose image**.
4.  If you selected **Take photo**, follow these steps:
    1.  You're taken to the camera on your mobile device, so that you can take a photo of the receipt. When you've finished taking a photo, click **OK** to accept the photo.
    2.  Optional: Enter a name for the photo, and enter any notes.

    �or� If you selected **Choose image**, follow these steps:
    1.  Select an image in the list.
    2.  Optional: Enter a name for the image, and enter any notes.

5.  Select **Done**.

## Quick expense entry by using the Expense management mobile workspace
1.  On your mobile device, select the **Expense management** workspace.
2.  Select **Quick expense entry**.
3.  Select the category for the expense. You see a list of expense categories that are loaded into your app for offline use. By default, up to 50 items are loaded, but a developer can change this number. For more information, developers should see [Dynamics�365 for Operations mobile platform](http://ax.help.dynamics.com/en/wiki/mobile-development-handbook/). If your category isn't in the list, select **Search** to do an online search in Dynamics�365 for Operations. Search by expense category, or switch to search by expense type.
4.  Enter the transaction date of the expense.
5.  Optional: Enter the merchant for the expense.
6.  Enter the amount of the expense.
7.  Select the currency of the expense. You see a list of the currency codes that are loaded into your app for offline use. By default, up to 400 currencies are loaded, but a developer can change this number. For more information, developers should see [Dynamics�365 for Operations mobile platform](http://ax.help.dynamics.com/en/wiki/mobile-development-handbook/). If your currency isn't in the list, select **Search** to do an online search in Dynamics�365 for Operations. Search by currency, or switch to search by name.
8.  Select to **Take photo** or **Choose image**.
9.  If you selected **Take photo**, you're taken to the camera on your mobile device, so that you can take a photo of the receipt. When you've finished taking a photo, click **OK** to accept the photo. �or� If you selected **Choose image**, select an image in the list.
10. Select **Done**.



