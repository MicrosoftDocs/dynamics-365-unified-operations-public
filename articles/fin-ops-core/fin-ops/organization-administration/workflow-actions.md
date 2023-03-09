---
# required metadata

title: Actions in workflow approval processes
description: This article explains the actions that each participant in a workflow approval process can take.
author: ChrisGarty
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 56411
ms.assetid: 65fb711c-6474-42d1-81ed-ca657c29bf1f
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Actions in workflow approval processes

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-1.md)]

This article explains the actions that each participant in a workflow approval process can take.

A workflow can involve several groups of people: the originator, task assignees, decision makers, and approvers. For example, in the following expense report workflow, Sam is the originator, the members of the queue are task assignees, John is a decision maker, and Frank, Sue, and Ann are approvers.

[![Workflow\_WithManualDecision.](./media/workflow_withmanualdecision.gif)](./media/workflow_withmanualdecision.gif)

The following sections explain the workflow actions that each group can perform.

## Actions that an originator can perform

The originator starts a workflow instance by submitting a document for processing. For example, Sam must click the **Submit** button on the **Expense report** page to submit the expense report.

## Actions that a task assignee can perform

A task can be assigned to multiple people or to a work item queue that is monitored by several people. However, only one person can complete a task. For example, Sam has submitted an expense report and has routed the receipts to the organization's Expense Reports department for review.

The members of the Adventure Works Expense Reports department monitor the queue. Julie, a member of that department, has accepted the task of reviewing Sam's expense report and receipts. Julie can now perform one of the following actions: complete, reject, delegate, request change, reassign, or release.

> [!NOTE]
> The actions that are available vary, depending on how the software developer designed the task.

### Complete

When a user completes a task, the document that was submitted for processing is assigned to the next user in the workflow, if there is a next user. If no additional processing is required, the workflow process ends.

For example, Julie, a member of the Adventure Works Expense Reports department, has accepted the task of reviewing Sam's expense report and receipts. After Julie completes the review, the document is assigned to John.

### Reject

When a user rejects a document, the workflow process ends.

For example, Julie, a member of the Adventure Works Expense Reports department, has accepted the task of reviewing Sam's expense report and receipts. If Julie rejects the expense report, the workflow process ends.

Sam can then resubmit the expense report. Sam can make changes first, or resubmit the original version. If Sam resubmits the expense report, the workflow process starts at the manual review task.

### Delegate

When a user delegates a task, the task is assigned to another user.

For example, Julie, a member of the Adventure Works Expense Reports department, has accepted the task of reviewing Sam's expense report and receipts. Julie delegates this task to Tim, who is Julie's assistant.

Tim then acts on behalf of Julie. Therefore, when Tim completes the review, the expense report is assigned to John, just as if Julie had completed the task.

### Request change

When a user requests a change to a document that was submitted, the document is sent back to the originator.

For example, Julie, a member of the Adventure Works Expense Reports department, has accepted the task of reviewing Sam's expense report and receipts. Julie notices some errors on the expense report and requests changes. The expense report is sent back to Sam.

Sam can resubmit the expense report. Sam can make the requested changes first, or resubmit the original version. If Sam resubmits the expense report, a member of the work item queue must review the expense report and the receipts again.

### Reassign

The members of a work item queue can reassign documents that are in that queue to another queue.

For example, Julie, a member of the Adventure Works Expense Reports department, is monitoring the queue. To help balance the workload, Julie can reassign the expense report, and the receipts that are included with it, to another queue.

### Release

Occasionally, a member of a work item queue might accept a task, but then decide that they can't complete the task. In this case, the person who accepted the task can release the document back to the work item queue.

For example, Julie, a member of the Adventure Works Expense Reports department, has accepted the task of reviewing Sam's expense report and receipts. If Julie can't complete the task, then Julie can release the document. The expense report is returned to the queue, so that other members of the Adventure Works Expense Reports department can complete the task.

## Actions that a decision maker can perform

Typically, a document is assigned to a decision maker, because there is a question that the decision maker must answer. The answer to the question is typically **Yes** or **No**, or **True** or **False**. If the decision maker doesn't select one of those choices, they can delegate the decision.

### \[Choice 1\] or \[Choice 2\]

A decision maker must answer a question that is related to the document. The answer to the question is typically **Yes** or **No**, or **True** or **False**. The answer that the decision maker selects determines the workflow branch that is used to process the document.

For example, Sam's expense report is assigned to John. John must decide whether the information in the document requires a call to Sam's manager. If John decides that a call is required, the expense report is assigned to Aretha, who must then call Sam's manager. If John decides that a call isn't required, the expense report is assigned to Frank for approval.

### Delegate

When a decision maker delegates a decision, the document is assigned to another user who must make the decision.

For example, Sam's expense report is assigned to John. John delegates the decision to Maria, who is John's assistant.

Maria then acts on behalf of John. If Maria decides that a call to Sam's manager is required, the expense report is assigned to Aretha, who must then call Sam's manager. If Maria decides that a call isn't required, the expense report is assigned to Frank for approval.

## Actions that an approver can perform

When a document is assigned to an approver, the approver can perform one of the following actions: approve, reject, delegate, or request change.

### Approve

When an approver approves a document, the document is assigned to the next user in the workflow, if there is a next user. If no additional processing is required, the workflow process ends.

For example, Sam has submitted an expense report for USD 6,000, and this document is assigned to Frank. When Frank approves the document, it's assigned to Sue for approval. When Sue approves the expense report, the workflow process ends.

### Reject

When an approver rejects a document, the workflow process ends.

For example, Sam has submitted an expense report for USD 12,000, and this document is assigned to Sue. If Sue rejects the expense report, the workflow process ends.

Sam can resubmit the expense report. Sam can make changes first, or resubmit the original version of the expense report. If Sam resubmits the expense report, the workflow process starts at the approval process.

### Delegate

When an approver delegates a document, the document is assigned to another user for approval.

For example, Sam has submitted an expense report for USD 12,000, and this document is assigned to Frank. Frank delegates the expense report to Ann.

Ann then acts on behalf of Frank. Therefore, when Ann approves the document, it's assigned to Sue for approval, just as if Frank had approved it. After Sue approves the document, it's sent to Ann for approval.

### Request change

When an approver requests a change to a document, the document is sent back to the originator.

For example, Sam has submitted an expense report for USD 12,000, and this document is assigned to Sue. If Sue requests a change, the expense report is sent back to Sam.

Sam can resubmit the expense report. Sam make the requested changes first, or resubmit the original version of the expense report. If Sam resubmits the expense report, it's sent to Frank for approval, because Frank is the first approver in the approval process.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
