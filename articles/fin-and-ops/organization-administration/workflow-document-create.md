---
title: 'How to: Create a Workflow Document Class'
TOCTitle: 'How to: Create a Workflow Document Class'
ms:assetid: 6ca32cdb-772f-412a-bd73-19be04882e29
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Cc592495(v=AX.60)
ms:contentKeyID: 35244798
ms.date: 05/18/2015
mtps_version: v=AX.60
---

# How to: Create a Workflow Document Class 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

Microsoft Dynamics AX table fields are defined in a query to create workflow conditions. A limitation of a Microsoft Dynamics AX query is that you cannot define calculated fields in the query itself. It is a common scenario to use calculated fields to determine the behavior of a workflow. For example, a dynamic sales total of all records in a table can be used as a workflow condition to determine whether the step should be used. To overcome this query limitation, you must use a workflow document class.

The workflow document class that you create defines table fields for conditions in two ways: the Application Object Tree (AOT) query and parameter methods. The getQueryName method of the [WorkflowDocument Class](https://msdn.microsoft.com/en-us/library/gg798542\(v=ax.60\)) must be overridden to return the name of the query. You can optionally add calculated fields by adding parameter methods with a specific signature on the class. For more information about workflow conditions, see [Design and configure workflows for Microsoft Dynamics AX](https://msdn.microsoft.com/en-us/library/gg751350\(v=ax.60\)).

Before you begin these procedures, you must create a query that specifies the data that will be accessed. For more information about workflow queries, see [How to: Create a Query for a Workflow Type](https://docs.microsoft.com/en-us/dynamicsax-2012/developer/how-to-create-a-query-for-a-workflow-type).

The following procedures show how to create a workflow document class including a parameter method for a calculated field.


> [!NOTE]
> <P>If you used the Workflow Wizard to create the workflow type, the workflow document class will have already been created by the wizard.</P>



### To create a workflow document class

1.  In the AOT, expand the **Classes** node.

2.  Right-click the **Classes** node, and then select **New Class**. A class group displays under the **Classes** node.

3.  Right-click the new class, click **Rename**, and then enter a name for the workflow document class.

4.  Expand the new class, select **classDeclaration**, right-click the class declaration, and then click **Edit**.

5.  Enter the following code in the class declaration.
    
       ```X++
       class <MyWorkflowDocumentClassName> extends WorkflowDocument
        {
        }
       ```

6.  Close the **Editor** window and click **Yes** to save changes.

7.  Right-click the new class, point to **Override Method**, and then click getQueryName. A method node named **getQueryName** displays under the workflow document class node and the **Editor** window opens.
    

    > [!NOTE]
    > <P>Be sure to select getQueryName as the method to override. The <A href="https://msdn.microsoft.com/en-us/library/gg798533(v=ax.60)">WorkflowDocument.getQuery Method</A> is used only internally to retrieve the actual query based on the string returned by the <A href="https://msdn.microsoft.com/en-us/library/gg798541(v=ax.60)">WorkflowDocument.getQueryName Method</A>.</P>



8.  In the **Editor** window, enter the following code for the query method.
    
       ```X++
       QueryName getQueryName()
        {
            return querystr(<MyWorkflowDocumentQueryName>);
        }
       ```

After you create the workflow document class, you can bind it to the workflow type. For more information, see [How to: Associate a Workflow Document Class with a Workflow Type].

To add a calculated field to the workflow document class, it must:

  - Be named parm \<name\>.

  - Define the parameters CompanyId, TableId, and RecId.

  - Return an extended data type that will be included in the list of fields for defining conditions or notification messages. The label for the EDT must uniquely identify the value.

### To add a calculated field to the workflow document class

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

[How to: Associate a Workflow Document Class with a Workflow Type]

[How to: Associate a Workflow Document Class with a Workflow Type]: https://docs.microsoft.com/en-us/dynamicsax-2012/developer/how-to-associate-a-workflow-document-class-with-a-workflow-type

  
**Announcements:** New book: "Inside Microsoft Dynamics AX 2012 R3" now available. Get your copy at the [MS Press Store](https://www.microsoftpressstore.com/store/inside-microsoft-dynamics-ax-2012-r3-9780735685109).
