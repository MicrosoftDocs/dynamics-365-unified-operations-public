---
# required metadata

title: Create a workflow document class
description: This topic describes how to create a workflow document class.
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
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Create a workflow document class 

This topic describes how to create a workflow document class.

Table fields are defined in a query to create workflow conditions. A limitation of queries is that you cannot define calculated fields in the query itself. A common scenario is to use calculated fields to determine the behavior of a workflow. For example, a dynamic sales total of all records in a table can be used as a workflow condition to determine whether the step should be used. To overcome this query limitation, you must use a workflow document class.

The workflow document class that you create defines table fields for conditions in two ways: the Application Explorer query and parameter methods. You must override the **getQueryName** method of the [WorkflowDocument Class](https://docs.microsoft.com/en-us/previous-versions/dynamics/ax-2012/application-classes/gg798542(v=ax.60)) to return the name of the query. You can optionally add calculated fields by adding parameter methods with a specific signature on the class. For more information about workflow conditions, see [Configure workflow properties](configure-workflow-properties.md) and [Configure conditional decisions in a workflow](configure-conditional-decision-workflow.md).

Before you begin these procedures, you must create a query that specifies the data that will be accessed. For more information about workflow queries, see [Create a query for a workflow type](workflow-type-query.md).

The following procedures show how to create a workflow document class including a parameter method for a calculated field.

> [!NOTE]
> <P>If you used the Workflow Wizard to create the workflow type, the workflow document class will have already been created by the wizard.</P>

## Create a workflow document class

1.  Create a new query by using one of these methods:
    + In the Application Explorer, expand the **Classes** node. Right-click the **Classes** node, and then select **New Class**. A class group displays under the **Classes** node. Right-click the new class, click **Rename**, and then enter a name for the workflow document class.
    + In the **Project** menu, select **Add new item**. In the **Add new item** dialog, select **Class**. Give the class a name and then click **Create**.

1.  Expand the new class, select **classDeclaration**, right-click the class declaration, and then click **Edit**.
1.  Enter the following code in the class declaration.

       ```X++
       class <MyWorkflowDocumentClassName> extends WorkflowDocument
       {
       }
       ```

1.  Close the **Editor** window and click **Yes** to save changes.
1.  Right-click the new class, point to **Override Method**, and then click getQueryName. A method node named **getQueryName** displays under the workflow document class node and the **Editor** window opens.

    > [!NOTE]
    > <P>Be sure to select getQueryName as the method to override. The <A href="https://docs.microsoft.com/en-us/previous-versions/dynamics/ax-2012/application-classes/gg798533(v=ax.60)">WorkflowDocument.getQuery Method</A> is used only internally to retrieve the actual query based on the string returned by the <A href="https://docs.microsoft.com/en-us/previous-versions/dynamics/ax-2012/application-classes/gg798541(v=ax.60)">WorkflowDocument.getQueryName Method</A>.</P>

8.  In the **Editor** window, enter the following code for the query method.

       ```X++
       QueryName getQueryName()
        {
            return querystr(<MyWorkflowDocumentQueryName>);
        }
       ```

After you create the workflow document class, you can bind it to the workflow type. For more information, see [Associate a workflow document class with a workflow type](workflow-type-associate-document.md).

To add a calculated field to the workflow document class, it must:

  - Be named parm \<name\>.
  - Define the parameters CompanyId, TableId, and RecId.
  - Return an extended data type that will be included in the list of fields for defining conditions or notification messages. The label for the EDT must uniquely identify the value.

## Add a calculated field to the workflow document class

1.  In the workflow document class that you want to add a calculated field to, right-click the class, and then click **New Method**. A new method node displays under the **Classes** node.
2.  Right-click the new method node, and then click **Edit**. Enter code that uses the format shown in the following code example.

The following code example shows how to add a calculated field to determine the total credit amount for a journal.

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
