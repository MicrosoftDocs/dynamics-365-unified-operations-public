---
title: Procurement and sourcing workflows
description: Learn about purchase requisitions and purchase orders that are approved by a user other than the person who entered the transaction.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: WorkflowTableListPageRnr
ms.topic: how-to
ms.date: 07/30/2024
ms.custom: 
  - bap-template
---

# Procurement and sourcing workflows

[!include [banner](../includes/banner.md)]

Some organizations require that purchase requisitions and purchase orders are approved by a user other than the person who entered the transaction. To set up an approval process, you can create a workflow.

A workflow represents a business process. It defines how a document flows through the system and indicates who must complete a task or approve a document. There are several benefits of using the workflow system in your organization:

- **Consistent processes** – You can define the approval process for specific documents, such as purchase requisitions and expense reports. Using the workflow system helps to ensure that documents are processed and approved in a consistent and efficient manner.
- **Process visibility** – You can track the status, history, and performance metrics of a specific workflow instance. This helps you determine whether changes should be made to the workflow to improve efficiency.
- **Centralized work list** – Users can view a centralized work list to view the workflow tasks and approvals assigned to them across all workflows they participate in. This is available on the **Work items** page.

## The types of workflows that you can create

The following workflow types are available for Procurement and sourcing.

| Type | Use this type to |
|---|---|
| Purchase requisition review | Create review and approval workflows for purchase requisitions. |
| Purchase requisition line review | Create review and approval workflows for purchase requisition lines. |
| Purchase order workflow | Create review and approval workflows for purchase orders. |
| Purchase order line workflow | Create review and approve workflows for purchase order lines. |
| Vendor add application workflow | Create review and approval workflows for adding new vendors via vendor requests. |

> [!IMPORTANT]
> When you are adding a new workflow, you might also see the following obsolete workflows listed in the **Create workflow** dialog box. These are related to the *confirmation of receipt* functionality that was available in [Dynamics AX 2012](/dynamicsax-2012/appuser-itpro/set-up-procurement-and-sourcing-workflows), but which has now been deprecated. These workflows are currently unsupported.
>
> - Delivery due date notification workflow
> - Invoice received notification workflow
> - Product receipt failed notification workflow
> - Unconfirmed product receipt rejection notification workflow

## Creating a workflow

To create a workflow, go to **Procurement and sourcing** \> **Setup** \> **Procurement and sourcing workflows** and create a new workflow by selecting the type of workflow you want to create.

In the workflow canvas, you can drag workflow elements into the designer and link the elements into a flow. The workflow elements should be configured. For approval and task workflow elements, you can configure which participant should take action.

## Types of participants

You can assign an approval step to the following groups of participants.

| User group | Description |
|---|---|
| Participant | Assign the approval step to members of a group or role. |
| Hierarchy | Assign the approval step to users in a specific organizational hierarchy. |
| Workflow user | Assign the approval step to users of this workflow. |
| Queue | Assign the approval step to a work item queue. |
| User | Assign the approval step to specific users. |

## Related information

- [Defining business process workflows for purchase requisitions](https://www.microsoft.com/download/details.aspx?id=101821)
- [Purchase requisition workflow](purchase-requisitions-workflow.md)
- [Onboard vendors](vendor-onboarding.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
