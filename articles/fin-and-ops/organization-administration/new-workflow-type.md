---
# required metadata

title: How to create a new workflow type
description: This topic describes how to create a workflow type in the Application Object Tree (AOT) in Dynamics 365 for Finance and Operations.
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

# How to: Create a New Workflow Type 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

This topic describes how to create a workflow type in the Application Object Tree (AOT). In Microsoft Dynamics AX, you enable the workflow process for a workflow document by creating workflow types that are used in the workflow configuration user interface.

A workflow type defines information about:

  - Which document the workflow is being used for.

  - Workflow categories used for assigning a workflow type to a specific module.

  - Tasks, automated tasks, approvals, and line item workflows that can be configured by the end-user.

  - Menu items and event handlers.

### To create a new workflow type

1.  In the AOT, expand the **Workflow** node.

2.  Right-click the **Workflow Types** node, and then click **Add-Ins** \> **Workflow type wizard**. The **Workflow wizard** is displayed. This wizard will help you create a new workflow type.

3.  Click **Next**.

4.  Set the following values for the wizard.
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><p>Value</p></th>
    <th><p>Description</p></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>Name</strong></p></td>
    <td><p>The name that will be used for the workflow type.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Category</strong></p></td>
    <td><p>Choose the workflow category to use for the workflow type. The category controls which module that the workflow type is available in. You can use an existing category or one that you created. For more information, see <a href="how-to-create-a-workflow-category.md">How to: Create a Workflow Category</a>.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Query</strong></p></td>
    <td><p>Choose the query that will access the table fields for the workflow document. For more information, see <a href="how-to-create-a-query-for-a-workflow-type.md">How to: Create a Query for a Workflow Type</a>.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Document menu item</strong></p></td>
    <td><p>Choose the menu item that points to the main form that displays the document for which you are creating a workflow type.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Document web menu item</strong></p></td>
    <td><p>Choose the web menu item that points to the Enterprise Portal page that displays the document for which you are creating a workflow type.</p></td>
    </tr>
    </tbody>
    </table>


5.  Specify which types of menu items you want to create. You can create menu items for the Microsoft Dynamics AX client, web menu items for Enterprise Portal, or items for both.

6.  Click **Next**. A list of all of the resources that will be created for the workflow type is displayed.

7.  Click **Finish** to create the resources. The wizard will create classes, menu items, web menu items, the workflow type, and a project that contains all of the items.

8.  A dialog box will be displayed that indicates the status. Click **OK**. The project that contains the workflow type resources is displayed.

After a workflow type is created, the next step is to complete the workflow document class to expose document data for conditions. For more information, see [How to: Create a Workflow Document Class](how-to-create-a-workflow-document-class.md).

## See also

[Creating a Workflow Type](creating-a-workflow-type.md)

[How to: Create a Workflow Category](how-to-create-a-workflow-category.md)

[Walkthrough: Creating a Workflow Type](walkthrough-creating-a-workflow-type.md)

