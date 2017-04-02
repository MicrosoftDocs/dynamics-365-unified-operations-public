---
# required metadata

title: Purchase requisition workflow
description: The workflow process moves purchase requisitions through the review process, from an initial status of Draft to a final status of Approved. When a purchase requisition is submitted for review, the workflow process is started. After a purchase requisition is approved, a purchase order can be generated for the purchase requisition lines and submitted to the vendor for order fulfillment.
author: YuyuScheller
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: PurchReqAuthorization, WorkflowParticipantExpenToken
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 2234
ms.assetid: dad3ba5a-2892-45d2-874a-300896f59b34
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Purchase requisition workflow

The workflow process moves purchase requisitions through the review process, from an initial status of Draft to a final status of Approved. When a purchase requisition is submitted for review, the workflow process is started. After a purchase requisition is approved, a purchase order can be generated for the purchase requisition lines and submitted to the vendor for order fulfillment.

Before a purchase requisition can be submitted for review, you must configure a workflow. The workflow process can include one or more review steps, in any order. The workflow process can also be configured to skip the review tasks and automatically approve the purchase requisition. You can configure the workflow to route the purchase requisition as a single document, or you can route individual purchase requisition lines to the appropriate reviewers. You can also create a scenario where the purchase requisition is routed as a single document to some reviewers and selected purchase requisition lines are routed to other reviewers.  

If purchase requisition lines are reviewed individually, the review process must be completed for all purchase requisition lines before the workflow process can move to the next step, and before the review process for the purchase requisition as a whole can be completed. When the review process has been completed for the purchase requisition and all its lines, the overall status of the purchase requisition is updated to **Approved**.  

You can configure your workflow to represent the business process for purchase requisitions in your organization. When you configure your purchase requisition workflow process, consider the following questions:

-   What expenditures must be reviewed?
-   What expenditures can be automatically approved?
-   Who is required to review and approve expenditure requests? What role are these users assigned to?
-   What process must be followed if a reviewer is not available?

The following examples illustrate two ways that you can configure a workflow for purchase requisitions.

## Example 1: Route a purchase requisition as a single document for review
The following illustration shows how a purchase requisition can flow through the workflow review process as a single document. The lines on the purchase requisition aren't routed individually. The following roles are included in the workflow process for this example:

-   **Requester** – The user who requests the items or services. The requester can prepare the purchase requisition, or another worker can prepare the purchase requisition on the requester’s behalf. This worker is the preparer. The preparer is responsible for managing the purchase requisition throughout the review process. Only the preparer of the purchase requisition can modify it.

**Note:** A worker must be granted the appropriate permissions to create a purchase requisition on behalf of someone else. Use the **Purchase requisition permission** page to set up these permissions.

-   **Purchasing agent** – The user who performs a procurement review and can approve the document.
-   **The requester's manager** – The user who performs a managerial review and can approve the document.

![Purchase requisition workflow review process](./media/purchreqworkflowoverview_submission.gif)  
In this example, the workflow process for the purchase requisition includes the following steps:

1.  The preparer submits a purchase requisition for review.
2.  The purchasing agent receives a notification. The notification requests that the purchasing agent verify the information in the purchase requisition. If required information is missing, the purchasing agent can either add it or return the purchase requisition to the preparer to add it. When all the required information has been filled in, the purchase requisition can move to the next step in the review process.
3.  The requester's manager reviews the purchase requisition. The purchase requisition might be routed to the requester's manager if, for example, the amount of the purchase requisition exceeds the requester’s spending limit for purchase requisitions. The requester's manager can approve or reject the purchase requisition, or return it to the preparer for changes.

## Example 2: Route the individual purchase requisition lines for review
The following illustration shows how the individual purchase requisition lines can be routed through a workflow. In general, the process for each line is the same as the process for a purchase requisition that is reviewed as a single document. However, each line must complete the workflow process individually before the workflow can be completed for the whole purchase requisition.  

In this example, a worker enters a request for posters and T-shirts for a marketing campaign. The cost of the posters is split between the Marketing department and the Sales department. If the cost of the posters or T-shirts exceeds the signing limit authority for department managers, the purchase requisition must also be reviewed by the group manager.  

The following roles are included in the workflow process for this example:

-   **Requester** – The user who requests the items or services. The requester can prepare the purchase requisition, or another worker can prepare the purchase requisition on the requester’s behalf. This worker is the preparer. The preparer is responsible for managing the purchase requisition throughout the review process. Only the preparer of the purchase requisition can modify it.

**Note:** A worker must be granted the appropriate permissions to create a purchase requisition on behalf of someone else. Use the **Purchase requisition permission** page to set up these permissions.

