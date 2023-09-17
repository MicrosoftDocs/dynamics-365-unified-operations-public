---
title: Create a workflow category
description: This article describes how to create a workflow category.
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
# Create a workflow category

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

When you create a workflow type, you must assign it to a workflow category. The workflow category determines whether the workflow type is available in a specific module. If an appropriate workflow category doesn't already exist, you must create it.

For example, a workflow type for a customer invoice should not be available in the **Master planning** module. To make the workflow type available only in the **Customer** module, select the **Customer** module when you create a workflow category.

This article describes how to create a workflow category.

## Create a workflow category

1. In Application Explorer, expand the **Business Process and Workflow** node.
2. Follow one of these steps to create the workflow category:

    + Right-click the **Workflow Categories** node, and then select **New Workflow Category**. A new workflow category group appears under the **Workflow Categories** node. Right-click the new workflow category, and then select **Properties**.
    + On the **Project** menu, select **Add new item**. In the **Add new item** dialog box, select **Workflow category**. Enter a name for the category, and then select **Create**.

3. On the **Properties** sheet, set the following properties, as required.

    | Property | Value |
    |---|---|
    | Name | Specify the name that is used to reference the workflow category. |
    | Label | Specify the label that is used for the workflow category in the user interface (UI). |
    | Help Text | Specify the description that is shown for the workflow category in the workflow configuration UI. |
    | Module | Specify the module that the workflow will be available in. The default module is **Ledger**. |

After you create a workflow category, a workflow type can be bound to it. Typically, the **Workflow** wizard completes this step. However, the following procedure explains how to manually bind a workflow type to a workflow category.

## Bind a workflow type to a workflow category

1. In Application Explorer, expand the **Business Process and Workflow** node, and then expand the **Workflow Types** node.
2. Right-click the workflow type that you want to bind to a workflow category, and then select **Properties**.
3. On the **Properties** sheet, set the **Category** property to the workflow category that you created in the previous procedure.

## See also

[Create a workflow type](workflow-type-create.md)

[Create a new workflow type](workflow-type-create-new.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
