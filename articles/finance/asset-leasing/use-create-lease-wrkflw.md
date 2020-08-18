---
# required metadata

title: Use lease approval workflows
description: This topic lists the steps for using workflows for approving asset leases, as well as for tracking the status and history of the workflow.
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

# Use lease approval workflows

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists the steps for using workflows for approving asset leases, as well as for tracking the status and history of the workflow. Workflows help bring consistency to the management of lease approvals by providing a standard set of approval steps, and by designating specific users to approve each step of the process. Workflows can also bring greater visibility into the approval process by letting you track the status and history of the workflow, as well as viewing a centralized worklist where users can view the tasks and approvals that are assigned to them. An approver can approve a lease, reject a lease, request a change in the lease, or assign the lease to another user for approval.

1. Before using this proceddure, you should have created at least on lease approval workflow. If you haven't create one yet, see [Set up a lease workflow](set-up-lease-wrkflw.md) for information on setting up a workflow. 
2. Submit a lease for approval by opening the **Book details** page for the lease to approve, and then clicking **Workflow**.
3. From the drop-down, select the **Submit** button.
4. When you click **Submit**, it will bring up a window where the user can add a comment, which will appear along with the lease to the designated approver. After entering a comment, select **Submit**. When you submit the lease to workflow, the approver will receive the lease to approve.
5. To view the leases that they are designated to approve, open the **Work items assigned to me** page (**Modules > Common > Work items > Work items assigned to me**).
6. To review the lease, select the **Lease ID** link. The page that's displayed will depend on which lease books and lease details you have access to.
7. When you viewed the lease, select **Workflow** and decide what action to take. The options include **Approve**, **Rejected**, **Request change**, **Delegate**, and **Canceled**. You can also select **View history** to see the approval history for the selected lease.
8. When you've selected an action, enter a comment to describe the selected action. When you've finished enterin the comment, click the **Approved** action from the list.
9. The approval actions can be viewed by navigating back to You can see the approval actions on the **Lease details** page from the **Lease summary**, (**Workflow > View history**).
10. From the **Workflow history** page, the user can see the workflow activities, which outlines what steps have been taken in the workflow on the specific lease. You can also see the status of the work items assigned by viewing the **Work items** drop-down list.
11. To stop a workflow, go to the Workflow history page and select Recall. Upon selection, a pop-up will appear. Insert a comment in the dialog box and click Ok.
12. To make a workflow inactive or to activate a previously created workflow, open the **Lease workflow** page (**Asset leasing > Setup > Lease workflow**).
13. Open the **Versions** page (**Navigate to Workflow > Versions**).
14. To make a current workflow inactive, select the active lease from the lease version's pop-up and click **Make inactive**.
15. To make an existing workflow active, select the desired workflow and click **Make active**.