-   **Purchasing agent** – The user who performs a procurement review and can approve the document.
-   **The requester's manager** – The user who performs a managerial review and can approve the document.
-   **Department manager** – The user who performs an expenditure review and can approve the document.
-   **Group manager** – The user who performs a signature authority review and can approve the document.

![Purchase requisition line workflow review process](./media/purchreqlineworkflowoverview.gif)  
In this example, the workflow process for the purchase requisition lines includes the following steps:

1.  The preparer submits a purchase requisition for review. Each line is routed to the reviewer who is configured to receive it in the workflow process.
2.  The purchasing agent receives a notification. The notification requests that the purchasing agent verify the information in the purchase requisition and on the purchase requisition lines. When the purchase requisition is opened by the purchasing agent all the lines are visible, but a visual indicator shows which lines have been sent to the purchasing agent for review. If required information is missing, the purchasing agent can either add it or return a purchase requisition line to the preparer to add it. When all the required information has been filled in, the purchase requisition line can move to the next step in the review process. Purchase requisition lines can continue through the review process independently of each other.
3.  The requester's line manager reviews and approves the purchase requisition lines. The approval might be routed to the requester's manager if, for example, the amount on a purchase requisition line exceeds the requester’s spending limit for purchase requisition lines. The manager can approve or reject one or both of the purchase requisition lines.
4.  The department manager for the Marketing department reviews the purchase requisition lines for both the posters and the T-shirts. The Sales department manager reviews the purchase requisition line only for the posters, because that is the only cost that is being charged to the Sales department.
5.  The group manager reviews and approves the purchase requisition line for the T-shirts only if group manager approval is required because, for example, the amount on the purchase requisition line exceeds the department manager’s approval limit. The group manager does not have to approve the purchase requisition line for the posters.

## Configuring a workflow for purchase requisitions
To route a purchase requisition for review, you must configure the purchase requisition workflow processes. The workflow process that you define controls the interaction between the user who requested the items (the requester) and the reviewer and approver in the workflow. The routing of the purchase requisition depends on the conditions that are specified in the workflow configuration. For example, these conditions determine when the purchase requisition should be routed, the user or role that it should be routed to, and the actions that users can take.  

The examples in this topic show how a purchase requisition can be routed through a workflow as a single document or as individual purchase requisition lines. You can also configure a workflow for purchase requisitions that reflects the internal control review of purchase requisitions that is defined for your organization.  

The participants or the reviewers that a task is assigned to in a workflow can be members of a particular user group, users who have a particular security role, users who are associated with the submitter in a managerial hierarchy, or named users or users who have specific expenditure responsibilities.

### Purchase requisition expenditure reviewers

Expenditure reviewer configurations let you dynamically route expenditures for review, based on the user who is assigned to a project role or a financial dimension where the expenditure is being charged. The workflow process uses the specified project role or financial dimension owner to determine who the expenditure should be routed to.  

You can define one or more expenditure reviewer configurations and then select a configuration when you create a workflow. You can configure the expenditure reviewer values for every legal entity in your organization. After you define the expenditure reviewer configurations, you assign a configuration to your workflow task.  

You don't have to define expenditure reviewer configurations. Instead, you can assign specific users or user groups as reviewers when you define your workflow. However, if you have a complex organization, expenditure reviewers can increase the efficiency of your approval process. In addition, if you set up expenditure reviewers, you don't have to update workflow reviewer assignments every time that a reviewer changes job roles.  

You can set up the expenditure reviewers on the **Purchase requisition expenditure reviewers** page. Create an expenditure reviewer configuration, and enter values for each legal entity in your organization. For requisitions that are assigned to a project, you can specify the role that is responsible for reviewing the requisitions: Project manager, Project controller, or Project sales manager. Expenditures will be routed to the user who is assigned to the specified role. You can also route the expenditure to the financial dimension owner by selecting the appropriate financial dimension option on the **Organization distributions** tab.  

To use one of the expenditure reviewers that you set up in a workflow, you must set the **Type of participant** option to **Expenditure participants** in the **Assignment** properties for the relevant workflow element.

See also
--------

[Create a requisition for consumption (task guide)](https://ax.help.dynamics.com/en/wiki/create-a-requisition-for-consumption/)

[Defining business process workflows for purchase requisitions](https://mbs.microsoft.com/customersource/Global/AX/learning/documentation/white-papers/Defining_business_process_workflows_for_purchase_requisitions)

[Procurement and sourcing workflows](procurement-sourcing-workflows.md)

[Purchase requisition overview](purchase-requisitions-overview.md)

