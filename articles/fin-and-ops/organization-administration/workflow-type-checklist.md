---
# required metadata

title: Workflow type checklist
description: This topic describes the steps necessary to create a new workflow type in Dynamics 365 for Finance and Operations.
author: RobinARH
manager: AnnBe
ms.date: 06/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 202694
ms.assetid: 33349e0d-d8ac-4d20-8f9b-5f85d4e01004
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Workflow type checklist 

This topic describes the steps to follow to create a new workflow type for Finance and Operations. Workflow types are used to create configurations for a workflow in a Finance and Operations application.

## Workflow type checklist

1.  If an existing category is not appropriate, create a new workflow category to use for the workflow type. For more information, see [Create a workflow category](workflow-type-category.md).

2.  Create a query that accesses the document for which the new workflow type is being created. For more information, see [Create a query for a workflow type](workflow-type-query.md).

3.  Create a workflow type in Application Explorer. Typically, you do this using the Workflow Wizard. For more information, see [Create a new workflow type](workflow-type-create-new).

We recommend that you use the Workflow Wizard to create a workflow type. When you use the wizard to create a workflow type, the following tasks are performed by the wizard. In some cases you must add more code for your workflow type. These procedures are provided so that you can see the details of the actions that the wizard performs, and the additional steps that you must perform to complete your workflow type.

1.  Create a workflow document class, and then bind the query used for the workflow to the class. For more information, see [Create a workflow document class](workflow-type-document-create.md).

2.  Bind the workflow document class to the workflow type. For more information, see [Associate a workflow document class with a workflow type](workflow-type-associate-document.md).

3.  Create workflow event handlers for started, completed, configuration change, and canceled, and then bind them to the workflow type. For more information, see [Create a workflow event handler](https://docs.microsoft.com/en-us/dynamicsax-2012/developer/how-to-create-a-workflow-event-handler).

4.  Create a class for the SubmitToWorkflowMenuItem and optionally, for the CancelMenuItem. Bind the classes to the **Action** menu items that you will create in the next step. For more information, see [Classes in X++](./dev-itpro/dev-ref/xpp-classes.md).

5.  Create an **Action** menu item for the workflow **SubmitToWorkflowMenuItem** property and optionally, for the **CancelMenuItem** property, and then bind the actions to the workflow type. For more information, see [Create a new workflow type](workflow-type-create-new.md).

### Next steps

After you create a workflow type, you can add tasks, automated tasks, and approvals. For more information, select the links below in the **See also** section.

## See also

[Configure workflow properties](configure-workflow-properties.md)

[Configure manual tasks in a workflow](configure-manual-task-workflow.md)

[Configure automated tasks in workflow](configure-automated-task-workflow.md)

[Configure approval processes in a workflow](configure-approval-process-workflow.md)
