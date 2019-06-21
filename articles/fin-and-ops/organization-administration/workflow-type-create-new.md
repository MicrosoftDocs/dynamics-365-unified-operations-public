---
# required metadata

title: Create a new workflow type
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
ms.reviewer: rhaertle
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

# Create a new workflow type 

This topic describes how to create a workflow type in the Application Explorer. You enable the workflow process for a workflow document by creating workflow types that are used in the workflow configuration user interface.

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
    
    Value | Description
    |---|---|
    | Name | The name that will be used for the workflow type. |
    | Category | Choose the workflow category to use for the workflow type. The category controls which module that the workflow type is available in. You can use an existing category or one that you created. For more information, see [Create a workflow category](workflow-type-category.md). |
    | Query | Choose the query that will access the table fields for the workflow document. For more information, see [Create a query for a workflow type](workflow-type-query.md). |
    | Document menu item | Choose the menu item that points to the main form that displays the document for which you are creating a workflow type. |
    | Document web menu item | Choose the web menu item that points to the Enterprise Portal page that displays the document for which you are creating a workflow type. |

5.  Specify which types of menu items you want to create. You can create menu items for the Finance and Operations client, web menu items for Enterprise Portal, or items for both.
6.  Click **Next**. A list of all of the resources that will be created for the workflow type is displayed.
7.  Click **Finish** to create the resources. The wizard will create classes, menu items, web menu items, the workflow type, and a project that contains all of the items.
8.  A dialog box will be displayed that indicates the status. Click **OK**. The project that contains the workflow type resources is displayed.

After you create a workflow type, the next step is to complete the workflow document class to expose document data for conditions. For more information, see [Create a workflow document class](workflow-type-document-create.md).

## See also

[Creating a workflow type](workflow-type-create.md)

[Create a workflow category](workflow-type-category.md)

