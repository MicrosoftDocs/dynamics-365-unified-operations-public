---
title: Workflow business events
description: Learn about workflow business events, which are generated at various points in the processing of a workflow, including an overview of workflow components.
author: ChrisGarty
ms.author: cgarty
ms.topic: upgrade-and-migration-article
ms.date: 04/08/2026
# ms.custom: [used by loc for topics migrated from the wiki]
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global 
ms.search.validFrom: 2019-3-31
# ms.search.form:  [Operations AOT form name to tie this article to]
ms.dyn365.ops.version: Platform update 24
---

# Workflow business events

[!include[banner](../includes/banner.md)]

Workflow business events are generated at various points in the processing of a workflow.

## Workflow construction

To construct a workflow, a developer defines workflow components in metadata and code by using the Visual Studio tools.

An administrator creates workflows in the web client and then designs them in the workflow designer. For more information, see [Create workflows](../../fin-ops/organization-administration/create-workflow.md).

### Workflow components

Define workflow components in metadata as follows:

- **Workflow types** - Also known as templates, workflow types define the elements allowed in a workflow. The administrator decides which elements to use when they create the workflow design.
  - In the Application Explorer, go to **AOT > Business Process and Workflow > Workflow Types**.
- **Workflow elements** - Workflow elements are the executable pieces that make up a workflow. For details, see [Workflow elements](../../fin-ops/organization-administration/workflow-elements.md).
  - Tasks (aka manual tasks) - Go to **AOT > Business Process and Workflow > Workflow Tasks**.
  - Approvals - Go to **AOT > Business Process and Workflow > Workflow Approvals**.
  - Automated tasks - Go to **AOT > Business Process and Workflow > Workflow Automated Tasks**.

## Workflow runtime

After a user submits a workflow, the system adds it to a queue and runs it by using the **Workflow message processing** batch job. As the workflow runs, it progresses through all the [connected workflow elements](../../fin-ops/organization-administration/create-workflow.md#connect-the-elements) until it reaches the end. When the workflow runtime encounters a [manual task element](../../fin-ops/organization-administration/workflow-elements.md#manual-task), it creates a work item for the [user assigned to the task](../../fin-ops/organization-administration/configure-manual-task-workflow.md#assign-the-task). When the workflow runtime encounters an [approval element](../../fin-ops/organization-administration/workflow-elements.md#approval-processes), it creates a work item for each [user assigned to each approval step](../../fin-ops/organization-administration/configure-approval-step-workflow.md#assign-the-approval-step).

## Workflow business event categories

Workflow business events fall into five categories. Microsoft Power Automate displays the category to help you select the right event.

:::image type="content" source="media/Business-event-category.png" alt-text="Screenshot of business event categories in Microsoft Power Automate.":::

- **Category: Workflow type**
  - These events trigger on workflow events, such as when a workflow starts or finishes. This category represents all workflow instances.
  - Example: Purchase requisition approval workflow started
  - **ID format** - "Workflow_" + Workflow name + Workflow instance ID, for example "Workflow_BudgetPlanReview_000002"
- **Category: Workflow element started**
  - These events trigger when a workflow element starts. This category represents all enabled workflow elements within a workflow instance.
  - Example: Purchase requisition automated approval started
  - **ID format** - "Workflow_" + Workflow name + Workflow instance ID + "_" + Workflow element name + "_Started", for example "Workflow_BudgetPlanReview_000002_BudgetActivateBudgetPlanChild_Started"
- **Category: Workflow element**
  - These events trigger on workflow element events other than started, such as when a workflow element finishes. This category represents all enabled workflow elements within a workflow instance.
  - Example: Purchase requisition automated approval completed
  - **ID format** - "Workflow_" + Workflow name + Workflow instance ID + "_" + Workflow element name, for example "Workflow_BudgetPlanReview_000002_BudgetActivateBudgetPlanChild"
- **Category: Workflow external task**
  - These events trigger when a workflow automated task element starts. This category represents all enabled workflow automated task elements within a workflow instance.
  - Example: Purchase requisition automated approval started
  - **ID format** - "Workflow_" + Workflow name + Workflow instance ID + "_" + Workflow element name + "_ExternalTask", for example "Workflow_BudgetPlanReview_000002_BudgetActivateBudgetPlanChild_ExternalTask"
- **Category: Workflow work item**
  - These events trigger when a workflow work item is created for a user. This category represents all enabled workflow tasks and workflow approvals within a workflow instance.
  - Example: Purchase requisition manual approval work item created for Bob
  - **ID format** - "Workflow_" + Workflow name + Workflow instance ID + "_" + Workflow element name + "_WorkItem", for example "Workflow_BudgetPlanReview_000002_BudgetActivateBudgetPlanChild_WorkItem"

## Completion of a work item in Power Automate

Workflow business events are a good target for triggering approval flows. You can use the **workflow work item** event along with the validate and complete OData actions to facilitate completion of a work item in Power Automate.

You can complete an approval or task work item in Power Automate by using the following steps:

- Trigger Power Automate by using the **when a business event occurs** trigger targeting the appropriate **workflow work item** event.
- Validate that the **workflow work item** contains a valid set of information so it's ready for completion by calling the **Validate** method on the **WorkflowWorkItems** entity.
- If the work item isn't ready for completion, send a notification to the assigned user to let them know that there's a work item that needs their attention.
- If the work item is ready for completion, request a response from the assigned user by sending the available response options to the user.
- After a response is provided, complete the work item with that response by calling the **Complete** method on the **WorkflowWorkItems** entity.

To enable external completion of work items, the work item action manager class needs to implement the `IValidateWorkflowWorkItemAction` interface. The standard `WorkflowWorkItemActionManager` class implements this interface. In Platform update 32, the `TrvWorkflowWorkItemActionManager` class was updated to implement the `IValidateWorkflowWorkItemAction` interface. Use the existing `IValidateWorkflowWorkItemAction` implementations as examples to notify updates about other `WorkflowWorkItemActionManager` classes.

For a step-by-step guide to setting up work item completion in Microsoft Power Automate, see [Consume workflow approval business events](how-to/how-to-flow.md).

## Troubleshooting workflow business events

### Troubleshooting workflow issues

Ensure that the workflow is running correctly and creating work items as expected. If the workflow doesn't work inside the application so that state changes aren't occurring, the events won't occur. Adjust the workflow configuration as needed. If needed, review the workflow details in the **Workflow History** form.

### Troubleshooting Power Automate issues

Ensure that the Power Automate subscription is available in **System administration > Setup > Business events > Business events catalog** on the **Active events** tab. If the Power Automate subscription isn't there, check Power Automate and recreate it if needed.

### Troubleshooting business events issues

Ensure that other business events are occurring by creating a Power Automate to trigger off another business event. For example, the Free Text Invoice Posted event can be triggered by simply creating a Free Text Invoice with a single line and posting it. For more information, see [Troubleshoot business events](troubleshooting.md).

### Troubleshooting work item approval via Power Automate ###

If a flow tries to handle approval for work items but doesn't trigger, verify these steps:

- Are you creating the work items so the applicable user can see them waiting for approval in the web client?
- Is the event subscription from Power Automate visible in the Business Events form?
- Are the workflow configuration and the event subscription from Power Automate for the correct legal entity (company)?

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
