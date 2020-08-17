---
# required metadata

title: Set up a lease workflow
description: 
author: moaamer
manager: Ann Beebe
ms.date: 08/17/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-08-17
ms.dyn365.ops.version: 10.0.14
---

# Set up a lease workflow

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The lease approval workflow creates an approval workflow when the lease is created. To understand how to use the workflow, refer to the Using the Lease workflow article.

1. Open the **Lease workflow** page (**Asset leasing > Setup > Lease workflow**).
2. Click **New**.
3. From the popup, click the **Lease workflow** link under the **Workflow type**. Opening this link will start the application. Once the application runs, sign into **Active Directory** to be redirected to the workflow application.
4. Drag the **Lease workflow approval** element onto the workflow.
5. Connect one node from the **Start** to the **Lease workflow approval**. Then connect the **Lease workflow approval** to the end. The result should appear like the following.
6. Double-click the **Lease workflow approval**.
7. Select **Properties** and name the workflow under **Basic settings**.
8. You can also set more parameters in this window for the workflow. If Automatic actions are enabled, the system will automatically take a specific action. Notifications can be sent if specified in the Notifications tab. In the Advanced settings tab, a final approver can be selected, a time limit can be set, and specific acts can be designated.
9. Once desired parameters and information is specified, click close to return to the previous window.
10. Now select the Step 1 and click Properties.
11. In Basic Settings, name the step, create a subject line for the approval, and designate instructions for the approval. An example is shown below.
12. Navigate to Assignment and select the assignment type. A specific user can be assigned to the approval by selecting "User."
13. If "User" was selected, navigate to Assignment > User. Then, double click on the user or users on the desired users to approve the lease. Then, select Close to return.
14. Click Save and close to create the workflow. Then, select Ok when prompted in the following two popups. Click close once returned to the Create workflow page.
15. Select the new workflow and click Versions. Then ensure it is made active by clicking the Make active button.
16. Click Close, and the new Active version will appear.
