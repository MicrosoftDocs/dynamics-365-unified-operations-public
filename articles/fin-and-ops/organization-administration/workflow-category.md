---
# required metadata

title: 
description: 
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
ms.author: RobinARH
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---
# How to: Create a Workflow Category 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

When you create a workflow type in Microsoft Dynamics AX, it must be assigned to a workflow category. The workflow category determines whether a workflow type is available in a specific module. If an appropriate workflow category does not already exist, you must create one.

For example, a workflow type for a customer invoice should not be available in the **Master planning** module. To make the workflow type available only in the **Customer** module, create a workflow category with the **Customer** module selected.

The following procedure describes how to create a new workflow category.

### To create a workflow category

1.  In the **AOT**, expand the **Workflow** node.

2.  Right-click the **Workflow Categories** node, and then click **New Workflow Category**. A new workflow category group displays under the **Workflow Categories** node.

3.  Right-click the new workflow category and then click **Properties**.

4.  In the **Properties** sheet, set the following properties as required.
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><p>Property</p></th>
    <th><p>Value</p></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>Name</strong></p></td>
    <td><p>The name that is used to reference the workflow category.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Label</strong></p></td>
    <td><p>The label used for the workflow category in the user interface.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Help Text</strong></p></td>
    <td><p>The description of the workflow category displayed in the configuration user interface.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Module</strong></p></td>
    <td><p>The module that the workflow will be available in. The default is <strong>Ledger</strong>.</p></td>
    </tr>
    </tbody>
    </table>


After a workflow category is created, you can bind the workflow type to the new category. Typically, this is performed by the Workflow Wizard. The following procedure describes how to manually bind a workflow type to a workflow category.

### To bind a workflow type to a workflow category

1.  In the **AOT**, expand the **Workflow** node, and then expand the **Workflow Types** node.

2.  Right-click the workflow type that you want to bind a workflow category to, and then select **Properties**.

3.  In the **Properties** sheet, set the **Category** property to the workflow category created in the previous procedure.

## See also

[Creating a Workflow Type](creating-a-workflow-type.md)

[How to: Create a New Workflow Type](how-to-create-a-new-workflow-type.md)

[Walkthrough: Creating a Workflow Type](walkthrough-creating-a-workflow-type.md)
