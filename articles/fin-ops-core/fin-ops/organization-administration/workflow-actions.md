---
title: Actions in workflow approval processes
description: Learn about the actions that each participant in a workflow approval process can take, including an overview on actions that an originator can perform.
author: ChrisGarty
ms.author: cgarty
ms.topic: article
ms.date: 03/10/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 65fb711c-6474-42d1-81ed-ca657c29bf1f
---

# Actions in workflow approval processes

[!include [banner](../includes/banner.md)]

This article explains the actions that each participant in a workflow approval process can take.

A workflow can involve several groups of people: the originator, task assignees, decision makers, and approvers. For example, in the following expense report workflow, Sam is the originator, the members of the queue are task assignees, John is a decision maker, and Frank, Sue, and Ann are approvers.

:::image type="content" source="./media/workflow_withmanualdecision.gif" alt-text="Screenshot of the Workflow with Manual Decision diagram.":::

The following sections explain the workflow actions that each group can perform.

## Actions that an originator can perform

The originator starts a workflow instance by submitting a document for processing. For example, Sam must select the **Submit** button on the **Expense report** page to submit the expense report.

## Actions that a task assignee can perform

You can assign a task to multiple people or to a work item queue that several people monitor. However, only one person can complete a task. For example, Sam submits an expense report and routes the receipts to the organization's Expense Reports department for review.

The members of the Adventure Works Expense Reports department monitor the queue. Julie, a member of that department, accepts the task of reviewing Sam's expense report and receipts. Julie can now perform one of the following actions: complete, reject, delegate, request change, reassign, or release.

> [!NOTE]
> The available actions vary, depending on how the software developer designed the task.

### Complete

When a user completes a task, the system assigns the document submitted for processing to the next user in the workflow, if there's a next user. If no additional processing is required, the workflow process ends.

For example, Julie, a member of the Adventure Works Expense Reports department, accepts the task of reviewing Sam's expense report and receipts. After Julie completes the review, the system assigns the document to John.

### Reject

When a user rejects a document, the workflow process ends.

For example, Julie, a member of the Adventure Works Expense Reports department, accepts the task of reviewing Sam's expense report and receipts. If Julie rejects the expense report, the workflow process ends.

Sam can then resubmit the expense report. Sam can make changes first, or resubmit the original version. If Sam resubmits the expense report, the workflow process starts at the manual review task.

### Delegate

When a user delegates a task, the system assigns the task to another user.

For example, Julie, a member of the Adventure Works Expense Reports department, accepts the task of reviewing Sam's expense report and receipts. Julie delegates this task to Tim, who is Julie's assistant.

Tim acts on behalf of Julie. Therefore, when Tim completes the review, the system assigns the expense report to John, just as if Julie had completed the task.

### Request change

When a user requests a change to a document that was submitted, the system sends the document back to the originator.

For example, Julie, a member of the Adventure Works Expense Reports department, accepts the task of reviewing Sam's expense report and receipts. Julie notices some errors on the expense report and requests changes. The system sends the expense report back to Sam.

Sam can resubmit the expense report. Sam can make the requested changes first, or resubmit the original version. If Sam resubmits the expense report, a member of the work item queue must review the expense report and the receipts again.

### Reassign

Members of a work item queue can reassign documents in that queue to another queue.

For example, Julie is a member of the Adventure Works Expense Reports department and monitors the queue. To help balance the workload, Julie can reassign the expense report and the included receipts to another queue.

### Release

Occasionally, a member of a work item queue accepts a task but then decides they can't complete it. In this case, the person who accepted the task can release the document back to the work item queue.

For example, Julie is a member of the Adventure Works Expense Reports department and accepts the task of reviewing Sam's expense report and receipts. If Julie can't complete the task, she can release the document. The expense report returns to the queue so that other members of the Adventure Works Expense Reports department can complete the task.

## Actions that a decision maker can perform

Typically, you assign a document to a decision maker because there's a question that the decision maker must answer. The answer to the question is typically **Yes** or **No**, or **True** or **False**. If the decision maker doesn't select one of those choices, they can delegate the decision.

### \[Choice 1\] or \[Choice 2\]

A decision maker must answer a question that's related to the document. The answer to the question is typically **Yes** or **No**, or **True** or **False**. The answer that the decision maker selects determines the workflow branch that's used to process the document.

For example, you assign Sam's expense report to John. John must decide whether the information in the document requires a call to Sam's manager. If John decides that a call is required, the expense report is assigned to Aretha, who must then call Sam's manager. If John decides that a call isn't required, the expense report is assigned to Frank for approval.

### Delegate

When a decision maker delegates a decision, they assign the document to another user who must make the decision.

For example, you assign Sam's expense report to John. John delegates the decision to Maria, who is John's assistant.

Maria acts on behalf of John. If Maria decides that a call to Sam's manager is required, she assigns the expense report to Aretha, who must then call Sam's manager. If Maria decides that a call isn't required, she assigns the expense report to Frank for approval.

## Actions that an approver can perform

When you assign a document to an approver, the approver can perform one of the following actions: approve, reject, delegate, or request change.

### Approve

When an approver approves a document, the document is assigned to the next user in the workflow, if there's a next user. If no additional processing is required, the workflow process ends.

For example, Sam submits an expense report for USD 6,000, and you assign this document to Frank. When Frank approves the document, it's assigned to Sue for approval. When Sue approves the expense report, the workflow process ends.

### Reject

When an approver rejects a document, the workflow process ends.

For example, Sam submits an expense report for USD 12,000, and you assign this document to Sue. If Sue rejects the expense report, the workflow process ends.

Sam can resubmit the expense report. Sam can make changes first, or resubmit the original version of the expense report. If Sam resubmits the expense report, the workflow process starts at the approval process.

### Delegate

When an approver delegates a document, the document is assigned to another user for approval.

For example, Sam submits an expense report for USD 12,000, and you assign this document to Frank. Frank delegates the expense report to Ann.

Ann then acts on behalf of Frank. Therefore, when Ann approves the document, it's assigned to Sue for approval, just as if Frank had approved it. After Sue approves the document, it's sent to Ann for approval.

### Request change

When an approver requests a change to a document, the system sends the document back to the originator.

For example, Sam submits an expense report for USD 12,000, and the system assigns the document to Sue. If Sue requests a change, the system sends the expense report back to Sam.

Sam can resubmit the expense report. Sam can make the requested changes first, or resubmit the original version of the expense report. If Sam resubmits the expense report, the system sends it to Frank for approval, because Frank is the first approver in the approval process.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
