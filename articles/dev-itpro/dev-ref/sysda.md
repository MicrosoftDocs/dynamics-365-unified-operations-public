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

The SysDA API lets you create queries that perform like X++ query statments and that are extensible like queries. The performance of a SysDA query is similar to a query statement. In contrast, a query if typically slower than a query statement. Unlike queries, SysDA queries support insertion, deletion, and updates.

The SysDa APIs include an extensive set of APIs for creating custom queries, but there are a smaller set of types that drive the primary query activities:
+ Select: **SysDaQueryObject** and **SysDaSearchStatement**
+ Update: **SysDaUpdateObject** and **SysDaUpdateStatement**
+ Insert: **SysDaInsertObject** and **SysDaInsertStatement**
+ Delete: **SysDaQueryObject** and **SysDaDeleteStatement**

The following sections provide examples of each type of query, and the customizations they support. The examples use a table named TestTable that has two fields, a string field named **stringField** and an integer field named **intField**.

## Select query

To run a select query:

+ Create and configure a **SysDaQueryObject** object. 
+ Create a **SysDaSearchObject** object, passing the **SysDaQueryObject** to the constructor. 
+ Iterate over the results of the query by passing the **SysDaSearchObject** to the **SysDaSearchStatement.next()** method.


```X++
// Finds all rows where intField <= 5.
private static void Query()
{
    // The table buffer that will hold the result.
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

    // Order the results by the intField.
    qe.OrderByClause().addDescending(fieldStr(TestTable, intField));

    // The query is now been built. Use it to fetch data.
    var sql = qe.toString();

    var so = new SysDaSearchObject(qe);
    var ss = new SysDaSearchStatement();

    while (ss.next(so))
    {
        info(t.stringField);
    }
}
```

## Update query

You build an update query by configuring an **SysDaUpdateObject** object. To update data, you pass a **SysDaUpdateObject** object to the **execute** method of a **SysDaUpdateStatement** object. The **execute** method must be wrapped in `ttsbegin` and `ttscommit` statements.

```X++
// Updates stringField to "Updated Value" for all rows where intField = 50.
private static void Update()
{
    TestTable t;

    // Create an update query to find rows where intField = 50.
    var uo = new SysDaUpdateObject(t);
    uo.whereClause(new SysDaEqualsExpression(
        new SysDaFieldExpression(t, fieldStr(TestTable, intField)),
        new SysDaValueExpression(50)));

    // Set stringField to "Updated Value".
    uo.settingClause()
       .add(fieldStr(TestTable, stringField), new SysDaValueExpression("Updated Value"));

    // Get the SQL string for the update query.
    // s IS NOT USED IN THIS EXAMPLE
    var s = uo.toString();

    // Update the rows.
    ttsbegin;
    new SysDaUpdateStatement().execute(uo);
    ttscommit;

    // Verify the results of the update query.
    TestTable t1;
    select * from t1 where t1.intField == 50;
    var updatedValue = t1.stringField;
}
```

## Insert queries

    /// <summary>
    /// Demonstrates insert statements using the VEDAS. In this test a
    /// literal value is inserted into the target, along with a field
    /// value.
    /// </summary>
    private static void Insert()
    {
        TestTable target;
        var io = new SysDaInsertObject(target);
        io.fields()
            .add(fieldStr(TestTable, stringField))
            .add(fieldStr(TestTable, intField));
        
        LanguageTable source;
        var qe = new SysDaQueryObject(source);


        var s1 = qe.projection()
            .Add(fieldStr(LanguageTable, LanguageId))
            .AddValue(40);


        qe.WhereClause(new SysDaEqualsExpression(
                        new SysDaFieldExpression(source, fieldStr(LanguageTable, LanguageId)),
                        new SysDaValueExpression("en-us")));


        // Assign the query to the insert statement.
        io.query(qe);


        var istmt = new SysDaInsertStatement();
        ttsbegin;
        istmt.executeQuery(Io);
        ttscommit;
    }



## Delete queries

    /// <summary>
    /// Shows the support for delete in the VEDAS
    /// </summary>
    private static void Delete()
    {
        TestTable target;


        var qe = new SysDaQueryObject(target);


        var s = qe.projection()
            .add(fieldStr(TestTable, intField));


        // Get rid of all the even values.
        qe.WhereClause(new SysDaEqualsExpression(
                new SysDaModExpression(
                        new SysDaFieldExpression(target, fieldStr(TestTable, intField)),
                        new SysDaValueExpression(2)),
                new SysDaValueExpression(0)));


        var ds = new SysDaDeleteStatement();
        var delobj =  new SysDaDeleteObject(qe);


        var r = delobj.toString();


        ttsbegin;
        ds.executeQuery(delobj);
        ttscommit;


    }


## More code

```
class VEDASDemo
{
    private static void GenerateData()
    {
        TestTable t;


        ttsbegin;
        delete_from t;
        for (int i = 1; i < 100; i++)
        {
            t.intField = i;
            t.stringField = "Value is " + int2Str(i);
            t.insert();
        }
        ttscommit;
    }

    /// <summary>
    /// Demo of the VEDAS
    /// </summary>
    /// <param name = "a"></param>
    public static void Main(Args a)
    {
        VEDASDemo::GenerateData();


        VEDASDemo::Query();
        VEDASDemo::Update();
        VEDASDemo::Insert();
        VEDASDemo::Delete();
    }
```

## Projection

## Execution



## Clauses

SysDa queries support several clauses:

+ `whereClause`
+ `orderByClause`
+ `groupByClause`
+ `joinClause` with `joinClauseKind`
+ `joinedQuery`
+ `settingClause`







