---
# required metadata

title: Set up a lease workflow
description: The topic describes the process for setting up an approval workflow that will run when a new lease is created.
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

The topic describes the process for setting up an approval workflow that will run when a new lease is created. For information about how to use the workflow, see [Use the lease approval workflow](use-create-lease-wrkflw.md). 

1. Open the **Lease workflow** page (**Asset leasing > Setup > Lease workflow**).
2. Click **New**.
3. From the popup, click the **Lease workflow** link under the **Workflow type**. Opening this link will start the application. Once the application runs, sign into **Active Directory** to be redirected to the workflow application.
4. Drag the **Lease workflow approval** element onto the workflow.
5. Connect one node from the **Start** to the **Lease workflow approval**. Then connect the **Lease workflow approval** to the end. The result should appear like the following.
6. Double-click the **Lease workflow approval**.
7. Select **Properties** and name the workflow under **Basic settings**.
   You can also set more parameters on this page for the workflow. If you've enabled **Automatic actions**, the system will automatically take a specific action. Notifications can be sent if specified in the **Notifications** tab. In the **Advanced settings** tab, you can specify a final approver, set a time limit, and designate specific actions to be completed.
8. When you've finished setting workflow parameters, click **Close**.
9. Select **Step 1**, and then click **Properties**.
10. In the **Basic Settings** field, name the step, create a subject line for the approval, and designate instructions for the approval. An example is shown below.
11. Open the **Assignment** page and select the **Assignment type**. You can assign a specific to the approval by selecting **User**.
12. If you selected **User** (**Assignment > User**), select the users who approve leases, then, click **Close**.
13. Click **Save** and close to create the workflow. Then, click **OK** when prompted. Click **Close** from the **Create workflow** page.
14. Select the new workflow and click **Versions**. Then ensure it is made active by clicking **Make active** button.
15. Click **Close**, and the new **Active version** will appear.
