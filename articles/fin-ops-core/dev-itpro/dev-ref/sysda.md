---
title: Access data by using the SysDa classes
description: This article explains how to create extensible queries and data access statements by using the SysDa application programming interface (API).
author: josaw1
ms.date: 08/20/2021
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.0
---

# Access data by using the SysDa classes

[!include [banner](../includes/banner.md)]

This article explains how to create extensible queries by using the SysDa application programming interface (API).

The extensible SysDa API provides almost all the data access possibilities that are available in X++. In fact, the APIs are wrappers around the code that the X++ compiler would generate. Therefore, use of the SysDa classes carries no overhead, unlike use of the **QueryRun** object, for example. Additionally, the check that the X++ compiler does on data access statements is your responsibility. For example, you create a **where** clause that compares a globally unique identifier (GUID) to an integer. The X++ compiler would diagnose this clause as an error.

The SysDa APIs include an extensive set of APIs for creating custom queries. However, there is a smaller set of types that drives the primary query activities:

+ Select: **SysDaQueryObject**, **SysDaSearchObject**, and **SysDaSearchStatement**
+ Update: **SysDaUpdateObject** and **SysDaUpdateStatement**
+ Insert: **SysDaInsertObject** and **SysDaInsertStatement**
+ Delete: **SysDaQueryObject**, **SysDaDeleteObject**, and **SysDaDeleteStatement**

The following sections provide examples of each type of query and the customizations that it supports. The examples use a table that is named TestTable. This table has two fields: a string field that is named **stringField** and an integer field that is named **intField**.

## Select query

To run a **select** query, follow these steps.

1. Create and configure a **SysDaQueryObject** object that specifies the table instance that will contain the designated records.
2. Create a **SysDaSearchObject** object, and pass the **SysDaQueryObject** object to the constructor.
3. Iterate over the results of the query by passing the **SysDaSearchObject** object to the **SysDaSearchStatement.findNext()** method.

The following example finds all rows in TestTable where **intField** \<= **5**.

```xpp
// t is the table buffer that will hold the result.
TestTable t;

// Create the query.
var qe = new SysDaQueryObject(t);

// Add clauses to the query. First the projection.
var s = qe.projection()
    .add(fieldStr(TestTable, intField))
    .add(fieldStr(TestTable, stringField));

// At this point the query is:
// intField, stringField FROM TestTable

// Add a where clause to include rows where intField is <= 5.
qe.WhereClause(new SysDaLessThanOrEqualsExpression(
    new SysDaFieldExpression(t, fieldStr(TestTable, intField)),
    new SysDaValueExpression(5)));

// Now the query is:
// intField, stringField FROM TestTable WHERE (TestTable.intField<= 5)

// Order the results by intField.
qe.OrderByClause().addDescending(fieldStr(TestTable, intField));

// Now the query is:
// intField, stringField FROM TestTable ORDER BY intField DESC WHERE (TestTable.intField<= 5)

var so = new SysDaSearchObject(qe);
var ss = new SysDaSearchStatement();

// Enumerate the designated values by using ss.
while (ss.findNext(so))
{
    info(t.stringField);
}
```

Alternatively, you can use the SysDaQueryObjectBuilder that builds a SysDaQueryObject in a fluent way.

 SysDaQueryObjectBuilder supports all four **JOIN** clauses:

 - INNER
 - OUTER
 - EXISTS
 - NOT EXISTS JOIN

 It supports all 5 aggregation functions: namely,
 - COUNT
 - SUM
 - AVG
 - MIN 
 - MAX

 It supports WHERE clauses, and multiple WHERE clauses are ANDed.

 It supports all seven comparison expressions: namely,

 - ==
 - <>
 - >
 - >=
 - <
 - <=
 - LIKE

 It supports ORDER BY clauses.

 It supports GROUP BY clauses.

 It supports all 16 hints:

 - firstOnly1
 - firstOnly10
 - firstOnly100
 - firstOnly1000
 - firstFast
 - reverse
 - forUpdate
 - noFetch
 - forceSelectOrder
 - forceNestedLoop
 - forceLiterals
 - forcePlaceholders
 - repeatableRead
 - optimisticLock
 - pessimisticLock
 - generateOnly

