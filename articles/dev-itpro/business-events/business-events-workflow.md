---
# required metadata

title: Workflow business events
description: The workflow business events are generated at various points in the processing of a workflow.
author: ChrisGarty
manager: AnnBe
ms.date: 01/30/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2019-3-31
ms.dyn365.ops.version: Platform update 24
---

# Workflow business events
[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

The workflow business events are generated at various points in the processing of a workflow.   

## Workflow construction

A developer can define workflows components in metadata and code in the Visual Studio tools.

An administrator can [create workflows](../../fin-and-ops/organization-administration/create-workflow) in the web client and then design them in the workflow designer.

### Workflow components
Workflow components are defined in metadata as:
- **Workflow types** (aka templates) define the elements allowed in a 
     - In the Application Explorer: AOT > Business Process and Workflow > Workflow Types 
- **[Workflow elements](../../fin-and-ops/organization-administration/workflow-elements)** are the executable pieces that make up a workflow
     - Tasks (aka Manual Tasks): AOT > Business Process and Workflow > Workflow Tasks
     - Approvals: AOT > Business Process and Workflow > Workflow Approvals
     - Automated Tasks: AOT > Business Process and Workflow > Workflow Automated Tasks

## Workflow runtime
When a workflow is submitted by a user, then it is added to a queue and run via the "Workflow message processing" batch job. As the workflow runs, it will progress through all the [connected workflow elements](../../fin-and-ops/organization-administration/create-workflow#connect-the-elements) until it reaches the end. When the workflow runtime encounters a [manual task element](../../fin-and-ops/organization-administration/workflow-elements#manual-task) it will create a work item for the [user assigned to the task](../../fin-and-ops/organization-administration/configure-manual-task-workflow#assign-the-task). When the workflow runtime encounters an [approval element](../../fin-and-ops/organization-administration/workflow-elements#approval-processes) then it will create a work item for each [user assigned to each approval step](../../fin-and-ops/organization-administration/configure-approval-step-workflow#assign-the-approval-step).

## Workflow business event categories

There are five different categories of workflow business events are: 
- **Category: Workflow type** 
     - These events will fire on workflow events like started and completed. All workflow instances will be represented in this category.
     - **ID format**: "Workflow_" + Workflow name + Workflow instance ID e.g. "Workflow_BudgetPlanReview_000002"
     - **Name format**: Workflow label + " (" + Workflow instance ID ")" e.g. "Prepare department budget (000002)"
- **Category: Workflow element started**
     - These events will fire when a workflow element is started. All enabled workflow elements within a workflow instance will be represented in this category. 
     - **ID format**: "Workflow_" + Workflow name + Workflow instance ID + "_" + Workflow element name + "_Started" e.g. "Workflow_BudgetPlanReview_000002_BudgetActivateBudgetPlanChild_Started"
     - **Name format**: Workflow label + " (" + Workflow instance ID ") - " + Workflow element label e.g. "Prepare department budget (000002) - Activate associated budget plan"
- **Category: Workflow element**
     - These events will fire on workflow element events other than started, such as completed. All enabled workflow elements within a workflow instance will be represented in this category. 
     - **ID format**: "Workflow_" + Workflow name + Workflow instance ID + "_" + Workflow element name e.g. "Workflow_BudgetPlanReview_000002_BudgetActivateBudgetPlanChild"
     - **Name format**: Workflow label + " (" + Workflow instance ID ") - " + Workflow element label e.g. "Prepare department budget (000002) - Activate associated budget plan"
- **Category: Workflow external task** 
     - These events will fire when a workflow automated task element is started. All enabled workflow automated task elements within a workflow instance will be represented in this category. 
     - **ID format**: "Workflow_" + Workflow name + Workflow instance ID + "_" + Workflow element name + "_ExternalTask" e.g. "Workflow_BudgetPlanReview_000002_BudgetActivateBudgetPlanChild_ExternalTask"
     - **Name format**: Workflow label + " (" + Workflow instance ID ") - " + Workflow element label e.g. "Prepare department budget (000002) - Activate associated budget plan"
- **Category: Workflow workitem**
     - These events will fire when a workflow workitem is created for a user. All enable workflow tasks and workflow approvals within a workflow instance will be represented in this category. 
     - **ID format**: "Workflow_" + Workflow name + Workflow instance ID + "_" + Workflow element name + "_WorkItem" e.g. "Workflow_BudgetPlanReview_000002_BudgetActivateBudgetPlanChild_WorkItem"
     - **Name format**: Workflow label + " (" + Workflow instance ID ") - " + Workflow element label e.g. "Prepare department budget (000002) - Activate associated budget plan"
