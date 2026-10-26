---
title: Set up and use quality order approval workflows (preview)
description: Learn how to set up and use approval workflows that route quality order test results to reviewers before the quality order is validated.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: InventQualityOrderTable, WorkflowTableListPageRnr
ms.topic: how-to
ms.date: 10/23/2026
ms.custom: 
  - bap-template
ai-usage: ai-assisted
---

# Set up and use quality order approval workflows (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

In regulated industries, a quality technician who records test results usually isn't allowed to release the tested material. A second person must review the evidence first. Quality order approval workflows add that review step to Microsoft Dynamics 365 Supply Chain Management. When you apply a workflow to a quality order, the technician submits the order instead of validating it. Reviewers then approve the results, return them, or ask for changes. After the final approval, the system runs standard quality order validation automatically, so the order passes or fails based on the recorded results, and the related inventory processing runs as usual. The workflow history stores every review action and comment.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.50 or later.
- The feature named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.47, this feature is turned on by default. As of version 10.0.49, it's mandatory and can't be turned off.
- The feature named *Quality order approval workflow* must be turned on in Feature management. This feature is turned off by default, and you can turn it off again later.
- An active quality order approval workflow configuration must exist and match the quality order. Otherwise, the order keeps its current behavior, and you validate it directly.
- Electronic signatures must not be required for quality order status updates. The two capabilities can't be combined. If a signature is required for a quality order, you can't submit that order for approval, and you must continue to use signed direct validation for it.
- Users who submit or act on quality order workflows need the required workflow privileges. The *Quality control clerk* and *Quality control manager* roles include these privileges by default.
- Each user who gives the final approval must be associated with a worker record. The system records that worker as the validator of the quality order.

## Approval statuses

When you turn on the *Quality order approval workflow* feature, quality orders include an **Approval status** field in addition to the **Status** field. The **Status** field shows whether the order status is *Open*, *Pass*, or *Fail*. The **Approval status** field appears as a column on the **Overview** tab of the **Quality orders** page. The system maintains this field. You can't edit it directly.

The following table describes each **Approval status** value.

| Approval status | Description |
|---|---|
| *Draft* | You didn't submit the quality order yet. You can edit the order, its lines, and its results. |
| *Submitted* | You submitted the order and the workflow instance started. The order is locked. |
| *In review* | A reviewer has a pending work item for the order. The order is locked. |
| *Change requested* | A reviewer used **Request change**. The order is unlocked so that you can correct it and resubmit. |
| *Rejected* | A reviewer used **Reject** to return the order. The order is unlocked so that you can correct it and resubmit. |
| *Approved* | The workflow completed, standard validation ran, and the order was finalized as *Pass* or *Fail*. |

While a quality order has an approval status of *Submitted* or *In review*, the system protects the evidence that reviewers are looking at:

- You can't change the quality order header, its lines, or its test results.
- You can't delete the quality order.
- The **Validate**, **Skip**, **Split**, and **Reset** actions are blocked. Use the workflow actions instead.

If a workflow configuration applies to a quality order, you must submit the order for approval. You can't validate it directly, even before you submit it.

## Set up quality order approval workflows

To set up quality order approval workflows, turn on the *Quality order approval workflow* feature, create and activate a workflow configuration, set the conditions that control when it applies, and assign security.

### Turn on the feature

To make quality orders use the approval workflow, follow these steps:

1. Go to **Feature management**.
1. Make sure that *Advanced quality management* is turned on.
1. Select *Quality order approval workflow*, and then select **Enable now**.

### Create a quality order approval workflow

Create a workflow of the *Quality order approval workflow* type for each approval process that your organization needs. The workflow determines which quality orders are routed for review, who reviews them, and in what order. You design it in the workflow editor, just as you design other workflows for Supply Chain Management. Learn more about the workflow editor in [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md), [Create workflows overview](../../fin-ops-core/fin-ops/organization-administration/create-workflow.md), and [Workflow elements](../../fin-ops-core/fin-ops/organization-administration/workflow-elements.md).