The following examples show two ways to build a SysDaQueryObject.

```xpp
<code>
SysDaQueryObjectBuilder::from(exampleTable)
    .firstOnly()
    .innerJoin(exampleJoinedTable)
    .where(exampleTable, fieldStr(ExampleTable, ExampleJoinedTableExampleId)).isEqualTo(exampleJoinedTable, fieldStr(ExampleJoinedTable, ExampleId))
    .where(exampleTable, fieldStr(ExampleTable, ExampleNumber)).isEqualToLiteral(0)
    .toSysDaQueryObject();
</code>
```

```xpp
<code>
var exampleTableQueryObject = new SysDaQueryObject(exampleTable);
var exampleJoinedTableQueryObject = new SysDaQueryObject(exampleJoinedTable);
exampleTableQueryObject.firstOnlyHint = SysDaFirstOnlyHint::FirstOnly1;
exampleTableQueryObject.joinClause(SysDaJoinKind::InnerJoin, exampleJoinedTableQueryObject);
exampleJoinedTableQueryObject.whereClause(new SysDaAndExpression(
    new SysDaEqualsExpression(
        new SysDaFieldExpression(exampleTable, fieldStr(ExampleTable, ExampleJoinedTableExampleId)),
        new SysDaFieldExpression(exampleJoinedTable, fieldStr(ExampleJoinedTable, ExampleId))),
    new SysDaEqualsExpression(
        new SysDaFieldExpression(exampleTable, fieldStr(ExampleTable, ExampleNumber)),
        new SysDaValueExpression(0))));
</code>
```

Use SysDaQueryExpression to enable OR and the other expressions.

The following example builds a SysDaQueryObject using **OR**.

```xpp
<code>
SysDaQueryObjectBuilder::from(exampleTable)
    .wherever(new SysDaOrExpression(
        new SysDaEqualsExpression(
            new SysDaFieldExpression(exampleTable, fieldStr(ExampleTable, ExampleNumber)),
            new SysDaValueExpression(0)),
        new SysDaEqualsExpression(
            new SysDaFieldExpression(exampleTable, fieldStr(ExampleTable, ExampleNumber)),
            new SysDaValueExpression(0))))
    .toSysDaQueryObject();
</code>
```

## Update statement

To run an **update** statement, follow these steps.

1. Create and configure a **SysDaUpdateObject** object.
2. Update data by passing the **SysDaUpdateObject** object to the **SysDaUpdateStatement.execute()** object. Because updates modify the data in the database, you must wrap the call to **execute** in **ttsbegin** and **ttscommit** statements.

The following example updates **stringField** to **"fifty"** for all rows where **intField** = **50**.

```xpp
TestTable t;

// Create an update query to find rows where intField = 50.
var uo = new SysDaUpdateObject(t);

// Set stringField to "fifty".
uo.settingClause()
    .add(fieldStr(TestTable, stringField), new SysDaValueExpression("fifty"));

// At this point the update statement is:
// UPDATE_RECORDSET TestTable SETTING stringField=fifty

uo.whereClause(new SysDaEqualsExpression(
    new SysDaFieldExpression(t, fieldStr(TestTable, intField)),
    new SysDaValueExpression(50)));

// Now the update statement is:
// UPDATE_RECORDSET TestTable SETTING stringField=fifty WHERE (TestTable.intField == 50)

// Update the rows.
ttsbegin;
    new SysDaUpdateStatement().execute(uo);
ttscommit;

// Verify the results of the update query.
TestTable t1;
select intField, stringField from t1 where t1.intField == 50;
info("Updated value is: " + t1.stringField);
// Output is: "Updated value is: fifty".
```

## Insert statement

To run an **insert** statement, follow these steps.

