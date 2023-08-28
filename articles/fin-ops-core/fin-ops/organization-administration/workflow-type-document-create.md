---
title: Create a workflow document class
description: This article describes how to create a workflow document class.
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
ms.assetid: 
---

# Create a workflow document class

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

You define table fields in a query to create workflow conditions. In a typical scenario, calculated fields are used to determine the behavior of a workflow. For example, a dynamic sales total of all records in a table can be used as a workflow condition to determine whether the step should be used. However, a limitation of queries is that you can't define calculated fields in the queries themselves. To overcome this query limitation, you must use a workflow document class. This article describes how to create a workflow document class.

The workflow document class that you create defines table fields for conditions in two ways: the Application Explorer query and parameter methods. You must override the **getQueryName** method of the [WorkflowDocument class](/previous-versions/dynamics/ax-2012/application-classes/gg798542(v=ax.60)) to return the name of the query. You can optionally add calculated fields by adding parameter methods that have a specific signature on the class. For more information about workflow conditions, see [Configure workflow properties](configure-workflow-properties.md) and [Configure conditional decisions in a workflow](configure-conditional-decision-workflow.md).

The following procedures explain how to create a workflow document class that includes a parameter method for a calculated field. Before you begin, you must create a query that specifies the data that will be accessed. For more information about workflow queries, see [Create a query for a workflow type](workflow-type-query.md).

> [!NOTE]
> If you used the **Workflow** wizard to create the workflow type, the wizard has already created the workflow document class.

## Create a workflow document class

1. Follow one of these steps to create a new query:

    + In Application Explorer, expand the **Classes** node. Right-click the **Classes** node, and then select **New Class**. A class group appears under the **Classes** node. Right-click the new class, select **Rename**, and then enter a name for the workflow document class.
    + On the **Project** menu, select **Add new item**. In the **Add new item** dialog box, select **Class**. Enter a name for the class, and then select **Create**.

2. Expand the new class, select **classDeclaration**, right-click the class declaration, and then select **Edit**.
3. Enter the following code in the class declaration.

    ```X++
    class <MyWorkflowDocumentClassName> extends WorkflowDocument
    {
    }
    ```

4. Close the **Editor** window, and select **Yes** to save your changes.
5. Right-click the new class, point to **Override Method**, and then select **getQueryName**. A method node that is named **getQueryName** appears under the workflow document class node, and the **Editor** window appears.

    > [!NOTE]
    > Be sure to select **getQueryName** as the method to override. The [WorkflowDocument.getQuery method](/previous-versions/dynamics/ax-2012/application-classes/gg798533(v=ax.60)) is used only internally to retrieve the actual query, based on the string that is returned by the [WorkflowDocument.getQueryName method](/previous-versions/dynamics/ax-2012/application-classes/gg798541(v=ax.60)).

6. In the **Editor** window, enter the following code for the query method.

    ```X++
    QueryName getQueryName()
    {
        return querystr(<MyWorkflowDocumentQueryName>);
    }
    ```

After you create the workflow document class, you can bind it to the workflow type. For more information, see [Associate a workflow document class with a workflow type](workflow-type-associate-document.md).

You can add a calculated field to the workflow document class only if it meets these conditions:

- It must be named **parm \<name\>**.
- It must define the **CompanyId**, **TableId**, and **RecId** parameters.
- It must return an extended data type (EDT) that will be included in the list of fields that define conditions or notification messages. The label for the EDT must uniquely identify the value.

## Add a calculated field to the workflow document class

1. In the workflow document class that you want to add a calculated field to, right-click the class, and then select **New Method**. A new method node appears under the **Classes** node.
2. Right-click the new method node, and then select **Edit**.
3. Enter code in the format that is shown in the following example. This example shows how to add a calculated field to determine the total credit amount for a journal.

    ```X++
    public TotalJournalCreditAmount parmTotalJournalCreditAmount(CompanyId _companyId, TableId _tableId, RecId _recId)
    {
        // The calculateAmounts method contains business and validation logic
        this.calculateAmounts(_companyId, _tableId, _recId);
        return totalJournalCreditAmount;
    }
    ```

## See also

[Associate a workflow document class with a workflow type](workflow-type-associate-document.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
