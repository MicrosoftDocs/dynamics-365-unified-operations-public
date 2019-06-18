---
title: Workflow Type Checklist
TOCTitle: Workflow Type Checklist
ms:assetid: c3a64584-4e32-442f-a2d4-9de213382c18
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Cc637397(v=AX.60)
ms:contentKeyID: 35251093
ms.date: 05/18/2015
mtps_version: v=AX.60
---

# Workflow Type Checklist 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

The following checklist describes the steps to follow to create a new workflow type for Microsoft Dynamics AX. Workflow types are used to create configurations for a workflow in a Microsoft Dynamics AX application. For more information about workflow configuration, see [Design and configure workflows for Microsoft Dynamics AX](https://msdn.microsoft.com/en-us/library/gg751350\(v=ax.60\)).

## Workflow Type Checklist

1.  If an existing category is not appropriate, create a new workflow category to use for the workflow type. For more information, see [How to: Create a Workflow Category](how-to-create-a-workflow-category.md).

2.  Create a query that accesses the document for which the new workflow type is being created. For more information, see [How to: Create a Query for a Workflow Type](how-to-create-a-query-for-a-workflow-type.md).

3.  Create a workflow type in the Application Object Tree (AOT). Typically, you do this using the Workflow Wizard. For more information, see [How to: Create a New Workflow Type](how-to-create-a-new-workflow-type.md).

We recommend that you use the Workflow Wizard to create a workflow type. When you use the wizard to create a workflow type, the following tasks are performed by the wizard. In some cases you must add more code for your workflow type. These procedures are provided so that you can see the details of the actions that the wizard performs, and the additional steps that you must perform to complete your workflow type.

1.  Create a workflow document class, and then bind the query used for the workflow to the class. For more information, see [How to: Create a Workflow Document Class](how-to-create-a-workflow-document-class.md).

2.  Bind the workflow document class to the workflow type. For more information, see [How to: Associate a Workflow Document Class with a Workflow Type](how-to-associate-a-workflow-document-class-with-a-workflow-type.md).

3.  Create workflow event handlers for started, completed, configuration change, and canceled, and then bind them to the workflow type. For more information, see [How to: Create a Workflow Event Handler](how-to-create-a-workflow-event-handler.md).

4.  Create a class for the SubmitToWorkflowMenuItem and optionally, for the CancelMenuItem. Bind the classes to the **Action** menu items that you will create in the next step. For more information, see [Classes in X++](classes-in-x.md).

5.  Create an **Action** menu item for the workflow **SubmitToWorkflowMenuItem** property and optionally, for the **CancelMenuItem** property, and then bind the actions to the workflow type. For more information, see [How to: Create a New Workflow Type](how-to-create-a-new-workflow-type.md).

### ![Cc637397.collapse\_all(en-us,AX.60).gif](images/Gg863931.collapse_all(en-us,AX.60).gif "Cc637397.collapse_all(en-us,AX.60).gif")Next Steps

After you create a workflow type, you can add tasks, automated tasks, and approvals. For more information, see [Creating Workflow Tasks, Automated Tasks, and Approvals](creating-workflow-tasks-automated-tasks-and-approvals.md).

## See also

[Walkthrough: Creating a Workflow Type](walkthrough-creating-a-workflow-type.md)

[Implementing Workflow for Microsoft Dynamics AX](implementing-workflow-for-microsoft-dynamics-ax.md)

[Creating Workflow Tasks, Automated Tasks, and Approvals](creating-workflow-tasks-automated-tasks-and-approvals.md)