To create a quality order approval workflow, follow these steps:

1. Go to **Inventory management** > **Setup** > **Inventory management workflows**.
1. On the Action Pane, select **New**.
1. In the **Create workflow** dialog box, under **Quality management workflows**, select **Quality order approval workflow**, and then select **Create workflow**.
1. The workflow editor app starts on your machine. (You might be asked to approve this action.) Use it to design your workflow as required.

    Your design must meet the following requirements. If it doesn't, users can't submit quality orders to the workflow.

    - The workflow must contain at least one *Approve quality order* approval element. Learn more in [Configure approval processes in a workflow](../../fin-ops-core/fin-ops/organization-administration/configure-approval-process-workflow.md) and [Configure approval steps in a workflow](../../fin-ops-core/fin-ops/organization-administration/configure-approval-step-workflow.md).
    - No element in the workflow can use automatic actions (automatic completion). Every approval must be made by a person, because the final approver becomes the validator of the quality order.

1. Save your work, and close the workflow editor app.
1. Choose whether to activate this workflow version or keep it inactive. Only one version can be active at a time for each workflow ID.

### Set conditions that control when the workflow applies

Use the submission conditions on the workflow to control which quality orders the workflow applies to. If no active workflow configuration matches a quality order, that order keeps its current behavior, and you validate it directly.

In addition to the fields of the quality order, you can use the following calculated values in workflow conditions. The system evaluates them against the current test results each time it runs the condition.

- **All tests passed** – *Yes* when at least one included, non-skipped test exists and all such tests pass, based on their current results. The value is *No* if all tests are skipped or excluded.
- **Failed test count** – The number of included, non-skipped tests whose result isn't *Pass*. Skipped and excluded tests aren't counted.
- **Skipped test count** – The number of tests that are marked as skipped, whether or not their results are included.

For example, you can use these values to route failing quality orders to a quality manager, and to let orders where every test passed follow a shorter review path.

### Assign security

Two privileges control access to quality order approval workflows. One privilege grants access to submit, recall, and resubmit quality orders. The other grants access to approve, reject, request changes to, and delegate approval work items.

Both privileges are included in the standard duties that are assigned to the *Quality control clerk* role. They're also included in the *Process quality order approval workflows* duty, which is assigned to the *Quality control manager* role by default. This manager duty grants workflow access without granting permission to create, edit, validate, or reopen quality orders. Add the duty to any custom role that must submit quality orders or act on approval work items.

The workflow configuration determines who receives a work item, and security determines whether that person can act on it. Assign participants who have the required duty. Otherwise, the workflow can't create the work item because the participant has insufficient permissions.

By default, a user can approve a quality order that they submitted if they're assigned to the approval. To prevent this behavior, turn on **Disallow approval by submitter** at **System administration** > **Setup** > **Workflow** > **Workflow parameters**.

## Submit a quality order for approval

Submit a quality order when you finish entering test results and the evidence is complete. Submission validates the results, starts the workflow, and locks the quality order so that reviewers can rely on what they see.

To submit a quality order for approval, follow these steps:

1. Go to **Inventory management** > **Periodic tasks** > **Quality management** > **Quality orders**.
1. Select or open the quality order that you want to submit.
1. Enter the test results for the order. Learn more in [Enter quality test results quickly](quality-quick-results-entry.md).
1. On the Action Pane, select **Workflow**, and then select **Submit**.
1. In the **Submit** dialog box, enter a comment for the reviewers, and then select **Submit**.

The approval request routes to the reviewers that the workflow defines. They get notified by using the notification method that's configured for the workflow.

Before the workflow starts, the system checks the quality order. If any of the following checks fail, the system cancels the submission and displays a message that explains what to correct:

- The quality order must have at least one test.
- Each non-skipped test must have at least one included result row.
- Each included result row must have a result. A value of zero counts as an entered result.
- Each included option test must have an outcome.

