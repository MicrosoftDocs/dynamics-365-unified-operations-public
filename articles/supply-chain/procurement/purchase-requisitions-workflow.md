---
title: Purchase requisition workflow
description: The workflow process moves purchase requisitions through the review process, from an initial status of Draft to a final status of Approved.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchReqAuthorization, WorkflowParticipantExpenToken, PurchReqTable
ms.topic: how-to
ms.date: 11/09/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Purchase requisition workflow

[!INCLUDE [banner](../includes/banner.md)]

The workflow process moves purchase requisitions through the review process, from an initial status of Draft to a final status of Approved. When you submit a purchase requisition for review, you start the workflow process. After a purchase requisition is approved, you can generate a purchase order for the purchase requisition lines and submit it to the vendor for order fulfillment.

Before you can submit a purchase requisition for review, you must configure a workflow. The workflow process can include one or more review steps, in any order. You can also configure the workflow process to skip the review tasks and automatically approve the purchase requisition. You can configure the workflow to route the purchase requisition as a single document, or you can route individual purchase requisition lines to the appropriate reviewers. You can also create a scenario where the purchase requisition is routed as a single document to some reviewers and selected purchase requisition lines are routed to other reviewers.  

If you review purchase requisition lines individually, you must complete the review process for all purchase requisition lines before the workflow process can move to the next step, and before the review process for the purchase requisition as a whole can be completed. When you complete the review process for the purchase requisition and all its lines, update the overall status of the purchase requisition to *Approved*.  

You can configure your workflow to represent the business process for purchase requisitions in your organization. When you configure your purchase requisition workflow process, consider the following questions:

- What expenditures must be reviewed?
- What expenditures can be automatically approved?
- Who is required to review and approve expenditure requests? What role are these users assigned to?
- What process must be followed if a reviewer isn't available?

## Add a line after requesting a change

If you can't add a line to a purchase requisition after requesting a change, recall the submitted requisition from workflow. Requesting a change isn't the same as recalling the document.

Recall applies to the whole purchase requisition and all its lines. Verify that the requisition has *Draft* status before you edit it or add a line. Learn more about requisition statuses and recall in [Purchase requisitions overview](purchase-requisitions-overview.md).

## Workflow configuration examples

The following examples illustrate two ways that you can configure a workflow for purchase requisitions.

### Example 1: Route a purchase requisition as a single document for review

The following illustration shows how a purchase requisition can flow through the workflow review process as a single document. The lines on the purchase requisition aren't routed individually. The workflow process for this example includes the following roles:

- *Requester* – The user who requests the items or services. The requester can prepare the purchase requisition, or another worker can prepare the purchase requisition on the requester’s behalf. This worker is the preparer. The preparer is responsible for managing the purchase requisition throughout the review process. Only the preparer of the purchase requisition can modify it. You must grant a worker the appropriate permissions to create a purchase requisition on behalf of someone else. Use the **Purchase requisition permission** page to set up these permissions.
- *Purchasing agent* – The user who performs a procurement review and can approve the document.
- *The requester's manager* – The user who performs a managerial review and can approve the document.

:::image type="content" source="./media/purchase-requisition-workflow-review-process.gif" alt-text="Diagram of a purchase requisition workflow with Requester, Purchasing Agent, and Requester's Manager swimlanes, showing review, approval, return, and reject paths." lightbox="./media/purchase-requisition-workflow-review-process.gif":::

In this example, the workflow process for the purchase requisition includes the following steps:

1. The preparer submits a purchase requisition for review.
1. The purchasing agent receives a notification. The notification requests that the purchasing agent verify the information in the purchase requisition. If required information is missing, the purchasing agent can either add it or return the purchase requisition to the preparer to add it. When all the required information is filled in, the purchase requisition can move to the next step in the review process.
1. The requester's manager reviews the purchase requisition. The purchase requisition might be routed to the requester's manager if, for example, the amount of the purchase requisition exceeds the requester’s spending limit for purchase requisitions. The requester's manager can approve or reject the purchase requisition, or return it to the preparer for changes.

### Example 2: Route the individual purchase requisition lines for review

The following illustration shows how you can route individual purchase requisition lines through a workflow. In general, the process for each line is the same as the process for a purchase requisition that you review as a single document. However, each line must complete the workflow process individually before the workflow can be completed for the whole purchase requisition.  

In this example, a worker enters a request for posters and T-shirts for a marketing campaign. The Marketing and Sales departments split the cost of the posters. If the cost of the posters or T-shirts exceeds the signing limit authority for department managers, the group manager must also review the purchase requisition.  

The following roles are included in the workflow process for this example:

- *Requester* – The user who requests the items or services. The requester can prepare the purchase requisition, or another worker can prepare the purchase requisition on the requester’s behalf. This worker is the preparer. The preparer is responsible for managing the purchase requisition throughout the review process. Only the preparer of the purchase requisition can modify it. A worker must be granted the appropriate permissions to create a purchase requisition on behalf of someone else. Use the **Purchase requisition permission** page to set up these permissions.
- *Purchasing agent* – The user who performs a procurement review and can approve the document.
- *The requester's manager* – The user who performs a managerial review and can approve the document.
- *Department manager* – The user who performs an expenditure review and can approve the document.
- *Group manager* – The user who performs a signature authority review and can approve the document.

:::image type="content" source="./media/purchase-requisition-line-workflow-overview.gif" alt-text="Diagram of a purchase requisition split into posters and T-shirts lines, each routed through separate review steps to an approved purchase requisition." lightbox="media/purchase-requisition-line-workflow-overview.gif":::

In this example, the workflow process for the purchase requisition lines includes the following steps:

1. The preparer submits a purchase requisition for review. Each line is routed to the reviewer who is configured to receive it in the workflow process.
1. The purchasing agent receives a notification. The notification requests that the purchasing agent verify the information in the purchase requisition and on the purchase requisition lines. When the purchasing agent opens the purchase requisition, all the lines are visible, but a visual indicator shows which lines have been sent to the purchasing agent for review. If required information is missing, the purchasing agent can either add it or return a purchase requisition line to the preparer to add it. When all the required information is filled in, the purchase requisition line can move to the next step in the review process. Purchase requisition lines can continue through the review process independently of each other.
1. The requester's line manager reviews and approves the purchase requisition lines. The approval might be routed to the requester's manager if, for example, the amount on a purchase requisition line exceeds the requester’s spending limit for purchase requisition lines. The manager can approve or reject one or both of the purchase requisition lines.
1. The department manager for the Marketing department reviews the purchase requisition lines for both the posters and the T-shirts. The Sales department manager reviews the purchase requisition line only for the posters, because that's the only cost that is being charged to the Sales department.
1. The group manager reviews and approves the purchase requisition line for the T-shirts only if group manager approval is required because, for example, the amount on the purchase requisition line exceeds the department manager’s approval limit. The group manager doesn't have to approve the purchase requisition line for the posters.

> [!NOTE]
> You must set the system currency if the header workflow for a purchase requisition requires approvals related to signing limits.

## Configuring a workflow for purchase requisitions

To route a purchase requisition for review, you must configure the purchase requisition workflow processes. The workflow process that you define controls the interaction between the user who requested the items (the requester) and the reviewer and approver in the workflow. The routing of the purchase requisition depends on the conditions that you specify in the workflow configuration. For example, these conditions determine when the purchase requisition should be routed, the user or role that it should be routed to, and the actions that users can take.  

The examples in this article show how a purchase requisition can be routed through a workflow as a single document or as individual purchase requisition lines. You can also configure a workflow for purchase requisitions that reflects the internal control review of purchase requisitions that is defined for your organization.  

The participants or the reviewers that a task is assigned to in a workflow can be members of a particular user group, users who have a particular security role, users who are associated with the submitter in a managerial hierarchy, or named users or users who have specific expenditure responsibilities.

### Purchase requisition expenditure reviewers

Expenditure reviewer configurations let you dynamically route expenditures for review, based on the user who is assigned to a project role or a financial dimension where the expenditure is being charged. The workflow process uses the specified project role or financial dimension owner to determine who the expenditure should be routed to.  

You can define one or more expenditure reviewer configurations and then select a configuration when you create a workflow. You can configure the expenditure reviewer values for every legal entity in your organization. After you define the expenditure reviewer configurations, you assign a configuration to your workflow task.  

You don't have to define expenditure reviewer configurations. Instead, you can assign specific users or user groups as reviewers when you define your workflow. However, if you have a complex organization, expenditure reviewers can increase the efficiency of your approval process. In addition, if you set up expenditure reviewers, you don't have to update workflow reviewer assignments every time that a reviewer changes job roles.  

You can set up the expenditure reviewers on the **Purchase requisition expenditure reviewers** page. Create an expenditure reviewer configuration, and enter values for each legal entity in your organization. For requisitions that are assigned to a project, you can specify the role that is responsible for reviewing the requisitions: Project manager, Project controller, or Project sales manager. Expenditures route to the user who is assigned to the specified role. You can also route the expenditure to the financial dimension owner by selecting the appropriate financial dimension option on the **Organization distributions** tab.  

To use one of the expenditure reviewers that you set up in a workflow, you must set the **Type of participant** option to **Expenditure participants** in the **Assignment** properties for the relevant workflow element.

## Related information

- [Create a requisition for consumption](tasks/create-requisition-consumption.md)
- [Defining business process workflows for purchase requisitions](https://www.microsoft.com/download/details.aspx?id=101821)
- [Procurement and sourcing workflows](procurement-sourcing-workflows.md)
- [Purchase requisition overview](purchase-requisitions-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
