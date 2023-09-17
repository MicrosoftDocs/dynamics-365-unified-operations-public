---
title: Workflow type checklist
description: This article describes the steps that are required to create a new workflow type.
author: josaw1
ms.date: 06/19/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
ms.custom: 202694
ms.assetid: 33349e0d-d8ac-4d20-8f9b-5f85d4e01004
---

# Workflow type checklist

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

This article describes the steps that are required to create a new workflow type. Workflow types are used to create configurations for a workflow.

## Workflow type checklist

1. If an existing category isn't appropriate, create a new workflow category to use for the workflow type. For more information, see [Create a workflow category](workflow-type-category.md).
2. Create a query that accesses the document that the new workflow type is being created for. For more information, see [Create a query for a workflow type](workflow-type-query.md).
3. Create a workflow type in Application Explorer. Typically, you complete this step by using the **Workflow** wizard. For more information, see [Create a new workflow type](workflow-type-create-new.md).

We recommend that you use the **Workflow** wizard to create a workflow type. The wizard performs the following tasks. In some cases, you must add more code for your workflow type. Links are provided so that you can see the details of the actions that the wizard performs and the additional steps that you must perform to complete your workflow type.

1. Create a workflow document class, and then bind the query that is used for the workflow to the class. For more information, see [Create a workflow document class](workflow-type-document-create.md).
2. Bind the workflow document class to the workflow type. For more information, see [Associate a workflow document class with a workflow type](workflow-type-associate-document.md).
3. Create workflow event handlers for started, completed, configuration change, and canceled events, and then bind event handlers to the workflow type. For more information, see [Create a workflow event handler](/dynamicsax-2012/developer/how-to-create-a-workflow-event-handler).
4. Create a class for **SubmitToWorkflowMenuItem**. Optionally create a class for **CancelMenuItem**. Bind the classes to the action menu items that you will create in the next step. For more information, see [Classes and methods](../../dev-itpro/dev-ref/xpp-classes-methods.md).
5. Create an action menu item for the **SubmitToWorkflowMenuItem** workflow property. Optionally create an action menu item for the **CancelMenuItem** property. Bind the actions to the workflow type. For more information, see [Create a new workflow type](workflow-type-create-new.md).

## Next steps

After you create a workflow type, you can add tasks, automated tasks, and approvals.

## See also

[Configure workflow properties](configure-workflow-properties.md)

[Configure manual tasks in a workflow](configure-manual-task-workflow.md)

[Configure automated tasks in a workflow](configure-automated-task-workflow.md)

[Configure approval processes in a workflow](configure-approval-process-workflow.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