Submission doesn't check result quantities, catch weight quantities, or instrument tags.

To withdraw a request that's still in review, select **Workflow** > **Recall**. The approval status returns to *Draft*, the order is unlocked, and the workflow history is retained.

### Resubmit a quality order after a review

If a reviewer rejects the quality order or requests a change, you receive a work item, and the order is unlocked. Correct the results, and then return the order to the same workflow instance so that the review continues where it left off.

To resubmit a quality order, follow these steps:

1. Go to **Inventory management** > **Periodic tasks** > **Quality management** > **Quality orders**.
1. Open the quality order. Its approval status is either *Rejected* or *Change requested*.
1. Correct the test results as required.
1. On the Action Pane, select **Workflow**, and then select **Resubmit**.
1. In the dialog box, enter a comment, and then select **Resubmit**.

> [!NOTE]
> Resubmission uses the workflow version that was active when the order was first submitted. Therefore, a quality order that's already in review isn't affected if you activate a new version of the workflow.

## Respond to a quality order approval request

If you're a reviewer, you receive a work item each time your approval is required. Review the test results, and then record your decision from the quality order.

To respond to a quality order approval request, follow these steps:

1. Go to **Inventory management** > **Periodic tasks** > **Quality management** > **Quality orders**.
1. Open the relevant quality order, and review its test results.
1. On the Action Pane, select **Workflow**, and then select one of the following actions:

    - **Approve** – Approve the results. If this approval is the last one that the workflow requires, the system finalizes the quality order.
    - **Reject** – Return the order to the submitter. The approval status is set to *Rejected*, and the order is unlocked for correction.
    - **Request change** – Ask the submitter for a specific correction. The approval status is set to *Change requested*, and the order is unlocked for correction.
    - **Delegate** – Assign your work item to another user. Learn more in [Delegate work items in a workflow](../../fin-ops-core/fin-ops/organization-administration/tasks/delegate-work-items-workflow.md).

Both **Reject** and **Request change** keep the workflow instance open, so the submitter resubmits to the same instance instead of starting a new review.

## How the system finalizes an approved quality order

When the last required approval is given and the workflow completes, the system finalizes the quality order in a single transaction. It runs the standard quality order validation on your behalf, with the following settings:

- **Accept error** is set to *No*. The outcome therefore reflects the recorded results. An approval can't make a failing quality order pass.
- **Validated by** is set to the worker who gave the last approval in the current review cycle. If that user isn't associated with a worker, finalization fails, and the quality order stays in review.

Validation sets the status of the quality order to *Pass* or *Fail*, and it runs the inventory processing that's associated with that outcome, such as the release of inventory blocking. The approval status is then set to *Approved*. If validation doesn't produce a *Pass* or *Fail* result, the whole operation is rolled back, and the quality order remains in its previous state.

If you later reopen a finalized quality order, its approval status returns to *Draft*, and it's disconnected from the completed workflow instance. You can then correct the results and submit the order for a new review.

## Review the approval history

As with other types of workflows, use the **Workflow history** page to review who acted on a quality order, when they acted, and which comments they entered.

To review the workflow history for a quality order, follow these steps:

1. Go to **Inventory management** > **Periodic tasks** > **Quality management** > **Quality orders**.
1. Open the relevant quality order.
1. On the Action Pane, select **Workflow**, and then select **Workflow history**. Learn more in [View workflow history](../../fin-ops-core/fin-ops/organization-administration/tasks/view-workflow-history.md).

## Related information

- [Quality orders](quality-orders.md)
- [Advanced quality management overview](advanced-quality-management-overview.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Set up and use CAPA case approval workflows](capa-approval-workflow.md)
- [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md)
- [Create workflows overview](../../fin-ops-core/fin-ops/organization-administration/create-workflow.md)
- [Actions in workflow approval processes](../../fin-ops-core/fin-ops/organization-administration/workflow-actions.md)
- [Inventory journal approval workflows](inventory-journal-workflow.md)
