---
# required metadata

title: Workflow system overview
description: This article describes the workflow system.
author: ChrisGarty
ms.date: 07/25/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: ["56381", "intro-internal"]
ms.assetid: 20b78595-e1d9-439a-ae1c-a776a3438919
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Workflow system overview

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-1.md)]

This article describes the workflow system.

## What is workflow?

The term *workflow* can be defined in two ways: as a system and as a business process.

### Workflow is a system

Workflow is a system that runs on the Application Object Server (AOS). The workflow system provides functionality that you can use to create individual workflows, or business processes.

### Workflow is a business process

A workflow represents a business process. It defines how a document flows, or moves, through the system by showing who must complete a task, make a decision, or approve a document. For example, the following illustration shows a workflow for expense reports.

![Workflow with elements that are assigned to users.](./media/workflow_user.gif)

To better understand this workflow, suppose that Sam submits an expense report for USD 7,000. In this scenario, Ivan must review the receipts submitted by Sam. Then Frank and Sue must approve the expense report. Now suppose that Sam submits an expense report for USD 11,000. In this scenario, Ivan must review the receipts, and Frank, Sue, and Ann must approve the expense report.

## Benefits of using the workflow system

There are several benefits of using the workflow system in your organization:

- **Consistent processes** – You can define how specific documents, such as purchase requisitions and expense reports, are processed. By using the workflow system, you ensure that documents are processed and approved in a consistent and efficient manner.
- **Process visibility** – You can track the status, history, and performance metrics of workflow instances. This helps you determine whether changes should be made to the workflow to improve efficiency.
- **Centralized work list** – Users can view a centralized work list that displays the workflow tasks and approvals that are assigned to them.


## Workflow content

+ [Workflow system architecture](workflow-system-architecture.md)
+ [Workflow elements](workflow-elements.md)
+ [Actions in workflow approval processes](workflow-actions.md)
+ [Create workflows overview](create-workflow.md)
+ [Configure workflow properties](configure-workflow-properties.md)
+ [Configure manual tasks in a workflow](configure-manual-task-workflow.md)
+ [Configure automated tasks in a workflow](configure-automated-task-workflow.md)
+ [Configure approval processes in a workflow](configure-approval-process-workflow.md)
+ [Configure approval steps in a workflow](configure-approval-step-workflow.md)
+ [Configure manual decisions in a workflow](configure-manual-decision-workflow.md)
+ [Configure conditional decisions in a workflow](configure-conditional-decision-workflow.md)
+ [Configure parallel activities in a workflow](configure-parallel-activity-workflow.md)
+ [Configure parallel branches in a workflow](configure-parallel-branch-workflow.md)
+ [Configure line-item workflows](configure-line-item-workflow.md)
+ [Workflow FAQ](workflow-FAQ.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
