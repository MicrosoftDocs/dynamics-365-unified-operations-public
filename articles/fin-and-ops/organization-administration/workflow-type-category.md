---
# required metadata

title: Create a workflow category
description: This topic describes how to create a workflow category.
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
# Create a workflow category 

This topic describes how to create a workflow category.

When you create a workflow type, it must be assigned to a workflow category. The workflow category determines whether a workflow type is available in a specific module. If an appropriate workflow category does not already exist, you must create one.

For example, a workflow type for a customer invoice should not be available in the **Master planning** module. To make the workflow type available only in the **Customer** module, create a workflow category with the **Customer** module selected.

The following procedure describes how to create a new workflow category.

## Create a workflow category

1.  In **Application Explorer**, expand the **Business Process and Workflow** node.

2.  Right-click the **Workflow Categories** node, and then click **New Workflow Category**. A new workflow category group displays under the **Workflow Categories** node.

3.  Right-click the new workflow category and then click **Properties**.

4.  In the **Properties** sheet, set the following properties as required.
    
| Property | Value |
|-----------|---|
| Name      | The name that is used to reference the workflow category. |
| Label     | The label used for the workflow category in the user interface. |
| Help Text | The description of the workflow category displayed in the configuration user interface. |
| Module    | The module that the workflow will be available in. The default is **Ledger**. |

After a workflow category is created, you can bind the workflow type to the new category. Typically, this is performed by the Workflow Wizard. The following procedure describes how to manually bind a workflow type to a workflow category.

## Bind a workflow type to a workflow category

1.  In **Application Explorer**, expand the **Business Process and Workflow** node, and then expand the **Workflow Types** node.

2.  Right-click the workflow type that you want to bind a workflow category to, and then select **Properties**.

3.  In the **Properties** sheet, set the **Category** property to the workflow category created in the previous procedure.

## See also

[Creating a workflow type](workflow-type-create.md)

[Create a new workflow type](workflow-type-create-new.md)
