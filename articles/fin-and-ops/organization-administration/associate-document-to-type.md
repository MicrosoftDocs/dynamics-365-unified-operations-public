---
title: 'How to: Associate a Workflow Document Class with a Workflow Type'
TOCTitle: 'How to: Associate a Workflow Document Class with a Workflow Type'
ms:assetid: 677fba82-0b9e-4308-9535-f09d258ee79f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Cc556363(v=AX.60)
ms:contentKeyID: 35244736
ms.date: 05/18/2015
mtps_version: v=AX.60
---

# How to: Associate a Workflow Document Class with a Workflow Type 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

To create a workflow in Microsoft Dynamics AX, you must bind a workflow document class to the workflow type. The workflow document class contains references to the table data fields used by the workflow. This procedure describes how to bind the workflow document class to a workflow type.


> [!NOTE]
> <P>If you used the Workflow Wizard to create the workflow type, the workflow document class will have already been bound to the workflow type by the wizard.</P>



Before you begin this procedure, you must create a workflow document class to expose table fields used for conditions in the configuration user interface. For more information, see [How to: Create a Workflow Document Class](how-to-create-a-workflow-document-class.md).

### To bind a workflow document class to a workflow type

1.  In the AOT, expand the **Workflow** node.

2.  In the **Workflow Types** node, right-click the workflow type that you want to bind a workflow document class to, and then click **Properties**.

3.  In the **Properties** sheet, set the **Document** property to the workflow document class that defines the workflow document.

## See also

[How to: Create a New Workflow Type](how-to-create-a-new-workflow-type.md)

[Walkthrough: Creating a Workflow Type](walkthrough-creating-a-workflow-type.md)

[How to: Create a Workflow Document Class](how-to-create-a-workflow-document-class.md)
