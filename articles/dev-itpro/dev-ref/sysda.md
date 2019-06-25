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
The SysDA API lets you create queries that perform like X++ query statments and are extensible like queries. X++ query statements are not extensible. If you want to add a new range, join, or field to your query, then you need to convert your statement to a query. Queries do have their own limitations:

+ Queries are slower than query statements. Even when the resulting TSQL is the same, queries need more compute to prepare the TSQL. The execution time in SQL server is of course the same (which often overshadows the overhead).
This is the reason we avoid converting select statements to queries in performance critical paths.
+ Queries have a limited set of capabilities. For example, `delete_from` is not supported. `update_recordset` and `insert_recordset` are partly supported by using some arcane static methods on **SysQuery**.

The SysDa APIs includes an extensive set of APIs for creating custom queries, but there are a smaller set of types that drive the primary query activities:
+ Select: **SysDaQueryObject** and **SysDaSearchStatement**
+ Update: **SysDaUpdateObject** and **SysDaUpdateStatement**
+ Insert: **SysDaInsertObject** and **SysDaInsertStatement**
+ Delete: **SysDaQueryObject** and **SysDaDeleteStatement**

## Select queries

Select queries are built using **SysDaQueryObject**. To fetch the data, you generate a SQL string from **SysDaQueryObject** and pass it to an **SysDaSearchObject**. You use **SysDaSearchStatement** to interate over the results in the **SysDaSearchObject**.


    /// <summary>
    /// Shows how to query using the VEDAS. The example is very simple, and
    /// does not contain joins, cross company and other features.
    /// </summary>
    private static void Query()
    {
        TestTable t; // This is the table buffer that will hold the result.


        // Create the query:
        var qe = new SysDaQueryObject(t);


        // Now add clauses to the query. First the projection:
        var s = qe.projection()
            .add(fieldStr(TestTable, intField))
            .add(fieldStr(TestTable, stringField));
        
        // add a where clause to include the first 5 records
        qe.WhereClause(new SysDaLessThanOrEqualsExpression(
            new SysDaFieldExpression(t, fieldStr(TestTable, intField)),
            new SysDaValueExpression(5)));


        // order the results by the integer field:
        qe.OrderByClause().addDescending(fieldStr(TestTable, intField));


        // Not the object model has been built. Not use it to fetch data.
        var sql = qe.toString();


        var so = new SysDaSearchObject(qe);
        var ss = new SysDaSearchStatement();


        while (ss.next(so))
        {
            info(t.stringField);
        }
    }


## Update queries

Update queries are built using **SysDaUpdateObject**. To update the data, you pass the **SysDaUpdateObject** object to the **execute** method of the **SysDaUpdateStatement**. The **execute** method must be wrapped in `ttsbegin` and `ttscommit` statements.

```X++
private static void Update()
    {
        TestTable t;


        var uo = new SysDaUpdateObject(t);
        uo.whereClause(new SysDaEqualsExpression(
            new SysDaFieldExpression(t, fieldStr(TestTable, intField)),
            new SysDaValueExpression(50)));


        uo.settingClause()
           .add(fieldStr(TestTable, stringField), new SysDaValueExpression("Updated Value"));
        
        var s = uo.toString();


        ttsbegin;
        new SysDaUpdateStatement().execute(uo);
        ttscommit;


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

## Projection

## Execution



## Clauses

SysDa queries support several clauses:

+ `whereClause`
+ `orderByClause`
+ `groupByClause`
+ `joinClause` with `joinClauseKind`
+ `joinedQuery`







