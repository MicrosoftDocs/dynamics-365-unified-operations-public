---
title: 'How to: Create a Query for a Workflow Type'
TOCTitle: 'How to: Create a Query for a Workflow Type'
ms:assetid: 189592a7-813b-42f1-a3d6-cae8e7abb509
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Hh457520(v=AX.60)
ms:contentKeyID: 37009275
ms.date: 05/18/2015
mtps_version: v=AX.60
---

# How to: Create a Query for a Workflow Type 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

Before you create a workflow type, you must first create a query that will access the table fields for the workflow document. The following procedure describes how to create a query that will be used by the workflow type.

### To create a query for a workflow type

1.  In the AOT, right-click the **Queries** node, and then click **New Query**. A query group displays under the **Queries** node.

2.  Right-click the new query and then click **Rename**. Enter a name for the query.

3.  Expand the new query, right-click the **Data Sources** node, and then click **New Data Source**. A data source group displays under the **Data Sources** node.

4.  Right-click the new data source group and then click **Properties**.

5.  In the **Properties** sheet, set the **Table** property to the main table for the document type for which you are defining a workflow.

6.  In the AOT, right-click the new query and then click **Save**.

For more information about how to create queries, see [How to: Create Queries by using the AOT](how-to-create-queries-by-using-the-aot.md).
