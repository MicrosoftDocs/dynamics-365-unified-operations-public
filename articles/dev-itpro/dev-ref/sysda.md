---
# required metadata

title: Query using the SysDA API
description: This topic explains how to create extensible queries by using the SysDA API. 
author: RobinARH
manager: AnnBe
ms.date: 06/24/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 72211
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.0
---

# Query using the SysDA API

[!include [banner](../includes/banner.md)]

This topic explains how to create extensible queries by using the SysDA API. 

The SysDA API lets you create queries that perform like X++ query statments and that are extensible like queries. The performance of a SysDA query is similar to a query statement. In contrast, a query is typically slower than a query statement. Unlike queries, SysDA queries support insertion, deletion, and updates.

The SysDa APIs include an extensive set of APIs for creating custom queries, but there are a smaller set of types that drive the primary query activities:
+ Select: **SysDaQueryObject**, **SysDaSearchObject**, and **SysDaSearchStatement**
+ Update: **SysDaUpdateObject** and **SysDaUpdateStatement**
+ Insert: **SysDaInsertObject** and **SysDaInsertStatement**
+ Delete: **SysDaQueryObject**, **SysDaDeleteObject** and **SysDaDeleteStatement**

The following sections provide examples of each type of query, and the customizations they support. The examples use a table named TestTable that has two fields, a string field named **stringField** and an integer field named **intField**.

## Select query

To run a select query:

+ Create and configure a **SysDaQueryObject** object. 
+ Create a **SysDaSearchObject** object, passing the **SysDaQueryObject** to the constructor. 
+ Iterate over the results of the query by passing the **SysDaSearchObject** to the **SysDaSearchStatement.next()** method.


```X++
// Find all rows where intField <= 5.

// t is the table buffer that will hold the result.
TestTable t; 

// Create the query.
var qe = new SysDaQueryObject(t);
// Add clauses to the query. First the projection.
var s = qe.projection()
    .add(fieldStr(TestTable, intField))
    .add(fieldStr(TestTable, stringField));

// Add a where clause to include rows where intField is <= 5.
qe.WhereClause(new SysDaLessThanOrEqualsExpression(
    new SysDaFieldExpression(t, fieldStr(TestTable, intField)),
    new SysDaValueExpression(5)));

// Order the results by intField.
qe.OrderByClause().addDescending(fieldStr(TestTable, intField));

var so = new SysDaSearchObject(qe);
var ss = new SysDaSearchStatement();

while (ss.next(so))
{
    info(t.stringField);
}
```

## Update query

To run an update query:

+ Create an configure a **SysDaUpdateObject** object. 
+ Update data by by passing the **SysDaUpdateObject** object to the **SysDaUpdateStatement.execute()** object. You must wrap the call to  **execute** in `ttsbegin` and `ttscommit` statements.

```X++
// Update stringField to "Updated Value" for all rows where intField = 50.

TestTable t;

// Create an update query to find rows where intField = 50.
var uo = new SysDaUpdateObject(t);
uo.whereClause(new SysDaEqualsExpression(
    new SysDaFieldExpression(t, fieldStr(TestTable, intField)),
    new SysDaValueExpression(50)));

// Set stringField to "Updated Value".
uo.settingClause()
   .add(fieldStr(TestTable, stringField), new SysDaValueExpression("Updated Value"));

// Update the rows.
ttsbegin;
    new SysDaUpdateStatement().execute(uo);
ttscommit;

// Verify the results of the update query.
TestTable t1;
select * from t1 where t1.intField == 50;
var updatedValue = t1.stringField;
info("Updated value is: " + t1.stringField);
```

## Insert query

To run an insert query:

+ Create and configure a **SysDaInsertObject** object to specify which fields are updated during the insertion.
+ Create and configure a **SysDaQueryObject** object that specifies the source of the rows to insert. The order of the fields in  **SysDaQueryObject.projection()** must match the order of the fields in the **SysDaInsertObject.fields()**.
+ Assign the **SysDaQueryObject** object to the **SysDaInsertObject** object.
+ Insert the new row by passing the **SysDaInsertObject** object to the **SysDaInsertStatement.executeQuery()** method.

```X++
// Insert rows with intField = 40 and stringField = "en-us".
TestTable t;

// Specify the fields in the new row.
var insertObject = new SysDaInsertObject(t);
insertObject.fields()
    .add(fieldStr(TestTable, stringField))
    .add(fieldStr(TestTable, intField));

// Retrieve the data to insert from the LanguageTable.
LanguageTable source;
var qe = new SysDaQueryObject(source);

var s1 = qe.projection()
    .Add(fieldStr(LanguageTable, LanguageId))
    .AddValue(40);

qe.WhereClause(new SysDaEqualsExpression(
                new SysDaFieldExpression(source, fieldStr(LanguageTable, LanguageId)),
                new SysDaValueExpression("en-us")));

// Assign the query to the insert statement.
insertObject.query(qe);

var insertStmt = new SysDaInsertStatement();
ttsbegin;
    insertStmt.executeQuery(insertObject);
ttscommit;

// Verify the results of the insert query.
TestTable t1;
select * from t1 where t1.stringField == "en-us";
info(any2Str(t1.intField) + ":" + t1.stringField); 
```

## Delete query

To run an delete query:

+ Create and configure a **SysDaQueryObject** object to specify which rows to delete.
+ Create a **SysDaDeleteObject** object, passing the **SysDaQueryObject** to the constructor.
+ Delete the rows by passing the **SysDaDeleteObject** object to the **SysDaDeleteStatement.executeQuery()** method.

```X++
// Delete rows where intField is even.
TestTable t;

var qe = new SysDaQueryObject(t);

var s = qe.projection()
    .add(fieldStr(TestTable, intField));

// Delete rows where intField is even.
qe.WhereClause(new SysDaEqualsExpression(
    new SysDaModExpression(
        new SysDaFieldExpression(t, fieldStr(TestTable, intField)),
        new SysDaValueExpression(2)),
        new SysDaValueExpression(0)));

var ds = new SysDaDeleteStatement();
var delobj =  new SysDaDeleteObject(qe);

ttsbegin;
    ds.executeQuery(delobj);
ttscommit;

info("Number of rows after deletion: " + any2Str(t.RowCount()));
```

## Clauses

SysDa queries support several clauses:

+ `whereClause`: The where clause is constructed from objects that inherit from **SysDaQueryExpression**. Examples are **SysDaEqualsExpression**, **SysDaNotEqualsExpression**, and **SysDaLessThanExpression**. You can find the full list by filtering in the Application Explorer.
+ `orderByClause`: .add and .addDescending 
+ `groupByClause`:
+ `joinClause` with `joinClauseKind`
+ `joinedQuery`
+ `settingClause`
