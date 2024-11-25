---
title: Use lease approval workflows
description: Learn about how to use workflows to approve asset leases, and how to track the status and history of the workflows, including a detailed step-by-step process.
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

# Use lease approval workflows

[!include [banner](../includes/banner.md)]

This article explains how to use workflows to approve asset leases, and how to track the status and history of the workflows. Workflows help bring consistency to the management of lease approvals by providing a standard set of approval steps and assigning specific users who approve each step of the process. An approver can approve a lease, reject it, request a change to it, or assign it to another user for approval. Workflows can also bring more visibility into the approval process by letting you track their status and history. Additionally, you can view a centralized worklist that lists the tasks and approvals that are assigned to specific approvers.

Before you use this procedure, make sure that at least on lease approval workflow has been created. If no workflow exists, create one. For information about how to set up a workflow, see [Set up lease approval workflows](set-up-lease-wrkflw.md).

1. Submit a lease for approval. On the **Book details** page for the lease, select **Workflow**, and then select **Submit**.
2. In the dialog box that appears, you can add a comment. The designated approver will see this comment together with the lease. When you've finished entering the comment, select **Submit**. The lease is submitted to the workflow system, and the approver receives it for approval.
3. To view the leases that they are designated for approval, go to **Modules \> Common \> Work items \> Work items assigned to me**.
4. On the **Work items assigned to me** page, select the **Lease ID** link for the lease that you want to view. The page that appears depends on the lease books and lease details that you have access to.
5. When you've finish viewing the lease, select **Workflow**, and decide what action should be taken. The options include **Approve**, **Rejected**, **Request change**, **Delegate**, and **Canceled**. You can also select **View history** to view the approval history for the selected lease.
6. After you've selected an action, enter a comment to describe the action. When you've finished entering the comment, select the **Approved** action in the list.
7. To view the approval actions, go back to the **Lease details** page from the **Lease summary** page, and then select **Workflow \> View history**.

    You can view the workflow activities on the **Workflow history** page. This page shows the workflow steps that have been taken on the specific lease. You can also use the **Work items** field to view the status of the assigned work items.

8. To stop a workflow, on the **Workflow history** page, select **Recall**. In the dialog box that appears, enter a comment, and then select **OK**.
9. To inactivate a workflow, or to activate a workflow that was previously created, go to **Asset leasing \> Setup \> Lease workflow**. Then, on the **Lease workflow** page, select **Workflow \> Versions**. To make a current workflow inactive, select the active lease in the lease version dialog box, and then select **Make inactive**. To make an existing workflow active, select the workflow, and then select **Make active**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
