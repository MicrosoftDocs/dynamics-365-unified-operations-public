---
# required metadata

title: Use the Create Lease Workflow
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

# Use the Create Lease Workflow

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The workflow represents a business process that defines how the lease moves though the system by allowing the user to set designated approvers. By using the workflow feature, users will have a more consistent leasing operation since the leases will be processed and approved in an efficient manner, have process visibility because the user can track the status and history of the workflow, and have a centralized worklist where users can view the tasks and approvals that are assigned to them.

1.	Create a lease approval workflow, which is outlined in the setup lease workflow section. An approver can approve a lease, reject a lease, request a change in the lease, or assign the lease to another user for approval.
2.	Submit a lease for approval by navigating to the desired lease's Book Details page and then clicking Workflow.
3.	From the drop-down, select the Submit button.
4.	Once the user hits Submit, it will bring up a window where the user can add a comment, which will appear along with the lease to the designated approver. After the desired comment is entered, select Submit. Upon submission, the approver will receive the lease to approve.
5.	To view the leases that they are designated to approve, navigate to Modules > Common > Work items > Work items assigned to me.
6.	To review the lease, select the Lease ID hyperlink. From there, the user will be taken to a page with accessibility to all lease books and lease details.
7.	Once the lease has been reviewed, select Workflow and decide what action to take: Approve, Rejected, Request change, Delegate, Canceled, and View history.
8.	Once the action has been selected, the user can submit a comment to accompany the action. After the comment is complete, click the bottom action, which is Approved in the example below.
9.	The approval actions can be viewed by navigating back to the Lease details page from the Lease summary. Workflow > View history
10.	From the Workflow history page, the user can see the workflow activities, which outlines what steps have been taken in the workflow on the specific lease. The user can also see the status of the work items assigned by viewing the Work items drop-down.
11.	To stop a workflow, go to the Workflow history page and select Recall. Upon selection, a pop-up will appear. Insert a comment in the dialog box and click Ok.
12.	To make a workflow inactive or to activate a previously created workflow, navigate to Asset leasing > Setup > Lease workflow.
13.	Navigate to Workflow > Versions
14.	To make a current workflow inactive, select the active lease from the lease version's pop-up and click Make inactive.
15.	To make an existing workflow active, select the desired workflow and click Make active.
