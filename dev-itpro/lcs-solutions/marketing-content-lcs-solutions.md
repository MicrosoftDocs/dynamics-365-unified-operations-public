---
# required metadata

title: Stage and publish an LCS solution
description: This topic explains how to upload the marketing content for your LCS solution package to the Azure Publishing Portal, and how to stage and publish your solution.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
# ms.search.scope: 
# ms.tgt_pltfrm: 
ms.custom: 196873
ms.assetid: 80b0cc44-ffbe-400e-b902-60518a930b0d
ms.search.region: Global
# ms.search.industry: 
ms.author: omarc
# ms.search.validFrom: 
# ms.dyn365.ops.version: 

---

# Stage and publish an LCS solution

[!include[banner](../includes/banner.md)]


This topic explains how to upload the marketing content for your LCS solution package to the Azure Publishing Portal, and how to stage and publish your solution.

Before you can publish the marketing content for your LCS solution package to the Microsoft Azure Publishing Portal, you must set up a Developer Center account with Microsoft. After you've set up an account, you can upload your marketing content and then manage the content through the lifecycle of application. For information about how to set up a Developer Center account, see [Create a Microsoft Developer account](https://azure.microsoft.com/en-us/documentation/articles/marketplace-publishing-accounts-creation-registration/).

## Upload marketing materials, set up legal information, and identify the support team
You can upload a marketing summary, a description of your solution, and other marketing materials.

1.  In the [Azure Publishing Portal](https://publish.windowsazure.com/workspace/), open your solution, and then, in the left pane, click **Marketing**.
2.  In the **Url** section, in the **Identifier** field, enter a short, URL-friendly identifier to use in the URLs that link to the specific marketing pages for your offer.
3.  In the **Languages** section, select **English**, and then, in the **Description** section, enter the title, summary, long summary, and description of your solution.
4.  In the **Logos** section, click the **Upload Image** link for the graphic size that corresponds to the graphic size that you want to upload. **Note:** All graphics must follow the sizes that are given for each image, and they must be in a PNG format.
5.  Click the plus sign (**+**) to add one or more links to additional resources.
6.  Optional: In the left pane, click **Sample Images** to upload any additional images that describe or promote your solution. **Note:** All graphics must follow the sizes that are given for each image, and they must be in a PNG format.
7.  In the left navigation pane, click **Plans**, and then, in the **Plans** section, enter the title, summary, and description of what customers will receive when they purchase your solution. **Important:** Currently, this information doesn't apply to Microsoft Dynamics 365 for Operations. However, it will be used in the future and must be included before your solution can be published. You can update this information at any time.
8.  In the left navigation pane, click **Legal**, and then, in the **Legal** section, enter the URLs of the privacy policy and the terms of use for your solution. Customers will be able to view these policies when they purchase your solution.
9.  In the left navigation pane, click **Support**, and then enter the engineering contact and customer support information for your organization. This information will be used as a single point of contact if Microsoft has a question about your solution. The information will also be used for customer support.
10. In the left navigation pane, click **Categories**, and then select the **Business Application** check box.

## Stage and publish your solution
After you've completed the previous procedure, you can stage and publish your solution.

1.  In the left navigation pane, click **Staging**.
2.  In the **Staging** group, click **Push to staging**. If any corrections are required, you receive an error message.
3.  For each error in the message, click the link to fix the issue.
4.  After you've fixed all the errors, you will be prompted to enter your Azure subscription ID. You can find this ID in LCS, at **Project Settings** &gt; **Azure Connectors**. Enter your Azure subscription ID, and then click the check mark. You are returned to the **Staging** page, where you can track the staging process of your application.
5.  When staging is completed, in the **Production** group, click **Request Approval to Push to Production**. Microsoft will begin to validate your solution and marketing materials. If any questions or concerns arise during the review, Microsoft will contact the engineering contacts that your company provided. After approval, your solution will be available in the Azure marketplace.


See also
--------

[LCS Solutions for AppSource home page](lcs-solutions-app-source.md)


