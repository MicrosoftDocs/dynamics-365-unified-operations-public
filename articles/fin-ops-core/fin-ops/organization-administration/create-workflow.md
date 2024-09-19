---
title: Create workflows overview
description: Learn about how to create a workflow, including outlines on opening the workflow editor and configuring the properties of a workflow.
author: ChrisGarty
ms.author: cgarty
ms.topic: overview
ms.date: 09/19/2024
ms.custom: 
  - bap-template
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-08-30
ms.search.form: WorkflowSelectTemplateRnr, WorkflowTableListPageRnr
ms.dyn365.ops.version: Platform update 2
ms.assetid: 836ddd01-cc34-45c3-a4b0-20647357dbc6
---

# Create workflows overview

[!include [banner](../includes/banner.md)]

This article explains how to create a workflow.

## Open the workflow editor

The module that you're working in determines the types of workflow that you can create. To select the type of workflow to create a new workflow using the workflow editor, follow these steps.

1. Open the module that you want to create a new workflow for. For example, to create a workflow for purchase requisitions, select **Procurement and sourcing**.
2. Select **Setup** &gt; **\[Module name\] workflows**.
3. On the list page that appears, on the Action Pane, select **New**.
4. On the **Create workflow** page, select the type of workflow to create, and then select **Create workflow**. The workflow editor is launched. 
5. Select or sign in to the account to use with the workflow editor. If prompted to **Stay signed in to all your apps**, select **OK** to allow the account to automatically sign in to the workflow editor and other apps in the future, or select **No, sign in to this app only** if you prefer to only sign in to the workflow editor for this session.

## Drag workflow elements onto the canvas

The **Workflow elements** area of the workflow editor contains the elements that you can add to your workflow. To add elements to the workflow, drag them onto the canvas.

## Connect the elements

To connect one workflow element to another, hold the pointer over an element until connection points appear. Select a connection point, and drag it to another element. Be sure to connect all the elements.

## Configure the properties of the workflow

Follow these steps to configure the properties of the workflow.

1. Select the canvas to make sure that no workflow element is selected.
2. Select **Properties** to open the **Properties** page for the workflow.
3. Follow the procedures in the [Configure workflow properties](configure-workflow-properties.md) article.

## Configure the elements of the workflow

Configure each element that you dragged onto the canvas. For information about how to configure each workflow element, see the following topics:

- [Configure manual tasks in a workflow](configure-manual-task-workflow.md)
- [Configure automated tasks in a workflow](configure-automated-task-workflow.md)
- [Configure approval processes in a workflow](configure-approval-process-workflow.md)
- [Configure approval steps in a workflow](configure-approval-step-workflow.md)
- [Configure manual decisions in a workflow](configure-manual-decision-workflow.md)
- [Configure conditional decisions in a workflow](configure-conditional-decision-workflow.md)
- [Configure parallel branches in a workflow](configure-parallel-activity-workflow.md)
- [Configure a parallel branch](configure-parallel-branch-workflow.md)
- [Configure line-item workflows](configure-line-item-workflow.md)

## Resolve any errors or warnings

The **Errors and warnings** pane at the bottom of the workflow editor shows messages that have been generated for the workflow. To find the element where an error or warning occurred, double-click the error or warning message. You must resolve all errors and warnings before you can make the workflow active.

## Save and activate the workflow

When you're ready to save and activate the workflow, follow these steps.

1. Select **Save and close** to close the workflow editor and open the **Save workflow** page.
2. Enter comments about the changes that you've made to the workflow, and then select **OK**.
3. If all errors and warnings have been resolved, the **Activate workflow** page appears. Select one of the following options:

    - To activate this version of the workflow, select **Activate the new version**. When a workflow is active, users can submit documents to it for processing.
    - If you don't want to activate this version, select **Do not activate the new version**. You can activate the workflow later.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