1. Create and configure a **SysDaInsertObject** object to specify which fields are updated during the insertion.
2. Create and configure a **SysDaQueryObject** object that specifies the source of the rows to insert. The order of the fields in **SysDaQueryObject.projection()** must match the order of the fields in **SysDaInsertObject.fields()**.
3. Assign the **SysDaQueryObject** object to the **SysDaInsertObject** object.
4. Insert the new row by passing the **SysDaInsertObject** object to the **SysDaInsertStatement.executeQuery()** method.

The following example inserts rows where **intField** = **40** and **stringField** = **"en-us"** into TestTable.

```xpp
TestTable t;

// Specify the fields in the new row.
var insertObject = new SysDaInsertObject(t);
insertObject.fields()
    .add(fieldStr(TestTable, stringField))
    .add(fieldStr(TestTable, intField));

// At this point the insert statement is:
// INSERT_RECORDSET TestTable(stringField, intField) SELECT

// Retrieve the data to insert from the LanguageTable by using a query.
LanguageTable source;
var qe = new SysDaQueryObject(source);

var s1 = qe.projection()
    .Add(fieldStr(LanguageTable, LanguageId))
    .AddValue(40);

// The query statement is:
// LanguageId, 40 FROM LanguageTable

qe.WhereClause(new SysDaEqualsExpression(
        new SysDaFieldExpression(source, fieldStr(LanguageTable, LanguageId)),
        new SysDaValueExpression("en-us")));

// Now the query is:
// LanguageId, 40 FROM LanguageTable WHERE (LanguageTable.LanguageId == en-us)

// Assign the query to the insert statement.
insertObject.query(qe); 

// The insert statement is now:
// INSERT_RECORDSET TestTable(stringField, intField) SELECT LanguageId, 40 FROM LanguageTable WHERE (LanguageTable.LanguageId == en-us)

var insertStmt = new SysDaInsertStatement();
ttsbegin;
    insertStmt.executeQuery(insertObject);
ttscommit;

// Verify the results of the insert query.
TestTable t1;
select * from t1 where t1.stringField == "en-us";
info(any2Str(t1.intField) + ":" + t1.stringField); 
// The output is "40:en-us".
```

## Delete statement

To run a **delete** statement, follow these steps.

1. Create and configure a **SysDaQueryObject** object to specify which rows to delete.
2. Create a **SysDaDeleteObject** object, and pass the **SysDaQueryObject** object to the constructor.
3. Delete the rows by passing the **SysDaDeleteObject** object to the **SysDaDeleteStatement.executeQuery()** method.

The following example deletes rows where **intField** is an even number.

```xpp
TestTable t;

// Build the query that specifies which rows to delete.
var qe = new SysDaQueryObject(t);

var s = qe.projection()
    .add(fieldStr(TestTable, intField));

// At this point the query is:
// intField FROM TestTable

// Delete rows where intField is even.
qe.WhereClause(new SysDaEqualsExpression(
    new SysDaModExpression(
    new SysDaFieldExpression(t, fieldStr(TestTable, intField)),
    new SysDaValueExpression(2)),
    new SysDaValueExpression(0)));

// Now the query is:
// intField FROM TestTable WHERE ((TestTable.intField MOD 2) == 0)

var ds = new SysDaDeleteStatement();
var delobj = new SysDaDeleteObject(qe);

// The deletion statement, from the SysDaDeleteObject, is:
// DELETE_FROM intField FROM TestTable WHERE ((TestTable.intField MOD 2) == 0)

ttsbegin;
    ds.executeQuery(delobj);
ttscommit;

info("Number of rows after deletion: " + any2Str(t.RowCount()));
```

## Clauses

SysDa queries support several clauses:

+ **whereClause** – The **where** clause is constructed from objects that inherit from **SysDaQueryExpression**. Examples are **SysDaEqualsExpression**, **SysDaNotEqualsExpression**, and **SysDaLessThanExpression**. You can find the full list by filtering in Application Explorer.
+ **orderByClause**
+ **groupByClause**
+ **joinClause** with **joinClauseKind**
+ **joinedQuery**
+ **settingClause**

## Troubleshooting

You can use the **toString()** method on **SysDaQueryObject**, **SysDaUpdateObject**, **SysDaInsertObject**, and **SysDaQueryObject** objects to view the statement that you're building.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
