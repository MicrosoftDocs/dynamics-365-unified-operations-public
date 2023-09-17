---
title: Create a new workflow type
description: This article describes how to create a workflow type in Application Explorer.
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

# Create a new workflow type

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

To make the workflow process available for a workflow document, you must create the workflow types that are used in the workflow configuration user interface (UI). This article describes how to create a workflow type in Application Explorer.

A workflow type defines the following information:

- The document that the workflow is used for
- Workflow categories, which are used to assign a workflow type to a specific module
- Tasks, automated tasks, approvals, and line item workflows that the user can configure
- Menu items and event handlers

## Create a new workflow type

1. Follow one of these steps to open the **Workflow** wizard. The wizard will help you create a new workflow type.

    + In Application Explorer, right-click the **Business Process and Workflow** node, and then select **Add-Ins** \> **Workflow type wizard**.
    + On the **Project** menu, select **Add new item**. In the **Add new item** dialog box, select **Workflow type**. Enter a name for the query, and then select **Create**.

2. Set the following values for the wizard.

    | Value | Description |
    |---|---|
    | Name | Specify the name that will be used for the workflow type. |
    | Category | Select the workflow category that will be used for the workflow type. The category determines the module that the workflow type is available in. You can use an existing category or a new category that you create. For more information, see [Create a workflow category](workflow-type-category.md). |
    | Query | Select the query that will access the table fields for the workflow document. For more information, see [Create a query for a workflow type](workflow-type-query.md). |
    | Document menu item | Select the menu item that points to the main page that shows the document that you're creating the workflow type for. |
    | Document web menu item | Select the web menu item that points to the Enterprise Portal page that shows the document that you're creating the workflow type for. |

3. Specify the types of menu items that you want to create. You can create menu items, web menu items, or both.
4. Select **Next**. A list of all the resources that will be created for the workflow type is shown.
5. Select **Finish** to create the resources. The wizard creates classes, menu items, web menu items, the workflow type, and a project that contains all the items.
6. When dialog box appears that indicates the status, select **OK**. The project that contains the workflow type resources is shown.

After you create a workflow type, the next step is to create a workflow document class to expose document data for conditions. For more information, see [Create a workflow document class](workflow-type-document-create.md).

## See also

[Create a workflow type](workflow-type-create.md)

[Create a workflow category](workflow-type-category.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
