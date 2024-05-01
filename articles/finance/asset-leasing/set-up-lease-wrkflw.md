---
title: Set up lease approval workflows
description: Learn about how to set up an approval workflow that will run when a new lease is created with a detailed step-by-step process.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/12/2021
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: WorkflowTableListPageRnr
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Set up lease approval workflows

[!include [banner](../includes/banner.md)]

The article explains how to set up an approval workflow that will run when a new lease is created. For information about how to use the workflow, see [Use lease approval workflows](use-create-lease-wrkflw.md). 

1. Go to **Asset leasing \> Setup \> Lease workflow**.
2. On the **Lease workflow** page, select **New**.
3. In the dialog box that appears, under **Workflow type**, select the **Lease workflow** link.

    The application is opened. After it runs, sign in to Microsoft Entra ID to be redirected to the workflow application.

4. Drag the **Lease workflow approval** element onto the workflow.
5. Connect one node from **Start** to **Lease workflow approval**. Then connect **Lease workflow approval** to **End**.
6. Double-click **Lease workflow approval**.
7. Select **Properties**, and then, under **Basic settings**, enter a name for the workflow.

    On this page, you can also set more parameters for the workflow. If you've turned on **Automatic actions**, the system will automatically take a specific action. Notifications can be sent if they are specified on the **Notifications** tab. On the **Advanced settings** tab, you can specify a final approver, set a time limit, and designate specific actions that must be completed.

8. When you've finished setting the workflow parameters, select **Close**.
9. Select **Step 1**, and then select **Properties**.
10. Under **Basic settings**, enter a name for the step, create a subject line for the approval, and specify instructions for the approval.
11. On the **Assignment** page, select the assignment type.
12. To assign specific users to the approval, select **User**, select the users who approve leases, and then select **Close**.
13. Select **Save and close** to create the workflow. Then, when you're prompted, select **OK**.
14. On the **Create workflow** page, select **Close**.
14. Select the new workflow, and then select **Versions**. Then select **Make active** to ensure that the workflow is active.
15. Select **Close**. The new active version appears.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]