---
title: Set up lease approval workflows
description: Learn about how to set up an approval workflow that will run when a new lease is created with a detailed step-by-step process.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 06/23/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: WorkflowTableListPageRnr
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Set up lease approval workflows

[!include [banner](../includes/banner.md)]

This article explains how to set up an approval workflow that runs when you create a new lease. For information about how to use the workflow, see [Use lease approval workflows](use-create-lease-wrkflw.md).

1. Go to **Asset leasing \> Setup \> Lease workflow**.
2. On the **Lease workflow** page, select **New**.
1. In the dialog box, under **Workflow type**, select the **Lease workflow** link.

    The application opens. After it runs, sign in to Microsoft Entra ID to be redirected to the workflow application.

1. Drag the **Lease workflow approval** element onto the workflow.
1. Connect one node from **Start** to **Lease workflow approval**. Then connect **Lease workflow approval** to **End**.
1. Double-click **Lease workflow approval**.
1. Select **Properties**, and then, under **Basic settings**, enter a name for the workflow.

    On this page, you can also set more parameters for the workflow. If you turn on **Automatic actions**, the system automatically takes a specific action. You can send notifications if you specify them on the **Notifications** tab. On the **Advanced settings** tab, you can specify a final approver, set a time limit, and designate specific actions that must be completed.

1. When you finish setting the workflow parameters, select **Close**.
1. Select **Step 1**, and then select **Properties**.
1. Under **Basic settings**, enter a name for the step, create a subject line for the approval, and specify instructions for the approval.
1. On the **Assignment** page, select the assignment type.
1. To assign specific users to the approval, select **User**, select the users who approve leases, and then select **Close**.
1. Select **Save and close** to create the workflow. Then, when you're prompted, select **OK**.
1. On the **Create workflow** page, select **Close**.
1. Select the new workflow, and then select **Versions**. Then select **Make active** to ensure that the workflow is active.
1. Select **Close**. The new active version appears.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
