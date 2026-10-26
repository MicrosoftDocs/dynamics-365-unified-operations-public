---
title: CAPA case approval workflows (preview)
description: Learn how to set up and use a workflow that routes corrective and preventive action (CAPA) cases for review and approval before they're closed.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSCAPACaseDetail
ms.topic: how-to
ms.date: 10/23/2026
ms.custom:
  - bap-template
ai-usage: ai-assisted
---

# CAPA case approval workflows (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

In regulated industries, the person who investigates a quality issue usually isn't allowed to decide on their own that the corrective action is complete. An independent reviewer must confirm the findings first. CAPA case approval workflows add that review step to Microsoft Dynamics 365 Supply Chain Management. When the *CAPA case approval workflow* feature is turned on, users submit a corrective and preventive action (CAPA) case for approval instead of closing it. Reviewers then approve the case, reject it, or request changes. After the whole workflow finishes, the system closes the case automatically. Every review action and comment is stored in the workflow history. You design the workflow by using the standard workflow editor in finance and operations apps.

[!INCLUDE [preview-note-d365](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

Before you can use CAPA case approval workflows, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.50 or later.
- The feature named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.47, this feature is turned on by default. As of version 10.0.49, it's mandatory and can't be turned off.
- The feature named *CAPA case approval workflow* must be turned on in Feature management. This feature is turned off by default, and you can turn it off again later.
- An active CAPA case approval workflow configuration must exist. Otherwise, users can't submit cases.
- Electronic signatures must not be required for CAPA case status changes. The two capabilities can't be combined. If a signature is required, you can't submit the case for approval, and you must continue to close cases through signed status changes.
- Users who submit or act on CAPA cases need the **Maintain cases for CAPA** duty. This duty is assigned to the **CAPA updater** and **CAPA administrator** roles by default.

While the *CAPA case approval workflow* feature is turned off, CAPA cases continue to use the generic case management workflow, as controlled by the **Use case management workflow** parameter. When the feature is turned on, the parameter is hidden, but its saved value is kept. Learn more in [CAPA management administration](capa-admin.md).

## How the approval workflow works

When you turn on the *CAPA case approval workflow* feature, new CAPA case submissions use the CAPA case approval workflow instead of the generic case workflow. The feature doesn't migrate existing workflow configurations and case data. A case that's already running in a generic workflow keeps its template. The feature doesn't provide a default approval chain. You must create a workflow configuration and assign its participants.

The workflow template supports two elements:

| Element | Purpose | Available outcomes |
|---|---|---|
| **Approve CAPA case** (approval) | Approve, reject, or request changes to the CAPA case resolution. | *Approve*, *Reject*, *Request change*. You can also delegate and resubmit. |
| **Review CAPA case** (task) | Complete the CAPA case review. | *Complete*. You can also delegate. |

Each case has an **Approval status** field that shows where it is in the process. Only workflow events change this field. Users can't edit it directly.

| Approval status | Description |
|---|---|
| *Draft* | The case isn't submitted yet. You can edit the case as your CAPA permissions allow. |
| *Submitted* | The case was submitted and is waiting to be routed. The case is locked. |
| *In review* | A reviewer has a pending work item for the case. The case is locked. |
| *Change requested* | A reviewer used **Request change**. The case is unlocked so that you can correct it and resubmit. |
| *Rejected* | A reviewer used **Reject** to return the case. The case is unlocked so that you can correct it and resubmit. |
| *Approved* | The workflow completed, and the system closed the case. |

The **Approval status** field appears as a column in the CAPA case grids, and on the CAPA case details page when the case is controlled by a CAPA approval workflow. If you turn the feature on or off while the CAPA case page is open, close and reopen the page to update the column visibility.

## Set up the CAPA case approval workflow

To set up CAPA case approval workflows, turn on the *CAPA case approval workflow* feature, create and activate a workflow configuration, review the CAPA parameters that affect the workflow, and assign security.

### Turn on the feature

To make CAPA cases use the approval workflow, follow these steps:

1. Go to **Feature management**.
1. Make sure that *Advanced quality management* is turned on.
1. Select *CAPA case approval workflow*, and then select **Enable now**.

### Create and activate the workflow

Create the CAPA case approval workflow using the workflow editor, just like other workflows for Supply Chain Management. Learn more about the workflow editor in [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md), [Create workflows overview](../../fin-ops-core/fin-ops/organization-administration/create-workflow.md), and [Workflow elements](../../fin-ops-core/fin-ops/organization-administration/workflow-elements.md).

To create and activate a CAPA case approval workflow, follow these steps:

1. Go to **Inventory management** > **Setup** > **Inventory management workflows**.
1. On the Action Pane, select **New**.
1. In the **Create workflow** dialog box, select the *CAPA case approval workflow* template (in the *CAPA case workflows* category), and then select **Create workflow**.
1. In the workflow editor, add the *Approve CAPA case* approval and, optionally, the *Review CAPA case* task, and connect them as your process requires. Learn more in [Configure approval processes in a workflow](../../fin-ops-core/fin-ops/organization-administration/configure-approval-process-workflow.md) and [Configure approval steps in a workflow](../../fin-ops-core/fin-ops/organization-administration/configure-approval-step-workflow.md).
1. Assign the participants for each element, and set any conditions or deadlines that you need.
1. Save the workflow, and then select **Activate**.

You must have an active CAPA case approval workflow configuration before users can submit cases. If none exists, submission fails.

You can create and activate the configuration while the *CAPA case approval workflow* feature is turned off, but the system doesn't route cases to it until the feature is turned on. Workflow conditions and assignments can use fields from the CAPA case, its associations, and its case category.

### Review CAPA settings that affect the workflow

Review the following settings on the **Quality management** tab of the **Inventory and warehouse management parameters** page. Learn more in [CAPA management administration](capa-admin.md).

- **Require root cause** – If you set this option to *Yes*, a case must have a root cause when users submit it for approval.
- **Electronic signature** – You can't use CAPA case approval workflows while an electronic signature is required for CAPA case status changes (the *Close/Cancel CAPA case* requirement). Turn off that requirement if you want to use the workflow.

### Assign security

The following privileges control access to the workflow. Both privileges are included in the *Maintain cases for CAPA* duty.

| Privilege | Grants access to |
|---|---|
| *CAPA case approval workflow* | Submitting a case and the related actions. |
| *Approve CAPA case* | Approving, completing, rejecting, requesting changes to, and delegating work items. |

Both privileges are included in the following standard roles:

- *CAPA updater*.
- *CAPA administrator*, through the *CAPA updater* subrole.

The *CAPA viewer*, *Quality control clerk*, and *Quality control manager* roles don't include these privileges. Add the *Maintain cases for CAPA* duty to any custom role that must submit or act on CAPA workflow work items.

The workflow configuration determines who receives a work item, and security determines whether that person can act on it. Assign participants who have the required duty. Otherwise, the workflow can't create the work item because the participant has insufficient permissions.

By default, a user can approve a case that they submitted if they're assigned to the approval. To prevent this behavior, turn on **Disallow approval by submitter** at **System administration** > **Setup** > **Workflow** > **Workflow parameters**.

## Submit and approve a CAPA case

After the workflow is active, the people who work on CAPA cases submit them for approval, and reviewers act on the work items that they receive. This section describes each step of that cycle, including how to rework a returned case and how to recall or reopen one.

### Submit a case

You can submit a case when all the following conditions are met:

- It's a CAPA case with a status of *Opened* or *In process*.
- Its approval status is *Draft*, *Rejected*, or *Change requested*.
- It isn't already linked to a running workflow.
- Electronic signatures aren't required for CAPA case status changes.
- If **Require root cause** is set to *Yes*, a root cause is recorded.
- An active CAPA case approval workflow configuration exists.

To submit a case, open the CAPA case details page. On the Action Pane, select **Workflow** > **Submit**, enter a comment if needed, and then select **Submit**.

After you submit a case, the **Approval status** field changes and the case is locked. While the approval status is *Submitted* or *In review*, you can't edit or delete the case, change its status, change its associations, delete case log entries, change knowledge article links, or add activities such as actions, tasks, appointments, and events.

You can still add case log entries, edit existing case log entries, manage email recipients, send email, and view association details, the transaction log, and questionnaire answers. The lock remains in effect if someone turns off the feature while the case is in the workflow.

### Review a case

Approvers and reviewers receive a work item each time their action is required. To respond, open the CAPA case. Then, on the Action Pane, select **Workflow**, and select one of the following actions:

- **Approve** – Moves the workflow forward. When the whole workflow completes, the system closes the case and sets the approval status to *Approved*.
- **Reject** – Returns the case to its owner. The approval status is *Rejected*.
- **Request change** – Returns the case to its owner. The approval status is *Change requested*.
- **Delegate** – Reassigns the work item to another user. Learn more in [Delegate work items in a workflow](../../fin-ops-core/fin-ops/organization-administration/tasks/delegate-work-items-workflow.md).
- **Complete** (review task) – Completes the review task. Completing a task doesn't close the case. The case closes only after the entire workflow completes.

Automatic approval is also supported.

If a validation error occurs when the workflow tries to complete, the workflow enters a faulted state. For example, this error can occur if **Require root cause** is turned on after the case is submitted and the case doesn't have a root cause. Correct the issue, and then use the standard workflow **Resume** action to retry the same workflow instance. Alternatively, recall the case.

### Rework and resubmit a case

After a reviewer rejects a case or requests changes, anyone who has CAPA edit access can edit it. Only the user who holds the returned work item, or a delegate, can resubmit it. Resubmitting continues the same workflow instance and keeps the workflow history.

### Recall a submitted case

To withdraw a submitted case, on the Action Pane, select **Workflow** > **Recall**. The system cancels the case through standard case cancellation, and the approval status returns to *Draft*.

### Turning off the feature while cases are in progress

If you turn off the *CAPA case approval workflow* feature, cases that were never controlled by a CAPA approval workflow return to the generic case workflow behavior. Cases that are already controlled by a CAPA approval workflow keep their workflow template and remain locked where applicable.

Approvers can continue to approve, reject, request changes, delegate, or complete work items, and users can recall a controlled case. However, users can't submit a new case or resubmit a case whose approval status is *Change requested* or *Rejected* until the feature is turned on again. To stop processing such a returned case while the feature is off, recall it. Recall cancels the case.

### Close a case

While a CAPA approval workflow applies to a case, you can't close it manually. The system closes it automatically after final approval. If you try to close it manually, you receive an error that tells you to submit the case for workflow approval first.

### Reopen an approved case

If you move an approved case back to *Opened* or *In process*, the system clears the approval. You must resubmit the case. The case log and workflow history are kept.

> [!NOTE]
> You can't reopen an approved case to *Opened* if the case has a service level agreement (SLA). Reopen the case to *In process* instead.

## Review the approval history

As with other types of workflows, you can use the **Workflow history** page to review who acted on a CAPA case, when they acted, and which comments they entered.

To review the workflow history for a CAPA case, follow these steps:

1. Go to **Inventory management** > **Periodic tasks** > **CAPA management** > **All CAPA cases**.
1. Open the relevant case.
1. On the Action Pane, select **Workflow**, and then select **Workflow history**. Learn more in [View workflow history](../../fin-ops-core/fin-ops/organization-administration/tasks/view-workflow-history.md).

## Related information

- [Corrective and preventive action (CAPA) management overview](capa-overview.md)
- [CAPA management administration](capa-admin.md)
- [Manage CAPA cases](capa-manage-cases.md)
- [Quality order approval workflows](quality-order-approval-workflow.md)
- [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md)
- [Create workflows overview](../../fin-ops-core/fin-ops/organization-administration/create-workflow.md)
- [Actions in workflow approval processes](../../fin-ops-core/fin-ops/organization-administration/workflow-actions.md)
